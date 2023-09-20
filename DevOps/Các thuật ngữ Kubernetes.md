# Các thuật ngữ Kubernetes
### Bài 01 : Tổng quan Kubernetes
- Deploy
- Deployment
- Hardware
- Operating System
- Hypervisor
- virtualization
- Virtual Machines - VMs
- Hypervisor
- Bin/Libary
- Container
- Container Deployment
- Container Runtime
- Bin/Libary
- Kubernetes chúng ta có thể group và quản lý Container theo ứng dụng và project
- Service Discovery and Load Balancing
- request của ứng dụng tới đúng container
- ứng dụng của chúng ta high available
- server vật lý gặp sự cố, nó có thể chuyển container của ta sang server vật lý khác
- auto scale resource
- auto restart application when failure
- zero downtime deployment
- automated rollouts and rollbacks application
- component of K8s
- Cluster
- Kubernetes Cluster
- Master nodes (control plane)
- Worker nodes
- API server, controller manager, Scheduler, Etcd
- API server: thành phần chính để giao tiếp với các thành phần khác
- Controller manager: gồm nhiều controller riêng cụ thể cho từng resource và thực hiện các chứng năng cụ thể cho từng thằng resource trong kube như create pod, create deployment, v...v...
- Scheduler: schedules ứng dụng tới node nào
- Etcd: là một database để lưu giữ trạng thái và resource của cluster

**Master nodes** bao gồm 4 thành phần chính là API server, controller manager, Scheduler, Etcd (mình sẽ giải thích rõ chức năng của từng thành phần trong bài viết khác):

- **API server**: thành phần chính để giao tiếp với các thành phần khác
- **Controller manager**: gồm nhiều **controller** riêng cụ thể cho từng resource và thực hiện các chứng năng cụ thể cho từng thằng resource trong kube như **create pod**, **create deployment**, v...v...
- **Scheduler**: schedules ứng dụng tới node nào
- **Etcd**: là một database để lưu giữ trạng thái và resource của **cluster**

**Master node** chỉ có nhiệm vụ **control state** của cluster, nó không có chạy ứng dụng trên đó, ứng dụng của chúng ta sẽ được chạy trên worker node. Worker node gồm 3 thành phần chính như:

- **Container runtime** (docker, rkt hoặc nền tảng khác): chạy container
- **Kubelet**: giao tiếp với API server và quản lý container trong một worker node
- **Kubernetes Service Proxy** (kube-proxy): quản lý network và traffic của các ứng dụng trong woker node
---
### Bài 02 : Kubernetes Pod
