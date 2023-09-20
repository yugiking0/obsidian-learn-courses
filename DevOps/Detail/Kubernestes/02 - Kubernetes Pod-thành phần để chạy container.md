# Kubernetes Series - Bài 2 - Kubernetes Pod: thành phần để chạy container

## Giới thiệu

Chào các bạn tới với series về kubernetes. Đây là bài thứ hai trong series của mình, trong bài này mình sẽ nói về **Kubernetes Pod**. Để thực hành được bài này thì yêu cầu các bạn đã có cài môi trường docker, kubernetes local và có kiến thức cơ bản về docker, nếu chưa cài các bạn có thể cài [Cài đặt Minikube](https://kubernetes.io/vi/docs/tasks/tools/install-minikube/). 

[Overview of Different Container Runtimes (cto.ai)](https://cto.ai/blog/overview-of-different-container-runtimes/)
## Kubernetes Pod là gì?

**Pod** là thành phần cơ bản nhất để deploy và chạy một ứng dụng, được tạo và quản lý bởi kubernetes. Pod được dùng để nhóm (group) và chạy một hoặc nhiều container lại với nhau trên cùng một **worker node**, những container trong một pod sẽ chia sẻ chung tài nguyên với nhau. **Thông thường chỉ nên run Pod với 1 container** (mình sẽ giải thích về việc *khi nào nên chạy một pod một container và một pod nhiều container* ở bài khác)

![[Pasted image 20230907161325.png]]

**Vậy tại sao là lại dùng Pod để chạy container, sao không chạy container trực tiếp?** Kubernetes Pod như một wrapper của container, cung cấp cho chúng ta thêm nhiều chức năng để quản lý và chạy một container, giúp container của ta chạy tốt hơn là chạy container trực tiếp, như là group tài nguyên của container, check container healthy và restart, chắc chắn ứng dụng trong container đã chạy thì mới gửi request tới container đó, cung cấp một số lifecycle để ta có thể thêm hành động vào Pod khi Pod chạy hoặc shutdown, v...v... Và kubernetes sẽ quản lý Pod thay vì quản lý container trực tiếp

![[Pasted image 20230907161406.png]]

## Chạy ứng dụng đầu tiên bằng Pod

Bây giờ ta bắt tay vào thực hành bài đầu tiên nào . 

Đầu tiên ta tạo một folder và tạo một file index.js, copy đoạn code sau vào:

```js
const http = require("http");

const server = http.createServer((req, res) => {
  res.end("Hello kube\n")
});

server.listen(3000, () => {
  console.log("Server listen on port 3000")
})
```

Tạo file Dockerfile và copy đoạn code sau vào:

```none
FROM node:12-alpine
WORKDIR /app
COPY index.js .
ENTRYPOINT [ "node", "index" ]
```

Run câu lệnh build image:

`docker build . -t 080196/hello-kube`

Test thử container có chạy đúng hay không, chạy container bằng câu lệnh:

`docker run -d --name hello-kube -p 3000:3000 080196/hello-kube`

Gửi request tới container:

![[Pasted image 20230907162755.png]]

Nếu in ra được chữ hello kube là container của chúng ta đã chạy được. Xóa container đi nhé

`docker rm -f hello-kube`

Bây giờ chúng ta sẽ dùng Pod để chạy container, các bạn có thể sử dụng image **080196/hello-kube** của mình hoặc tạo image của riêng các bạn theo hướng dẫn [Create Docker Images for Docker Hub](https://www.pluralsight.com/guides/create-docker-images-docker-hub) - **Create Docker Images for Docker Hub**

Tạo một file tên là **hello-kube.yaml** và copy config sau vào:

```yaml
apiVersion: v1 # Descriptor conforms to version v1 of Kubernetes API
kind: Pod # Select Pod resource
metadata:
  name: hello-kube # The name of the pod
spec:
  containers:
    - image: 080196/hello-kube # Image to create the container
      name: hello-kube # The name of the container
      ports:
        - containerPort: 3000 # The port the app is listening on 
          protocol: TCP
```

> Thường thì ta sẽ không chạy Pod trực tiếp như thế này, mà sẽ sử dụng các resource khác của kube để chạy Pod, mình sẽ nói ở các bài viết sau

Dùng kubectl CLI (nếu bạn đã cài kubernetes local thì kubectl CLI sẽ có sẵn) để chạy file config của Pod

`kubectl apply -f hello-kube.yaml`

![[Pasted image 20230907162815.png]]

Kiểm tra pod đã chạy hay chưa

`kubectl get pod`

![[Pasted image 20230907162827.png]]

Nếu cột status hiện Running là Pod của bạn đã được chạy thành công, status ContainerCreating là Pod đang được tạo. Tiếp theo chúng ta sẽ test pod xem nó chạy đúng hay không. Trước hết để test Pod, ta phải **expose traffic** của Pod để nó có thể nhận request trước, vì hiện tại Pod của chúng ta đang chạy trong **local cluster** và không có **expose port** ra ngoài

![[Pasted image 20230907162848.png]]Có 2 cách để expose port của pod ra ngoài, dùng Service resource (mình sẽ nói về Service ở bài sau) hoặc dùng kubectl port-forward. Ở bài này chúng ta sẽ dùng port-forward, chạy câu lệnh sau để expose port của pod

`kubectl port-forward pod/hello-kube 3000:3000`

![[Pasted image 20230907162904.png]]

![[Pasted image 20230907162917.png]]

Test gửi request tới pod

![[Pasted image 20230907162929.png]]

Nếu in ra được chữ hello kube thì pod của chúng ta đã chạy đúng. Sau khi chạy xong để clear resource thì chúng ta xóa pod bằng câu lệnh

`kubectl delete pod hello-kube`

## Tổ chức pod bằng cách sử dụng labels

Dùng label là cách để chúng ta có thể phân chia các pod khác nhau tùy thuộc vào dự án hoặc môi trường. Ví dụ công ty của chúng ta có 3 môi trường là testing, staging, production, nếu chạy pod mà không có đánh label thì chúng ta rất khó để biết pod nào thuộc môi trường nào

![[Pasted image 20230907162956.png]]

![[Pasted image 20230907163005.png]]

Labels là một thuộc tính cặp key-value mà chúng ta gán vào resource ở phần metadata, ta có thể đặt tên key và value với tên bất kì. Ví dụ:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: hello-kube-testing
  labels:
    enviroment: testing # label with key is enviroment and value is testing
    project: kubernetes-series
spec:
  containers:
    - image: 080196/hello-kube
      name: hello-kube
      ports:
        - containerPort: 3000
          protocol: TCP

---
apiVersion: v1
kind: Pod
metadata:
  name: hello-kube-staging
  labels:
    enviroment: staging # label with key is enviroment and value is staging
    project: kubernetes-series
spec:
  containers:
    - image: 080196/hello-kube
      name: hello-kube
      ports:
        - containerPort: 3000
          protocol: TCP

---
apiVersion: v1
kind: Pod
metadata:
  name: hello-kube-production
  labels:
    enviroment: production # label with key is enviroment and value is production
    project: kubernetes-series
spec:
  containers:
    - image: 080196/hello-kube
      name: hello-kube
      ports:
        - containerPort: 3000
          protocol: TCP
```

`kubectl apply -f hello-kube.yaml`

Ta có thể list pod với labels như sau

`kubectl get pod --show-labels`

![[Pasted image 20230907163032.png]]

Ta có thể chọn chính xác cột label hiển thị với -L options

`kubectl get pod -L enviroment`

![[Pasted image 20230907163046.png]]

Và ta có thể lọc pod theo label với -l options

`kubectl get pod -l enviroment=production`

![[Pasted image 20230907163103.png]]

Label là một cách rất hay để chúng ta có thể tổ chức pod theo chúng ta muốn và dễ dàng quản lý pod giữa các môi trường và dự án khác nhau. Để clear resource thì chúng ta xóa pod đi nhé

`kubectl delete -f hello-kube.yaml`

![[Pasted image 20230907163113.png]]

## Phân chia tài nguyên của kubernetes cluster bằng cách sử dụng namespace

Tới phần này ta đã biết cách chạy pod và dùng labels để tổ chức pod, nhưng ta chưa có phân chia tài nguyên giữa các môi trường và dự án khác nhau. Ví dụ trong một dự án thì ta muốn tài nguyên của production phải nhiều hơn của testing, thì ta làm thế nào? Chúng ta sẽ dùng **namespace**

Namespace là cách để ta chia tài nguyên của cluster, và nhóm tất cả những resource liên quan lại với nhau, bạn có thể hiểu namespace như là một sub-cluster. Đầu tiên chúng ta list ra toàn bộ namespace

`kubectl get ns`

Ta sẽ thấy có vài namespace đã được tại bởi kube, trong đó có namespace tên là default, kube-system. Namespace default là namespace chúng ta đang làm việc với nó, khi ta sử dụng câu lệnh kubectl get để hiển thị resource, nó sẽ hiểu ngầm ở bên dưới là ta muốn lấy resource của namespace mặc định. Ta có thể chỉ định resource của namespace chúng ta muốn bằng cách thêm option --namespace vào

`kubectl get pod --namespace kube-system`

![[Pasted image 20230907163129.png]]

Bây giờ ta sẽ thử tạo một namespace và tạo pod trong namespace đó. Cách tổ chức namespace tốt là tạo theo **`<project_name>:<enviroment>`**. Ví dụ: mapp-testing, mapp-staging, mapp-production, kala-testing, kala-production. Ở đây làm nhanh thì mình sẽ không đặt namespace theo cách trên

`kubectl create ns testing`

Sửa lại file hello-kube.yaml

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: hello-kube-testing
  namespace: testing # namespace name
spec:
  containers:
    - image: 080196/hello-kube
      name: hello-kube
      ports:
        - containerPort: 3000
          protocol: TCP
```

Tạo pod

![[Pasted image 20230907163223.png]]

Bây giờ nếu ta list pod mà không chỉ định namespace testing, ta sẽ không thấy pod nào cả

![[Pasted image 20230907163234.png]]

Để list pod, ta phải chỉ định thêm namespace chúng ta muốn lấy

`kubectl get pod -n testing`

![[Pasted image 20230907163246.png]]

Vậy là ta đã tạo pod trong namespace testing thành công, xóa pod đi nhé, khi xóa thì ta cũng cần chỉ định namespace chứa resource của chúng ta

`kubectl delete pod hello-kube-testing -n testing`

![[Pasted image 20230907163306.png]]

Bạn cũng có thể xóa namespace bằng cách dùng câu lệnh delete, **chú ý là khi xóa namespace thì toàn bộ resource trong đó cũng sẽ bị xóa theo**

`kubectl delete ns testing`

![[Pasted image 20230907163324.png]]

Sử dụng namespace ta có thể tổ chức, quản lý việc phân chia tài nguyên giữa các môi trường và dự án khác nhau dễ dàng hơn.

## Kết luận

Vậy là ta đã thành công chạy ứng dụng đâu tiên trên kubernetes bằng cách sử dụng Pod. Pod là thành phần đơn giản nhất và là một thành phần chính của kubernetes để chạy container, những thành phần khác của kubernetes chỉ đóng vai trò hỗ trợ để chạy Pod, giúp pod chạy ngon hơn trong việc deploy. Cảm ơn các bạn đã đọc bài của mình. Nếu có thắc mắc hoặc cần giải thích rõ thêm chỗ nào thì các bạn có thể hỏi dưới phần comment. Hẹn gặp lại các bạn ở bài tiếp theo mình sẽ nói về **Kubernetes ReplicationController, ReplicaSet hoặc Kubernetes Services**.