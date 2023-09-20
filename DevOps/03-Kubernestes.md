# Kubernetes - Tìm hiểu về cách hoạt động của Kubernetes

Kubernetes là một nền tảng điều phối giúp quản lý hiệu quả các ứng dụng trong container. Vậy cụ thể hơn thì Kubernetes là gì? Vì sao chúng ta nên sử dụng Kubernetes?

## Kubernetes là gì?

[Kubernetes](https://kubernetes.io/vi/) (còn được gọi là k8s hay “kube”) là một nền tảng điều phối container mã nguồn mở. Ta có thể dùng Kubernetes để tự động hóa nhiều quy trình thủ công liên quan đến việc deploy, quản lý và mở rộng các ứng dụng trong container. Nói cách khác, ta có thể tập hợp các nhóm host đang chạy **Linux** container với nhau. Từ đó, Kubernetes có thể giúp dễ dàng quản lý các nhóm đó một cách hiệu quả nhất.

Ngoài ra, cluster **Kubernetes** có thể mở rộng các host trên các cloud tại chỗ, public, private hay hybrid. Do đó, Kubernetes là một nền tảng lý tưởng để host các ứng dụng **cloud-native** yêu cầu khả năng mở rộng nhanh chóng. Chẳng hạn như truyền dữ liệu theo thời gian thực thông qua Apache Kafka.

Ban đầu, Kubernetes được phát triển và thiết kế bởi các kỹ sư tại Google. Do đó, Google chính là một trong những người đóng góp đầu tiên cho công nghệ **container** của Linux. Đây cũng chính là công nghệ đằng sau các dịch vụ cloud của Google. Tính đến nay, Google tạo ra đến hơn 2 tỷ triển khai container mỗi tuần. Tất cả đều được cung cấp bởi nền tảng nội bộ Borg – tiền thân của Kubernetes.

[[Kubernetes tổng quan]]

![[Pasted image 20230907101036.png | 500]]

Kubernetes là gì?

## Ứng dụng của Kubernetes

Vậy ứng dụng của **Kubernetes là gì**? Trước hết, ưu điểm chính của việc sử dụng Kubernetes là nó cung cấp nền tảng để lên lịch và chạy các container trên những cluster máy vật lý hoặc máy ảo (VM). Việc này đặc biệt hữu ích nếu ta muốn tối ưu hóa việc dev app cho cloud.

Nói rộng hơn, sử dụng Kubernetes giúp ta triển khai đầy đủ hơn và dựa trên cơ sở hạ tầng container-based trong môi trường sản xuất. Ngoài ra, Kubernetes chủ yếu dùng để tự động hóa các task. Do đó ta có thể làm nhiều việc tương tự nhau mà các nền tảng ứng dụng hay hệ thống quản lý khác cho phép.

Bên cạnh đó, các developer cũng có thể tạo ra những ứng dụng cloud-native làm nền tảng runtime bằng các mẫu Kubernetes. Trong đó, các mẫu này là những công cụ mà một Kubernetes developer cần để build những ứng dụng hoặc dịch vụ container-based.

### Ta có thể sử dụng Kubernetes để

- Sắp xếp các container trên nhiều host.
- Sử dụng phần cứng hiệu quả hơn. Nhằm tối đa hóa tài nguyên cần thiết để chạy các ứng dụng doanh nghiệp.
- Kiểm soát và tự động hóa việc triển khai, cập nhật ứng dụng.
- Mount và thêm bộ nhớ để chạy ứng dụng có trạng thái.
- Mở rộng quy mô và các ứng dụng trong container, cũng như tài nguyên của chúng.
- Quản lý các dịch vụ một cách cụ thể, rõ ràng. Từ đó đảm bảo các ứng dụng đã deploy luôn chạy đúng theo kế hoạch.
- Kiểm tra tình trạng và tự phục hồi ứng dụng với tính năng tự thay thế, tự restart, tự nhân bản và tự động mở rộng.

Tuy nhiên, Kubernetes dựa trên nhiều project khác để có thể cung cấp đầy đủ các dịch vụ trên. Cụ thể, ta có thể thêm một số project mã nguồn mở sau để tận dụng tối đa sức mạnh của Kubernetes:

- Registry thông qua các dự án như Docker Registry.
- Networking, qua OpenvSwitch và intelligent edge routing.
- Telemetry thông qua Kibana, Hawkular hay Elastic.
- Bảo mật, với LDAP, SELinux, RBAC, OAUTH với multitenancy layers.
- Tự động hóa bằng cách bổng sung Ansible playbook để cài đặt và quản lý vòng đời của các cluster.
- Dịch vụ, thông qua một catalog chứa nhiều mẫu app phổ biến.

## Cách hoạt động của Kubernetes

Trong phần này, ta sẽ tìm hiểu cách hoạt động của **Kubernetes là gì**. Trước tiên, cần biết rằng mỗi triển khai một Kubernetes đang hoạt động được gọi là một cluster. Ta có thể hình dung Kubernetes cluster gồm hai phần: một control plane và một máy tính toán (compute machine) – node.

![[Pasted image 20230907101049.png]]

Mỗi node là một môi trường Linux của chính nó, đó có thể là một máy vật lý hay máy ảo. Mỗi node sẽ chạy các pod được tạo từ những container.

Control plane có nhiệm vụ duy trì trạng thái mong muốn của cluster. Chẳng hạn như ứng dụng đang chạy hay container image đang được sử dụng. Còn compute machine sẽ chạy các ứng dụng và workload.

Kubernetes control plane nhận các lệnh từ admin (hay DevOps team) và chuyển tiếp các lệnh đó đến compute machine. Việc này sẽ hoạt động với vô số dịch vụ để tự động quyết định node phù hợp nhất cho task. Tiếp đến, nó sẽ phân bổ tài nguyên và chỉ định các pod trong node để hoàn thành công việc được yêu cầu.

Trạng thái mong muốn của một cluster sẽ xác định các ứng dụng hoặc workload nên chạy. Cùng với đó là quyết định những image nào sẽ sử dụng, các tài nguyên nào nên được cung cấp và nhiều chi tiết cấu hình khác.

Xét về cơ sở hạ tầng, có rất ít thay đổi với cách ta quản lý container. Quyền kiểm soát container chỉ xảy ra ở một cấp độ cao hơn, giúp kiểm soát tốt hơn mà không cần phải quản lý vi mô từng container hay node riêng biệt.

Công việc của ta liên quan đến việc cấu hình Kubernetes, xác định node, pod và container bên trong chúng. Còn Kubernetes sẽ xử lý việc sắp xếp các container.

Ta có thể tự do lựa chọn nơi sử dụng Kubernetes. Có thể là trên bare metal server, máy ảo, nhà cung cấp public cloud, private cloud hay môi trường hybrid cloud. Một trong những ưu điểm chính của Kubernetes là nó có thể hoạt động trên nhiều cơ sở hạ tầng khác nhau.

## Những khái niệm cơ bản trong Kubernetes

Trước khi bắt đầu việc sử dụng Kubernetes hay tìm hiểu sâu hơn về kiến trúc đằng sau cách thức hoạt động của các tool Kubernetes là gì, hãy cùng xem qua 7 thuật ngữ phổ biến nhất của Kubernetes. Hiểu rõ được những thuật ngữ này, ta có thể dễ dàng dùng Kubernetes một cách hiệu quả nhất.

### Pod

Một pod gồm một hay nhiều container khác nhau. Các pod là đơn vị cơ bản nhất tồn tại bên trong Kubernetes. Do đó, về mặt kỹ thuật thì container không hẳn là một phần của Kubernetes – vì ngay cả một container duy nhất cũng được gọi là một pod.

Bất kỳ container nào bên trong pod đều chia sẻ tài nguyên và một mạng. Đồng thời, chúng có thể giao tiếp được với nhau, thậm chí khi ở trên những node riêng biệt.

### Node

Node là thành phần của phần cứng. Một node có thể là một máy ảo host bởi nhà cung cấp cloud, hay là một máy vật lý trong các data center. Tuy nhiên, để nghĩ về node một cách đơn giản hơn, ta có thể xem nó như các tài nguyên CPU/RAM được sử dụng bởi Kubernetes cluster, thay vì chỉ là các máy đơn lẻ. Sở dĩ vì các pod không bị giới hạn với bất kỳ máy nhất định nào, tại mọi thời điểm. Do đó, chúng sẽ di chuyển trên tất cả tài nguyên có sẵn để đạt được trạng thái mong muốn của ứng dụng.

Có hai loại node khác nhau là worker và master.

### Cluster

Các cluster chạy các ứng dụng nằm trong container do Kubernetes quản lý. Một cluster là một chuỗi các node được liên kết với nhau.

Bằng cách kết hợp với nhau, những node này có thể tổng hợp tài nguyên của chúng. Từ đó làm cho cluster mạnh hơn nhiều so với những máy riêng lẻ. Kubernetes di chuyển các pod xung quanh cluster khi những node được thêm hay xóa.

Một cluster có thể chứa nhiều node worker, và phải có ít nhất một node master.

### Services

Services là một đối tượng API hiển thị một ứng dụng. Về cơ bản, nó mô tả cách lưu lượng mạng sẽ truy cập vào một tập hợp các pod. Services có thể được tìm thấy ở trên mọi node.

### Deployment

Deployment là một đối tượng API, về cơ bản thì chúng quản lý việc nhân bản pod.

Một deployment xác định trạng thái của cluster. Chẳng hạn như xác định số lượng bản sao của một pod được chạy. Khi deployment được thêm vào một cluster, Kubernetes sẽ tự động tạo số pod chính xác rồi giám sát chúng. Nếu có một pod nào đó fail, Kubernetes sẽ nhân bản nó theo tiêu chí ‘deployment’.

### Kubeadm

Kubeadm là một công cụ cài đặt khởi động nhanh dành cho Kubernetes.

Nó giúp tạo một cluster khả thi tối thiểu, với một master node duy nhất. Kubeadm rất nhanh và dễ sử dụng. Thêm vào đó, nó đảm bảo các cluster tuân theo những phương pháp tốt nhất. Do đó, Kubeadm là một công cụ tuyệt vời với những người mới sử dụng Kubernetes. Ngoài ra, ta cũng có thể dùng Kubeadm trong việc kiểm thử các ứng dụng.

**Xem thêm:** [Cách tạo Kubernetes Cluster bằng Kubeadm trên Ubuntu 20.04](https://vietnix.vn/tao-kubernetes-cluster-bang-kubeadm-tren-ubuntu-20-04/)

### Minikube

Minikube là một phiên bản nhẹ hơn của Kubernetes. Đồng thời nó cũng dễ sử dụng nội bộ hơn. Nó sẽ tạo một máy ảo (VM) trên máy cục bộ, tại đó ta có thể chạy một single-node cluster. Việc này cũng rất hữu ích cho việc thử nghiệm.

## Tại sao nên sử dụng Kubernetes?

Với những ưu điểm đã kể trên, chắc hẳn ta cũng đã biết lý do sử dụng Kubernetes là gì. Kubernetes có thể giúp ta phân phối, quản lý các ứng dụng được chứa trong container, được kế thừa, cloud-native, cũng như những ứng dụng được tái cấu trúc thành microservices.

Để đáp ứng nhu cầu kinh doanh đang ngày càng biến động, các nhóm developer cần có khả năng nhanh chóng build những ứng dụng và dịch vụ mới. Quá trình phát triển cloud-native bắt đầu bằng những microservices trong container. Chúng cho phép ta develop nhanh hơn, dễ dàng chuyển đổi cũng như tối ưu hóa các ứng dụng hiện có.

Các ứng dụng sản xuất có trên rất nhiều container, và những container này phải được deploy trên nhiều server host. Kubernetes cho ta khả năng điều phối và quản lý cần thiết để deploy các container cho những workload này.

Việc điều phối Kubernetes cho phép ta build những dịch vụ ứng dụng trải rộng trên nhiều container. Đồng thời cũng có thể lên lịch cho các container đó trên một cluster, chia tỷ lệ container, quản lý tình trạng theo thời gian. Ngoài ra, sử dụng Kubernetes cũng giúp cải thiện đáng kể bảo mật IT.

Thêm vào đó, Kubernetes cũng cần được tích hợp với networking, storage, bảo mật, telemetry và nhiều dịch vụ khác để cung cấp cơ sở hạ tầng container toàn diện nhất.

![[Pasted image 20230907102904.png | 700]]

Khi mở rộng sang một môi trường sản xuất cà nhiều ứng dụng, chắc chắn ta cần có nhiều container làm việc cung nhau để có thể cung cấp những services riêng lẻ.

Linux container cung cấp các ứng dụng microservice-based một đơn vị triển khai ứng dụng lý tưởng. Cùng với đó là một môi trường thực thi khép kín (self-contained). Ngoài ra, các microservice trong container cũng giúp việc điều phối dịch vụ dễ dàng hơn. Trong đó gồm cả việc lưu trữ, networking và bảo mật.

Việc này sẽ làm tăng đáng kể số lượng container trong môi trường. Và từ đó dẫn đến độ phức tạp cũng tăng theo. Tuy nhiên, Kubernetes đã khắc phục rất nhiều vấn đề phổ biến liên quan đến việc này. Cụ thể, Kubernetes phân loại những container này thành các pods. Các pod sau đó sẽ thêm một lớp trừu tượng vào những container này. Từ đó ta có thể lên lịch các workload và cung cấp những dịch vụ cần thiết, chẳng hạn như networking hay lưu trữ, cho các container này.

Các phần các của Kubernetes cũng giúp cân bằng tải trên những pod này. Đồng thời đảm bảo số lượng container phù hợp để hỗ trợ workload của mình.

## So sánh giữa Kubernetes và Docker Swarm

Người dùng thường hay so sánh Kubernetes với Docker, tuy nhiên việc này không hẳn là chính xác. Nói đúng hơn, ta nên so sánh Kubernetes với Docker Swarm – vì đây là hai công nghệ container tương đương nhau. Trong đó, Docker Swarm là giải pháp điều phối container của Docker, Inc. Vậy sự khác nhau giữa Docker Swarm và Kubernetes là gì?

Swarm được tích hợp chặt chẽ với hệ sinh thái Docker và có API của riêng nó. Sự tích hợp này chính là một trong những lợi thế của Swarm so với Kubernetes. Sở dĩ vì việc chuyển đổi từ Docker sang Swarm là rất đơn giản. Còn Kubernetes thì sở hữu GUI của riêng nó, được lựa chọn bởi những người dùng thích sử dụng graphical interface hơn là command line.

Nói về công cụ, Kubernetes chiếm ưu thế vì có bộ công cụ phong phú hơn. Ngoài ra còn có thể được mở rộng và tùy chỉnh nhiều hơn so với Swarm, đặc biệt khi nói đến việc giám sát hệ thống và auto-scaling.

Nhìn chung, Swarm được xem là một giải pháp đơn giản hơn, dễ bắt đầu hơn và chủ yếu phù hợp cho việc phát triển. Còn Kubernetes thì không bị ràng buộc với Docker, hỗ trợ các quy trình làm việc phức tạp hơn. Bên cạnh đó, Kubernetes cũng phổ biến hơn so với Swarm trong các môi trường sản xuất.

**Xem thêm:** [Cách cấu hình tường lửa Linux cho Docker Swarm trên CentOS 7](https://vietnix.vn/cau-hinh-tuong-lua-linux-cho-docker-sawrm-tren-centos-7/)

## Lời kết

Hy vọng bài viết trên sẽ giúp bạn biết nhiều hơn về Kubernetes là gì? Nếu có thắc mắc hay đóng góp ý kiến, mời bạn để lại bình luận phía dưới bài viết này. Vietnix xin chân thành cảm ơn bạn!