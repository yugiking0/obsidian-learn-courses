- **API Group**

    Một tập những đường dẫn tương đối đến Kubernetes API.

    Bạn có thể cho phép hay vô hiệu từng API group bằng cách thay đổi cấu hình trên API server của mình. Đồng thời bạn cũng có thể vô hiệu hay kích hoạt các đường dẫn cho những tài nguyên cụ thể. API group đơn giản hóa việc mở rộng Kubernetes API. Nó được chỉ định dưới dạng REST và trong trường `apiVersion` của một đối tượng đã được chuyển hóa.

    - Đọc thêm về [API Group](https://kubernetes.io/docs/concepts/overview/kubernetes-api/#api-groups-and-versioning).

- **API server**

    Cũng được biết đến như là:_kube-apiserver_  

    API server là một thành phần của Kubernetes [control plane](https://kubernetes.io/vi/docs/reference/glossary/?all=true#term-control-plane), được dùng để đưa ra Kubernetes API. API server là front end của Kubernetes control plane.

    Thực thi chính của API server là [kube-apiserver](https://kubernetes.io/docs/reference/generated/kube-apiserver/). kube-apiserver được thiết kế để co giãn theo chiều ngang — có nghĩa là nó co giãn bằng cách triển khai thêm các thực thể. Bạn có thể chạy một vài thực thể của kube-apiserver và cân bằng lưu lượng giữa các thực thể này.

- **Biến môi trường trong Container**

    Biến môi trường của container là một cặp Tên-Giá trị nhằm cung cấp những thông tin hữu ích vô trong những containers bên trong một Pod.

    Biến môi trường của container cung cấp thông tin cần thiết cho mỗi ứng dụng cùng với những thông tin về những resources quan trọng đối với [Containers](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/#why-containers) đó. Ví dụ, thông tin chi tiết về file system, thông tin về bản thân của chính container đó, và những resources khác ở trong cluster như điểm kết của một services.

- **Bộ chọn (Selector)**

    Cho phép người dùng lọc ra một danh sách tài nguyên dựa trên labels (nhãn).

    Selectors được áp dụng khi truy vấn những danh sách tài nguyên để lọc dựa trên [labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels) chúng được đánh.

- **cgroup (control group)**

    Một nhóm các process trên Linux với sự tùy chọn trong cô lập tài nguyên, trách nhiệm và giới hạn.

    cgroup là một tính năng của Linux kernel giúp giới hạn, giao trách nhiệm, và cô lập việc sử dụng các tài nguyên trên máy (CPU, memory, disk I/O, network) cho một tập các process.

- **Chú thích (Annotation)**

    Một cặp khóa-giá trị được sử dụng để đính kèm tùy ý một metadata không xác định cụ thể vào các đối tượng.

    Metadata (siêu dữ liệu) có trong một annotation có thể nhỏ hoặc lớn, có cấu trúc hoặc không, và có thể bao gồm những kí tự không được cho phép như [Labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels). Các công cụ và thư viện ở phía client có thể thu thập những metadata này.

- **Cluster**

    Một tập các worker machine, được gọi là node, dùng để chạy các containerized application. Mỗi cụm (cluster) có ít nhất một worker node.

    Các worker node chứa các pod (là những thành phần của ứng dụng). Control Plane quản lý các worker node và pod trong cluster. Trong môi trường sản phẩm (production environment), Control Plane thường chạy trên nhiều máy tính và một cluster thường chạy trên nhiều node, cung cấp khả năng chịu lỗi (fault-tolerance) và tính sẵn sàng cao (high availability).

- **Container**

    Một image nhẹ, khả chuyển và có khả năng thực thi, chứa phần mềm và tất cả các dependencies của nó.

    Containers tách rời các ứng dụng khỏi hạ tầng máy chủ nhằm giúp cho việc triển khai dễ dàng hơn trên từng hệ thống cloud hay hệ điều hành khác nhau, và đơn giản hóa việc nhân rộng.

- **Container runtime interface (CRI)**

    Container runetime interface (CRI) là một API phục vụ cho việc tích hợp container runtimes với kubelet trên một node.

    Để biết thêm chi tiết, đọc thêm về [CRI](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-node/container-runtime-interface.md) API.

- **Control Plane**

    Tầng điều khiển container, được dùng để đưa ra API và các interface để định nghĩa, triển khai, và quản lý vòng đời của các container. [-]

    Tầng điều khiển container, được dùng để đưa ra API và các interface để định nghĩa, triển khai, và quản lý vòng đời của các container.

- **CustomResourceDefinition**

    Những đoạn custom code chỉ định một loại tài nguyên được thêm vào Kubenretes API server mà không cần thiết phải xây dựng một custom server hoàn chỉnh.

    Custom Resource Definitions cho phép bạn có thể mở rộng Kubernetes API cho môi trường của bạn trong trường hợp những API được cung cấp sẵn không đáp ứng được các nhu cầu của bạn.

- **DaemonSet**

    Đảm bảo một bản sao của [Pod](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/) đang chạy trên một tập các node của [cluster](https://kubernetes.io/vi/docs/reference/glossary/?all=true#term-cluster).

    Được sử dụng để deploy những system daemon ví dụ như log collector, monitoring agent, những cái thường phải chạy trên mọi [Node](https://kubernetes.io/docs/concepts/architecture/nodes/).

- **Deployment**

    Một API object quản lý việc nhân rộng bản sao của ứng dụng.

    Mỗi bản sao là một đại diện diện cho một [Pod](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/), và các pods này được phân bố giữa các nodes trong cluster.

- **Docker**

    Docker (cụ thể là Docker Engine) là một công nghệ phần mềm thực hiện việc ảo hóa tầng hệ điều hành, còn được gọi là container.

    Docker sử dụng khả năng cô lập các tài nguyên của Linux kernel như cgroups và kernel namespaces, cùng với một hệ thống tệp tin có khả năng kết hợp như OverlayFS và một vài thành phần khác để các containers có thể chạy độc lập trên cùng một máy Linux, tránh được việc bị overhead khi khởi động và bảo trì máy ảo (VMs).

- **kube-proxy**

    [kube-proxy](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy/) là một network proxy chạy trên mỗi node trong cluster, thực hiện một phần Kubernetes [Service](https://kubernetes.io/docs/concepts/services-networking/service/).

    kube-proxy duy trình network rules trên các node. Những network rules này cho phép kết nối mạng đến các pods từ trong hoặc ngoài cluster.

    Kube-proxy sử dụng lớp packet filtering của hệ điều hành nếu có sẵn. Nếu không thì kube-proxy sẽ tự điều hướng network traffic.

- **Kubelet**

    Một agent chạy trên mỗi node nằm trong cluster. Nó giúp đảm bảo rằng các containers đã chạy trong một pod.

    Kubelet sẽ nhận một tập các PodSpecs (đặc tính của Pod) được cung cấp thông qua các cơ chế khác nhau và bảo đảm rằng containers được mô tả trong những PodSpecs này chạy ổn định và khỏe mạnh. Kubelet không quản lý những containers không được tạo bởi Kubernetes.

- **Nhãn (Label)**

    Gán nhãn các đối tượng (tags objects) với các thuộc tính xác định, có ý nghĩa và có liên quan tới người dùng.

    Labels là những cặp key/value gắn liền với những đối tượng như [pod](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/). Chúng được dùng để tổ chức và chọn lựa giữa những tập hợp con của các đối tượng này.

- **Node**

    Một node là một máy worker trong Kubernetes

    Một worker node có thể là một máy tính ảo hay máy tính vậy lý, tùy thuộc vào cluster. Nó bao gồm một số daemons hoặc services cần thiết để chạy các [Pods](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/) và được quản lý bởi control plane. Daemons trên một node bao gồm [kubelet](https://kubernetes.io/docs/reference/generated/kubelet), [kube-proxy](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy/), và một container runtime triển khai theo [CRI](https://kubernetes.io/docs/concepts/overview/components/#container-runtime) như [Docker](https://docs.docker.com/engine/).

- **Pod**

    Đối tượng nhỏ nhất và đơn giản nhất của Kubernetes. Một Pod đại diện cho một tập các [containers](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/#why-containers) đang chạy trên cluster.

    Một Pod thường được set up để chạy với một container chính yếu. Nó đồng thời có thể chạy kèm với các sidecar containers giúp bổ trợ thêm một số tính năng như thu thập log. Các Pods thường được quản lý bởi một [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/).

- **Service**

    Một cách để thể hiện ứng dụng đang chạy trong một tập các [Pods](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/) dưới dạng dịch vụ mạng.

    Một tập các Pods được một Service nhắm đến (thường) được xác định với một [selector](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/). Nếu có nhiều Pods được thêm vào hay xóa đi, tập những Pods hợp với selector sẽ thay đổi. Service đảm bảo network traffic có thể đến tới tập những Pods để giải quyết công việc.

- **Taint**

    Là một đối tượng bao gồm ba thuộc tính bắt buộc: key, value, và effect. Taints (dấu chờ) ngăn cản việc lập lịch cho các pod chạy trên các [node](https://kubernetes.io/docs/concepts/architecture/nodes/) hay nhóm các node.

    Taints (dấu chờ) và tolerations hoạt động cùng với nhau để đảm bảo rằng các pod sẽ không lập lịch chạy lên những node không phù hợp. Có thể đặt một hoặc nhiều hơn một dấu chờ lên node. Một node chỉ có thể lập lịch chạy cho một pod với tolerations phù hợp với những dấu taint được cấu hình.

- **Ứng dụng**

    Một lớp nơi các ứng được đã được containerized chạy. [-]

    Một lớp nơi các ứng được đã được containerized chạy.

- **Vòng điều khiển (Controller)**

    Trong hệ thống Kubernetes, các bộ controllers là các vòng lặp điều khiển theo dõi trạng thái của mỗi [cluster](https://kubernetes.io/vi/docs/reference/glossary/?all=true#term-cluster), sau đó chúng sẽ tạo hoặc yêu cầu sự thay đổi cần thiết. Mỗi controller cố thực hiện việc thay đổi để giúp hệ thống chuyển từ trạng thái hiện tại sang trạng thái mong muốn.

    Vòng điều khiển lặp lại theo dõi trạng thái chung của cluster thông qua Kubernetes API server (một thần phần của [Control Plane](https://kubernetes.io/vi/docs/reference/glossary/?all=true#term-control-plane)).

    Một vài controllers chạy bên trong control plan, cung cấp các vòng lặp điều khiển vận hành nhân gốc của các hoạt động trong hệ thống Kubernetes. Ví dụ: với deployment controller, daemonset controller, namespace controller, và persistent volume controller (và một vài controller còn lại) đều chạy bên trong kube-controller-manager.