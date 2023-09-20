# Hướng dẫn tạo Kubernetes Cluster bằng Kubeadm trên Ubuntu 20.04
---
Kubernetes là một hệ thống điều phối các containers (vùng chứa) và quản lý chúng ở một quy mô lớn. Để hiểu rõ hơn về hệ thống này, hãy cùng Vietnix tìm hiểu về cách thiết lập và tạo Kubernetes Cluster bằng Kubeadm trên Ubuntu 20.04. Cùng tìm hiểu qua bài chia sẻ dưới đây.

## Giới thiệu về Kubernetes Cluster

**Lưu ý:** Hướng dẫn này sử dụng phiên bản 1.22 của [[03-Kubernestes | Kubernestes]], phiên bản được hỗ trợ chính thức tại thời điểm thực hiện bài viết này. Bạn có thể xem thông tin của phiên bản này hoặc những phiên bản mới nhất trong trang document chính thức của Kubernetes.

**Kubernetes** là một hệ thống điều phối các [[01-Container | Container]] (vùng chứa) và quản lý chúng theo quy mô. Hệ thống này được phát triển ban đầu bởi **Google** dựa trên kinh nghiệm vận hành các containers trong quá trình phát triển sản phẩm. Tới thời điểm hiện tại, Kubernetes có mã nguồn mở và được phát triển rất tích cực bởi cộng đồng công nghệ trên toàn thế giới.

**Kubeadm** tự động cài đặt và cấu hình các thành phần Kubernetes như là máy chủ [API](https://vietnix.vn/api-la-gi/), Controller Manager và Kube DNS. Tuy nhiên, Kubeadm không tạo users hoặc xử lý việc cài đặt và cấu hình các dependencies ở cấp độ hệ điều hành.

Đối với các tác vụ sơ bộ này, bạn có thể sử dụng công cụ quản lý cấu hình như **Ansible** hoặc **SaltStack**. Việc sử dụng các công cụ trên giúp tạo mới các Cluster (cụm) bổ sung hoặc tạo lại các Cluster hiện có nhưng đơn giản và ít xảy ra lỗi hơn.

Trong hướng dẫn cách thiết lập một Cluster Kubernetes từ đầu bằng cách sử dụng Ansible và Kubeadm, sau đó là triển khai một ứng dụng [Nginx](https://vietnix.vn/nginx-la-gi/) bên trong hệ thống này.

## Mục tiêu

Cluster của bạn sẽ bao gồm các tài nguyên như sau:

- **Một Control Plane Node**: Mỗi node trong Kubernetes sẽ chỉ một server chịu trách nhiệm quản lý trạng thái của Cluster. Nhiệm vụ của Contol Plane Node là chạy **Etcd** – nơi lưu trữ dữ liệu của Cluster giữa các thành phần đảm nhận quá trình lên lịch công việc cho các Worker Nodes.
- **Hai Worker Nodes**: Là các server nơi lượng công việc của bạn (tức là các ứng dụng và dịch vụ được chứa trong container) sẽ được chạy. Một Worker sẽ tiếp tục chạy lượng công việc đó sau khi đã được giao, ngay cả khi Control Plane ngừng hoạt động do quá trình thiết lập lịch trình đã hoàn tất. Công suất của một Cluster có thể được tăng lên nhờ vào việc tăng thêm các Workers.

Sau khi hoàn thành bài hướng dẫn này, bạn sẽ có một Cluster sẵn sàng để chạy các ứng dụng được chứa trong container, miễn là các server có đủ tài nguyên [CPU](https://vietnix.vn/cpu-la-gi/) và [RAM](https://vietnix.vn/ram-la-gi/) để chạy chúng. Và hầu hết các ứng dụng Unix truyền thống như ứng dụng web, cơ sở dữ liệu, daemon và command line đều có thể được chứa bởi container và chạy trên Cluster. Bản thân mỗi Cluster chỉ tiêu thụ khoảng 300 – 500 MB bộ nhớ và 10% CPU trên mỗi node.

Khi Cluster được thiết lập, các bạn sẽ triển khai **Nginx** web server cho Cluster đó để đảm bảo rằng nó đang chạy chính xác lượng công việc được giao.

[](https://lixi.vietnix.vn/?utm_source=website&utm_medium=banner-single-post&utm_campaign=li-xi-tet)[![Banner WordPress Hosting Singlepost](https://static-xf1.vietnix.vn/wp-content/uploads/2023/02/banner-singlepost.jpg)](https://vietnix.vn/wordpress-hosting/)

_Chương trình ra mắt dịch vụ WordPress Hosting miễn phí 500 mẫu website_

## Yêu cầu tiên quyết

- Cặp khóa SSH trên máy local Linux/ macOS/ BSD của bạn.
- Ba server chạy [Ubuntu 20.04](https://vietnix.vn/ubuntu-20-04/) với ít nhất 2GB RAM và 2 vCPU trên mỗi server. Và có thể kết nối đến ba servers đó bằng SSH với tư cách là **root** user bằng cặp khóa SSH trên.
- Ansible được cài đặt trên máy local.
- Đã làm quen, sử dụng qua playbook trong Ansible.
- Biết cách cách khởi chạy container từ image của [Docker](https://vietnix.vn/docker-la-gi/).

**Lưu ý:** Nếu chưa bao giờ đăng nhập bằng SSH vào những server trên thì bạn có thể bị nhắc chấp nhận vân tay server ở các bước thực hiện. Để hạn chế sự bất tiện này thì bạn nên làm điều này ngay bây giờ hoặc tắt tính năng kiểm tra host key trên server.

## Các bước tiến hành

Sau đây là hướng dẫn chi tiết các bước tiến hành tạo Kubernetes Cluster bằng Kubeadm trên Ubuntu 20.04. Mời bạn cùng theo dõi và thực hiện theo những bước này:

![Hướng dẫn tạo Kubernetes Cluster bằng Kubeadm trên Ubuntu 20.04](https://static-xf1.vietnix.vn/wp-content/uploads/2023/05/tao-kubernetes-cluster-bang-kubeadm-tren-ubuntu-20-04.webp)

Hướng dẫn tạo Kubernetes Cluster bằng Kubeadm trên Ubuntu 20.04

### Bước 1: Thiết lập Workspace Directory và file Inventory của Ansible

Trong bước này, bạn sẽ tạo một thư mục trên máy local để dùng làm workspace. Bạn cũng tiến hành cấu hình Ansible để có thể giao tiếp và thực thi các lệnh trên remote server. Sau đó, tiếp tục tạo một file `hosts` chứa các thông tin như [địa chỉ IP](https://vietnix.vn/dia-chi-ip-la-gi/) và các group của mỗi server.

Trong số ba máy chủ bạn đang sở hữu, một máy chủ sẽ là Control Plane với IP `control_plane_ip`. Hai máy chủ còn lại sẽ là Worker và sẽ có IP `worker_1_ip` và `worker_2_ip`.

Bắt đầu với việc tạo một thư mục có tên `~/kube-cluster` trong thư mục **home** trên máy local của bạn và `cd` vào đó:

Copy

```bash
mkdir ~/kube-cluster
cd ~/kube-cluster
```

Thư mục này sẽ là nơi làm việc của bạn trong những phần còn lại của hướng dẫn và sẽ chứa tất cả các playbook của Ansible. Đây cũng sẽ là thư mục dùng để chạy tất cả các lệnh local.

Tiếp theo tạo một file có tên `~/kube-cluster/hosts` bằng `nano` hoặc text editor tùy ý:

Copy

```bash
nano ~/kube-cluster/hosts
```

Thêm đoạn sau vào file, để chỉ định thông tin về cấu trúc logic của Cluster:

Copy

```plain
[control_plane]
control1 ansible_host=control_plane_ip ansible_user=root 

[workers]
worker1 ansible_host=worker_1_ip ansible_user=root
worker2 ansible_host=worker_2_ip ansible_user=root

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```

**Trong đó:**

- Các inventory file trong Ansible được sử dụng để chỉ định thông tin server như địa chỉ IP, remote user và sau đó nhóm các server này thành một đơn vị để thực thi lệnh trên đó.
- `~/kube-cluster/hosts` sẽ là file inventory và bạn đã thêm hai nhóm Ansible (**Control Plane** và **Worker**) vào đó để chỉ định cấu trúc logic cho Cluster.
- Trong **nhóm Control Plane**, có một mục nhập server có tên “control1” để liệt kê IP của Control Plane (`control_plane_ip`) và chỉ định rằng Ansible sẽ chạy các lệnh từ xa với tư cách là **root** user. Tương tự, trong **nhóm Worker**, có hai mục dành nhập server cho worker (`worker_1_ip` và `worker_2_ip`) và chỉ định `ansible_user` có quyền root.
- Dòng cuối cùng của file yêu cầu Ansible sử dụng trình thông dịch Python 3 của remote server cho các hoạt động quản lý.

Lưu và đóng file sau khi hoàn tất. Nếu các bạn đang sử dụng `nano`, hãy nhấn `Ctrl + X`, sau đó khi được nhắc, hãy nhấn `Y` và `Enter`.

Sau khi thiết lập inventory của server, bây giờ các bạn sẽ chuyển sang cài đặt các dependencies cấp hệ điều hành và cài đặt cho cấu hình.

### Bước 2: Tạo một non-root user trên tất cả các remote servers

Trong phần này, bạn sẽ tạo **non-root** user với đặc quyền `sudo` trên tất cả các máy chủ để sau này có thể SSH vào chúng theo cách thủ công với tư cách là người dùng không có quyền `sudo`. Điều này thực sự hữu ích trong nhiều trường hợp.

Ví dụ như bạn muốn xem thông tin hệ thống bằng các lệnh như `top/htop`, xem danh sách các containers đang chạy hoặc thay đổi các files cấu hình do **root** sở hữu. Các thao tác này được thực hiện thường xuyên trong quá trình bảo trì một Cluster. Việc sử dụng **non-root** user cho những tác vụ đó sẽ giảm thiểu rủi ro sửa đổi hoặc xóa các files quan trọng hoặc vô tình thực hiện các thao tác nguy hiểm khác.

Bắt đầu bằng cách tạo một tệp có tên `~/kube-cluster/initial.yml` trong workspace của bạn:

Copy

```bash
nano ~/kube-cluster/initial.yml
```

Tiếp theo, thêm các **play** sau vào file để tạo **non-root** user với đặc quyền `sudo` trên tất cả các máy chủ. Mỗi play trong Ansible là tập hợp các bước nhắm đến máy chủ và nhóm cụ thể. Với play dưới đây sẽ tạo một **non-root** user được cấp đặc quyền `sudo`:

Copy

```plain
---
- hosts: all
  become: yes
  tasks:
    - name: create the 'ubuntu' user
      user: name=ubuntu append=yes state=present createhome=yes shell=/bin/bash

    - name: allow 'ubuntu' to have passwordless sudo
      lineinfile:
        dest: /etc/sudoers
        line: 'ubuntu ALL=(ALL) NOPASSWD: ALL'
        validate: 'visudo -cf %s'

    - name: set up authorized keys for the ubuntu user
      authorized_key: user=ubuntu key="{{item}}"
      with_file:
        - ~/.ssh/id_rsa.pub
```

Dưới đây là những gì playbook này thực hiện:

- Tạo user non-root tên `ubuntu`.
- Cấu hình file `sudoers` để cho phép người dùng `ubuntu` chạy các lệnh `sudo` mà không cần mật khẩu.
- Thêm public key trong máy local của bạn (thường là `~/.ssh/id_rsa.pub`) vào danh sách các khóa được ủy quyền của người dùng `ubuntu` từ xa. Điều này sẽ cho phép truy cập bằng SSH vào từng máy chủ với tư cách là người dùng `ubuntu`.

Lưu và đóng tệp sau khi bạn đã hoàn thành.

Tiếp theo, chạy playbook local trên máy:

Copy

```bash
ansible-playbook -i hosts ~/kube-cluster/initial.yml
```

Lệnh trên sẽ hoàn thành trong vòng hai đến năm phút. Sau khi hoàn thành, bạn sẽ thấy output tương tự như sau:

Copy

```plain
Output
PLAY [all] ****

TASK [Gathering Facts] ****
ok: [control1]
ok: [worker1]
ok: [worker2]

TASK [create the 'ubuntu' user] ****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [allow 'ubuntu' user to have passwordless sudo] ****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [set up authorized keys for the ubuntu user] ****
changed: [worker1] => (item=ssh-rsa AAAAB3...)
changed: [worker2] => (item=ssh-rsa AAAAB3...)
changed: [control1] => (item=ssh-rsa AAAAB3...)

PLAY RECAP ****
control1                     : ok=4    changed=3    unreachable=0    failed=0   
worker1                    : ok=4    changed=3    unreachable=0    failed=0   
worker2                    : ok=4    changed=3    unreachable=0    failed=0   
```

Bây giờ, quá trình thiết lập sơ bộ ban đầu đã hoàn tất, bạn có thể chuyển sang cài đặt các dependencies dành riêng cho Kubernetes.

### Bước 3: Cài đặt các Dependencies của Kubernetes

Trong phần này, bạn sẽ cài đặt các packages ở cấp hệ điều hành theo yêu cầu của Kubernetes với package manager của Ubuntu. Các packages này bao gồm:

- **Docker** – một runtime container: Đây là thành phần chạy các containers của bạn. Tuy Kubernetes cũng hỗ trợ các loại runtime khác, nhưng Docker vẫn là một lựa chọn phổ biến và đơn giản.
- `kubeadm` – một công cụ CLI hỗ trợ cài đặt và cấu hình các thành phần khác nhau của Cluster theo một cách tiêu chuẩn.
- `kubelet` – một dịch vụ/chương trình hệ thống chạy trên tất cả các node và hỗ trợ xử lý các hoạt động ở cấp độ node.
- `kubectl` – một công cụ CLI được sử dụng để đưa ra các lệnh cho Cluster thông qua máy chủ API.

Bắt đầu bằng việc tạo một file có tên `~/kube-cluster/kube-dependencies.yml` trong workspace như sau:

Copy

```bash
nano ~/kube-cluster/kube-dependencies.yml
```

Thêm các play sau vào file để cài đặt các packages vào servers:

Copy

```plain
---
- hosts: all
  become: yes
  tasks:
   - name: create Docker config directory
     file: path=/etc/docker state=directory

   - name: changing Docker to systemd driver
     copy:
      dest: "/etc/docker/daemon.json"
      content: |
        {
        "exec-opts": ["native.cgroupdriver=systemd"]
        }

   - name: install Docker
     apt:
       name: docker.io
       state: present
       update_cache: true

   - name: install APT Transport HTTPS
     apt:
       name: apt-transport-https
       state: present

   - name: add Kubernetes apt-key
     apt_key:
       url: https://packages.cloud.google.com/apt/doc/apt-key.gpg
       state: present

   - name: add Kubernetes' APT repository
     apt_repository:
      repo: deb http://apt.kubernetes.io/ kubernetes-xenial main
      state: present
      filename: 'kubernetes'

   - name: install kubelet
     apt:
       name: kubelet=1.22.4-00
       state: present
       update_cache: true

   - name: install kubeadm
     apt:
       name: kubeadm=1.22.4-00
       state: present

- hosts: control_plane
  become: yes
  tasks:
   - name: install kubectl
     apt:
       name: kubectl=1.22.4-00
       state: present
       force: yes
```

Lần play đầu tiên trong playbook thực hiện như sau:

- Cài đặt **Docker**, một runtime container và cấu hình các cài đặt tương thích.
- Cài đặt `apt-transport-https`, cho phép thêm các nguồn HTTPS bên ngoài vào danh sách nguồn APT của mình.
- Thêm khóa apt trong repository của Kubernetes APT để xác minh khóa.
- Thêm repository của Kubernetes APT vào danh sách nguồn APT của máy chủ từ xa.
- Cài đặt `kubelet` và `kubeadm`.

Lần play thứ hai bao gồm một tác vụ duy nhất là cài đặt `kubectl` trên Control Plane Node. Lưu và đóng file khi hoàn tất.

**Lưu ý:** Mặc dù document của Kubernetes khuyên bạn nên sử dụng phiên bản mới nhất cho môi trường của mình, nhưng bài hướng dẫn này sử dụng một phiên bản cụ thể (1.22). Nếu thực hiện đúng theo hướng dẫn này thì bạn chắc chắn sẽ thao tác thành công. Tuy nhiên vì Kubernetes thay đổi nhanh chóng nên phiên bản mới nhất có thể không hoạt động với bài hướng dẫn này. Ngoài ra, mặc dù “xenial” là tên của Ubuntu 16.04 và bài hướng dẫn này dành cho Ubuntu 20.04 nhưng Kubernetes vẫn phù hợp các nguồn gói Ubuntu 16.04 theo mặc định và vẫn được hỗ trợ trên 20.04 trong trường hợp này.

Tiếp theo, chạy playbook bằng lệnh:

Copy

```bash
ansible-playbook -i hosts ~/kube-cluster/kube-dependencies.yml
```

Sau khi hoàn thành, bạn sẽ nhận được output tương tự như sau:

Copy

```plain
Output
PLAY [all] ****

TASK [Gathering Facts] ****
ok: [worker1]
ok: [worker2]
ok: [control1]

TASK [create Docker config directory] ****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [changing Docker to systemd driver] ****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [install Docker] ****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [install APT Transport HTTPS] *****
ok: [control1]
ok: [worker1]
changed: [worker2]

TASK [add Kubernetes apt-key] *****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [add Kubernetes' APT repository] *****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [install kubelet] *****
changed: [control1]
changed: [worker1]
changed: [worker2]

TASK [install kubeadm] *****
changed: [control1]
changed: [worker1]
changed: [worker2]

PLAY [control1] *****

TASK [Gathering Facts] *****
ok: [control1]

TASK [install kubectl] ******
changed: [control1]

PLAY RECAP ****
control1                     : ok=11    changed=9    unreachable=0    failed=0   
worker1                    : ok=9    changed=8    unreachable=0    failed=0  
worker2                    : ok=9    changed=8    unreachable=0    failed=0  
```

Sau khi chạy playbook này, **Docker**, `kubeadm` và `kubelet` sẽ được cài đặt trên tất cả các máy chủ từ xa. `kubectl` không phải là một thành phần bắt buộc và chỉ cần thiết cho việc thực thi các lệnh Cluster. Việc chỉ cài đặt `kubectl` trên Control Plane Node là hợp lí trong hoàn cảnh này vì bạn sẽ chỉ chạy các lệnh `kubectl` từ Control Plane Node. Tuy nhiên, hãy lưu ý rằng các lệnh `kubectl` có thể được chạy từ bất kỳ Worker Node nào hoặc từ bất kỳ máy tính nào mà `kubectl` có thể được cài đặt và cấu hình để trỏ đến một Cluster.

Như vậy, tất cả các dependencies của hệ thống hiện đã được cài đặt. Ở bước tiếp theo, bạn sẽ tiến hành thiết lập Control Plane Node và khởi tạo Cluster.

Để triển khai và quản lý Kubernetes Cluster một cách hiệu quả, không lo lắng về vấn đề hiệu suất và độ ổn định, bạn có thể tham khảo dịch vụ VPS tại Vietnix. Đối với yêu cầu cấu hình tối thiểu 2GB RAM và 2 vCPU bạn có thể lựa chọn các gói VPS CHEAP 3, VPS BASIC 3, VPS PREMIUM 3, VPS NVME 3 trở lên.

![Bảng giá thuê VPS tốc độ cao tại Vietnix](https://static-xf1.vietnix.vn/wp-content/uploads/2023/05/bang-gia-dich-vu-vps-toc-do-cao-tai-vietnix-1.webp)

Bảng giá thuê VPS tốc độ cao tại Vietnix

Các gói dịch vụ VPS tại Vietnix được đánh giá cao về tốc độ, sự ổn định và bảo mật. Ngoài ra, đội ngũ kỹ thuật Vietnix luôn sẵn sàng hỗ trợ bạn 24/7, giúp bạn vận hành và quản lý VPS dễ dàng, triển khai dự án hiệu quả nhất.

Liên hệ Vietnix để biết thêm thông tin về các gói [VPS tốc độ cao](https://vietnix.vn/vps-nvme/).

[Đăng ký ngay VPS tốc độ cao giảm tới 30%](https://vietnix.vn/vps-nvme/)

### Bước 4: Thiết lập Control Plane Node

Trong phần này, bạn sẽ thiết lập Control Plane Node. Tuy nhiên, trước khi tạo bất kỳ playbook nào, bạn nên hiểu rõ một số khái niệm như Pod và Plugin Network Pod, vì Cluster của bạn sẽ bao gồm cả hai yếu tố này.

**Pod** là một đơn vị nhỏ nhất chạy một hoặc nhiều container. Các container này chia sẻ các tài nguyên như khối lượng file và network interface chung. Các Pods là đơn vị thiết lập lịch trình cơ bản trong Kubernetes, trong đó tất cả các containers trong một Pod sẽ được đảm bảo chạy trên cùng một Node nơi mà Pod được thiết lập trên đó.

Mỗi Pod có địa chỉ IP riêng. Địa chỉ này cho phép các Pod tren node truy cập lẫn nhau. Còn các containers trên một node có thể giao tiếp dễ dàng với nhau thông qua local interface. Tuy nhiên, giao tiếp giữa các Pods phức tạp hơn và yêu cầu phải có một network riêng biệt có thể định tuyến lưu lượng traffic rõ ràng từ một Pod trên node này sang Pod trên node khác.

Chức năng này được cung cấp bởi các network plugins của Pod. Đối với Cluster, bạn sẽ sử dụng **Flannel** – một lựa chọn ổn định và hiệu quả hơn.

Tạo một playbook Ansible có tên `control-plane.yml` trên máy:

Copy

```bash
nano ~/kube-cluster/control-plane.yml
```

Thêm play sau vào file để khởi tạo Cluster và cài đặt Flannel:

Copy

```plain
---
- hosts: control_plane
  become: yes
  tasks:
    - name: initialize the cluster
      shell: kubeadm init --pod-network-cidr=10.244.0.0/16 >> cluster_initialized.txt
      args:
        chdir: $HOME
        creates: cluster_initialized.txt

    - name: create .kube directory
      become: yes
      become_user: ubuntu
      file:
        path: $HOME/.kube
        state: directory
        mode: 0755

    - name: copy admin.conf to user's kube config
      copy:
        src: /etc/kubernetes/admin.conf
        dest: /home/ubuntu/.kube/config
        remote_src: yes
        owner: ubuntu

    - name: install Pod network
      become: yes
      become_user: ubuntu
      shell: kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml >> pod_network_setup.txt
      args:
        chdir: $HOME
        creates: pod_network_setup.txt
```

Đây là bảng phân tích của lần play này:

- Tác vụ đầu tiên khởi tạo Pod bằng cách chạy `kubeadm init`. Truyền đối số `--pod-network-cidr=10.244.0.0/16` chỉ định subnet riêng tư mà IP của Pod sẽ được giao từ đó. Theo mặc đinh, Flannel sử dụng subnet trên; và bạn đang yêu cầu `kubeadm` sử dụng subnet đó.
- Tác vụ thứ hai tạo một thư mục `.kube` tại `/home/ubuntu`. Thư mục này sẽ chứa thông tin cấu hình, chẳng hạn như các file lưu admin keys – nơi được yêu cầu để kết nối với Cluster và địa chỉ API của Cluster.
- Tác vụ thứ ba sao chép file `/etc/kubernetes/admin.conf` được tạo từ `kubeadm init` vào thư mục chính của người dùng không phải **root**. Điều này sẽ cho phép các bạn sử dụng `kubectl` để truy cập Pod mới được tạo.
- Tác vụ cuối cùng chạy `kubectl apply` để cài đặt **`Flannel`**. `kubectl apply -f descriptor.[yml|json]` là cú pháp để yêu cầu `kubectl` tạo các đối tượng được mô tả trong file `descriptor.[yml|json]`. Tệp `kube-flannel.yml` chứa mô tả về các đối tượng cần thiết để thiết lập `Flannel` trong cụm.

Lưu và đóng file khi hoàn tất.

Chạy playbook cục bộ bằng lệnh sau:

Copy

```bash
ansible-playbook -i hosts ~/kube-cluster/control-plane.yml
```

Sau khi hoàn thành, các bạn sẽ thấy output tương tự như sau:

Copy

```plain
Output

PLAY [control1] ****

TASK [Gathering Facts] ****
ok: [control1]

TASK [initialize the cluster] ****
changed: [control1]

TASK [create .kube directory] ****
changed: [control1]

TASK [copy admin.conf to user's kube config] *****
changed: [control1]

TASK [install Pod network] *****
changed: [control1]

PLAY RECAP ****
control1                     : ok=5    changed=4    unreachable=0    failed=0  
```

Để kiểm tra trạng thái của Control Plane Node, hãy SSH vào node đó bằng lệnh sau:

Copy

```bash
ssh ubuntu@control_plane_ip
```

Khi đã ở trong Control Plane Node, hãy thực hiện:

Copy

```bash
kubectl get nodes
```

Bây giờ các bạn sẽ thấy output tương tự như dưới đây:

Copy

```plain
Output
NAME     STATUS   ROLES                  AGE   VERSION
control1   Ready    control-plane,master   51s   v1.22.4
```

**Lưu ý:** Kể từ Ubuntu 20.04, kubernetes đang trong quá trình cập nhật lại thuật ngữ cũ. `Control Plane` Node trong suốt hướng dẫn này từng được gọi là `master` node và đôi khi bạn sẽ thấy kubernetes gán hay dùng đồng thời cả hai thuật ngữ trên vì lý do tương thích.

Output cho biết rằng `Control Plane` Node đã hoàn thành tất cả các tác vụ khởi tạo và ở trạng thái sẵn sàng để bắt đầu chấp nhận các Worker Node cũng như thực hiện tác vụ được gửi đến máy chủ API. Ở bước tiếp theo, bạn có thể bắt đầu thêm worker từ máy của mình.

### Bước 5: Thiết lập các Worker Nodes

Thêm các workers vào Cluster bao gồm việc thực hiện một lệnh duy nhất trên mỗi Worker. Lệnh này bao gồm thông tin Pod cần thiết, chẳng hạn như địa chỉ IP, Port của máy chủ Control Plane Node và token bảo mật. Chỉ các node vượt token bảo mật mới có thể tham gia Cluster.

Điều hướng trở lại nơi làm việc của các bạn và tạo một playbook có tên là `worker.yml`:

Copy

```bash
nano ~/kube-cluster/workers.yml
```

Thêm các dòng sau vào file để thêm workers vào Cluster:

Copy

```plain
---
- hosts: control_plane
  become: yes
  gather_facts: false
  tasks:
    - name: get join command
      shell: kubeadm token create --print-join-command
      register: join_command_raw

    - name: set join command
      set_fact:
        join_command: "{{ join_command_raw.stdout_lines[0] }}"


- hosts: workers
  become: yes
  tasks:
    - name: join cluster
      shell: "{{ hostvars['control1'].join_command }} >> node_joined.txt"
      args:
        chdir: $HOME
        creates: node_joined.txt
```

Đây là những gì playbook làm:

- Lần play đầu tiên giúp lấy những lệnh cần được chạy trên các Worker nodes. Lệnh này sẽ có định dạng sau: `kubeadm join --token <token> <control-plane-ip>:<control-plane-port> --Discovery-token-ca-cert-hash sha256:<hash>`. Sau khi nhận được lệnh với **token** và **hash** values, tác vụ sẽ thiết lập lệnh đps thành fact để lần play kế tiếp có thể truy cập thông tin đó.
- Lần play thứ hai có một nhiệm vụ duy nhất là chạy lệnh tham gia trên tất cả các Workder nodes. Sau khi hoàn thành nhiệm vụ này, hai Worker nodes sẽ là trở thành một phần của Cluster.

Lưu và đóng file khi bạn hoàn tất.

Chạy playbook cục bộ bằng lệnh sau:

Copy

```bash
ansible-playbook -i hosts ~/kube-cluster/workers.yml
```

Sau khi hoàn thành, bạn sẽ thấy output tương tự như sau:

Copy

```plain
Output
PLAY [control1] ****

TASK [get join command] ****
changed: [control1]

TASK [set join command] *****
ok: [control1]

PLAY [workers] *****

TASK [Gathering Facts] *****
ok: [worker1]
ok: [worker2]

TASK [join cluster] *****
changed: [worker1]
changed: [worker2]

PLAY RECAP *****
control1                     : ok=2    changed=1    unreachable=0    failed=0   
worker1                    : ok=2    changed=1    unreachable=0    failed=0  
worker2                    : ok=2    changed=1    unreachable=0    failed=0  
```

Với việc bổ sung các Worker nodes, Cluster của bạn hiện đã được thiết lập và hoạt động đầy đủ, với các Workers sẵn sàng hoạt động. Trước khi lên lịch cho các ứng dụng, bạn cần xác minh rằng Cluster đang hoạt động như dự tính.

### Bước 6: Xác minh Cluster

Một Cluster đôi khi có thể bị lỗi trong quá trình thiết lập do một Node bị hỏng hoặc kết nối mạng giữa Control Plane Node và các Worker Nodes không hoạt động chính xác. Do đó, bạn cần kiểm tra lại Cluster và đảm bảo rằng các Node đã và đang hoạt động chính xác.

Bạn sẽ cần kiểm tra trạng thái hiện tại của Cluster từ Control Plane Node để đảm bảo rằng các Nodes đã sẵn sàng. Nếu đã ngắt kết nối khỏi Control Plane Node, bạn có thể SSH trở lại đó bằng lệnh sau:

Copy

```bash
ssh ubuntu@control_plane_ip
```

Sau đó thực hiện lệnh sau để lấy trạng thái của Cluster:

Copy

```bash
kubectl get nodes
```

Bạn sẽ thấy output tương tự như sau:

Copy

```plain
Output
NAME     STATUS   ROLES                  AGE     VERSION
control1   Ready    control-plane,master   3m21s   v1.22.0
worker1  Ready    <none>                 32s     v1.22.0
worker2  Ready    <none>                 32s     v1.22.0
```

Nếu tất cả các Nodes của bạn có giá trị `Ready` ở phần `STATUS`, điều đó có nghĩa chúng là đã một phần của Cluster và sẵn sàng để hoạt động.

Tuy nhiên, nếu một số Nodes có `STATUS` là `NotReady`, điều đó có thể là các Worker Nodes chưa hoàn thành quá trình thiết lập. Hãy đợi khoảng 5 đến 10 phút trước khi chạy lại nút `kubectl get` và kiểm tra ouput mới. Nếu vẫn có trạng thái `NotReady`, bạn có thể phải xác minh và chạy lại các lệnh ở những bước trước đó.

Bây giờ, Cluster đã được kiểm tra thành công. Tiếp theo bạn hãy lên lịch cho một ứng dụng Nginx mẫu trên Cluster này.

### Bước 7: Chạy ứng dụng trên Cluster

Giờ đây, bạn có thể triển khai bất kỳ ứng dụng được đóng gói nào vào Cluster của mình. Để làm quen, hãy triển khai Nginx bằng Deployments và Services để tìm hiểu cách ứng dụng này có thể được triển khai cho Cluster. Ngoài ra, bạn cũng có thể sử dụng các lệnh bên dưới cho ứng dụng được chứa trong container khác, miễn là thay đổi tên image của Docker và bất kỳ flag có liên quan khác (chẳng hạn như `ports` và `volumes`).

Đảm bảo rằng bạn đã đăng nhập vào Control Plane Node, sau đó chạy lệnh sau để tạo một deployment có tên `nginx`:

Copy

```bash
kubectl create deployment nginx --image=nginx
```

Mỗi deployment là một đối tượng trong Kubernetes giúp đảm bảo luôn có một lượng Pod cụ thể đang chạy dựa trên mẫu đã xác định, ngay cả khi các Pods gặp sự cố trong suốt khoảng thời gian tồn tại của Cluster. Việc triển khai ở trên sẽ tạo một Pod với một container từ image của Docker có tên Nginx Docker.

Tiếp theo, hãy chạy lệnh sau để tạo một ứng dụng công khai có tên `nginx`. Lệnh này dựa trên `NodePort`, một sơ đồ giúp Pod có thể truy cập được thông qua một cổng tùy ý được mở trên mỗi Node của Cluster:

Copy

```bash
kubectl expose deploy nginx --port 80 --target-port 80 --type NodePort
```

Dịch vụ là một loại đối tượng khác của Kubernetes giúp hiển thị các dịch vụ nội bộ của Cluster cho client, bao gồm cả bên trong và bên ngoài. Chúng cũng có khả năng giúp cân bằng yêu cầu tải cho nhiều Pods và là thành phần không thể thiếu trong Kubernetes.

Chạy lệnh sau:

Copy

```bash
kubectl get services
```

Lệnh này sẽ xuất các thông tin tương tự như sau:

Copy

```plain
Output
NAME         TYPE        CLUSTER-IP       EXTERNAL-IP           PORT(S)             AGE
kubernetes   ClusterIP   10.96.0.1        <none>                443/TCP             1d
nginx        NodePort    10.109.228.209   <none>                80:nginx_port/TCP   40m
```

Từ dòng `nginx` và `nginx_port` của output trên có thể truy xuất Port mà Nginx đang chạy. Kubernetes sẽ tự động chỉ định một Port ngẫu nhiên lớn hơn 30000, đồng thời đảm bảo rằng Port đó chưa bị ràng buộc hay bị sử dụng bởi một dịch vụ khác.

Để kiểm tra xem mọi thứ có đang hoạt động hay không, hãy truy cập `http://worker_1_ip:nginx_port` hoặc `http://worker_2_ip:nginx_port` thông qua trình duyệt trên máy của bạn. Bạn sẽ thấy trang chào mừng quen thuộc của Nginx.

Nếu muốn xóa ứng dụng Nginx, trước tiên hãy xóa dịch vụ `nginx` khỏi Control Plane Node:

Copy

```bash
kubectl delete service nginx
```

Chạy lệnh sau để đảm bảo rằng dịch vụ đã bị xóa:

Copy

```bash
kubectl get services
```

Bạn sẽ thấy output như sau:

Copy

```plain
Output
NAME         TYPE        CLUSTER-IP       EXTERNAL-IP           PORT(S)        AGE
kubernetes   ClusterIP   10.96.0.1        <none>                443/TCP        1d
```

Sau đó xóa deployment:

Copy

```bash
kubectl delete deployment nginx
```

Chạy lệnh sau để xác nhận rằng thao tác xóa deployment đã thực hiện thành công:

Copy

```bash
kubectl get deployments
```

Copy

```plain
Output
No resources found.
```

Vietnix là nhà cung cấp dịch vụ VPS hàng đầu tại Việt Nam với hơn 10 năm kinh nghiệm và hơn 50.000 khách hàng tin tưởng sử dụng. Nếu bạn đang có nhu cầu thuê VPS để tạo Kubernetes Cluster bằng Kubeadm trên Ubuntu 20.04, hãy liên hệ với Vietnix để được tư vấn lựa chọn gói dịch vụ phù hợp.

Vietnix không chỉ nổi tiếng về chất lượng sản phẩm mà còn đặc biệt chú trọng đến dịch vụ hỗ trợ khách hàng. Điều này được minh chứng bởi 97% khách hàng đã sử dụng dịch vụ Vietnix đánh giá cao với 5 sao, 89% khách hàng duy trì sử dụng dịch vụ đến thời điểm hiện tại.

Với sự nỗ lực không ngừng nghỉ để nâng cao chất lượng và mang lại sự hài lòng cho khách hàng, Vietnix đã được vinh danh với giải thưởng “[Thương hiệu Việt Nam xuất sắc năm 2022](https://vietnix.vn/vietnix-nhan-giai-thuong-hieu-viet-nam-xuat-sac-2022/)“.

Liên hệ ngay với Vietnix để trải nghiệm dịch vụ VPS tốc độ cao ngay hôm nay.

- **Địa chỉ:** 265 Hồng Lạc, Phường 10, Quận Tân Bình, Thành Phố Hồ Chí Minh
- **Hotline:** 1800 1093
- **Email:** sales@vietnix.com.vn

## Lời kết

Trong bài viết này, bạn đã thiết lập thành công cụm Kubernetes trên Ubuntu 20.04 một cách tự động hóa bằng Kubeadm và Ansible. Tiếp theo, bạn có thể thoải mái triển khai các ứng dụng và dịch vụ của riêng mình trên đó. Cảm ơn bạn đã theo dõi bài viết và đừng quên chia sẻ bài viết nếu cảm thấy nó hữu ích nhé.