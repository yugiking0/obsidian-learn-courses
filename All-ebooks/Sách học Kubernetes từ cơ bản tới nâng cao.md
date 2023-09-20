# Những cuốn sách học Kubernetes từ cơ bản tới nâng cao

## Giới thiệu

Kubernetes là công cụ khá phổ biến với anh em DevOps trong những năm gần đây, tuy nhiên việc học và vận dụng được nó hơi khó cho những bạn mới bắt đầu. Nên ở bài này mình muốn giới thiệu tới mọi người những cuốn sách đã giúp mình trong việc học Kubernetes từ chưa biết gì tới vận dụng được nó trong thực tế. Những cuốn sách mình giới thiệu sẽ đi từ cơ bản tới nâng cao.

## Basic level

### Kubernetes in Action

Đầu tiên là cuốn sách dành cho người chưa biết gì về Kubernetes: _Kubernetes in Action_.

![image.png](https://images.viblo.asia/c14ae7a0-c8d3-41b4-a004-96368ecdfb3e.png)

_[Kubernetes in Action, Second Edition](https://www.manning.com/books/kubernetes-in-action-second-edition)_

Đây là cuốn sách cực kì hay, dạy cho các bạn những thứ cơ bản nhất của Kubernetes. Bạn sẽ được học song song về lý thuyết và thực hành. Ví dụ bạn sẽ học được những khái niệm sau trong cuốn sách này:

- Kubernetes là gì?
- Tại sao ta lại cần nó?
- Kubernetes giúp gì cho ta trong việc quản lý và chạy container?
- Các thành phần cơ bản nhất của Kubernetes?
- Làm thế nào để sử dụng Kubernetes để xây dựng một hệ thống với tính khả dụng cao.
- Kubernetes scaling.
- Và rất nhiều khái niệm khác.

Sau khi đọc xong cuốn này bạn sẽ có một nền tảng vững chắc về Kubernetes, nếu muốn đọc tiếng việt thì các bạn xem series của mình nhé: [Kubernetes Series](https://viblo.asia/s/kubernetes-series-bq5QL8QGlD8).

### Kubernetes Best Practices - Blueprints for Building Successful Applications on Kubernetes

Sau khi đã mần xong lý thuyết thì tiếp theo các bạn cần tìm hiểu cách vận dụng Kubernetes vào các hệ thống thực tế, cuốn sách này sẽ giúp bạn: _Kubernetes Best Practices - Blueprints for Building Successful Applications on Kubernetes_.

![image.png](https://images.viblo.asia/47a9fa76-28ac-4595-8c5d-2bee20ce7ea7.png)

_[Kubernetes Best Practices](https://www.oreilly.com/library/view/kubernetes-best-practices/9781492056461)_

Cuốn sách này sẽ chỉ bạn cài rất nhiều ứng dụng bằng Kubernetes, ví dụ như:

- Cách cài Ingress Controller.
- Cách cài hệ thống monitoring bằng Prometheus.
- Cách cài hệ thống logging bằng Elasticsearch, Logstash, Kibana.
- Cách tốt nhất để quản lý ConfigMaps và Secrets.
- Cách xây dựng hệ thống CI/CD trên Kubernetes.
- ...

## Middle

Sau khi xem xong 2 cuốn trên thì chắc có thể vận dụng được Kubernetes trong thực tế rồi, nhưng nếu các bạn muốn tìm hiểu sâu hơn nữa, thì các cuốn tiếp theo sẽ giúp bạn tìm hiểu sâu hơn một chút về Kubernetes.

### Managing Kubernetes

Khi ta làm việc với Kubernetes thì thường sẽ có hai vai trò là Kubernetes Developer và Kubernetes Administrator.

Kubernetes Developer là những người sẽ viết các file manifest cho ứng dụng và triển khai nó lên trên Kubernetes. Còn Kubernetes Administrator là những người sẽ dựng Kubernetes Cluster, sau đó quản lý vận hành nó để các bạn Developer có thể dễ dàng sử dụng.

Cuốn sách này sẽ chỉ các bạn vận hành Kubernetes: _Managing Kubernetes_.

![image.png](https://images.viblo.asia/47dd3c29-0b0d-4199-bb79-7539c5b72a1b.png)

_[Managing Kubernetes](https://www.oreilly.com/library/view/managing-kubernetes/9781492033905)_

Đây là cuốn sẽ chỉ cho ta cách vận hành Kubernetes trên môi trường production, cách cài Kubernetes trên môi trường production, cách quản lý cụm Kubernetes, cách lưu trữ và khôi phục một cụm Kubernetes Cluster.

### Kubernetes Operators

Operators trong Kubernetes được xây dựng dựa trên khái niệm của _[operator pattern](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)_. Operators sẽ giúp chúng ta mở rộng các chức năng của Kubernetes, một vài ví dụ của Kubernetes Operators:

- Argo Rollout.
- Elastic Cloud on Kubernetes (ECK).
- Confluent for Kubernetes.

Với Operators, thay vì ta phải viết rất nhiều file manifest để triển khai ứng dụng, thì ta chỉ cần viết đơn giản như sau:

```yaml
apiVersion: platform.confluent.io/v1beta1
kind: Kafka
metadata:
  name: kafka
  namespace: confluent
spec:
  replicas: 3
  image:
    application: confluentinc/cp-server:7.2.0
    init: confluentinc/confluent-init-container:2.4.0
  dataVolumeCapacity: 10Gi
  metricReporter:
    enabled: true
```

Chỉ cần một file manifest đơn giản để triển khai được Kafka 😁.

Sau đây là cuốn sách hướng dẫn cho bạn thiết kế và xây dựng một Operators: _Kubernetes Operators - Automating the Container Orchestration Platform_.

![image.png](https://images.viblo.asia/dad5656b-151c-4323-a1db-01e2306286b8.png)

_[Kubernetes Operators](https://www.oreilly.com/library/view/kubernetes-operators/9781492048039/)_

## Advanced

Nếu luyện xong các cuốn trên và các bạn vẫn muốn tìm hiểu sâu hơn nữa về Kubernetes thì mình giới thiệu tiếp cho các bạn hai cuốn sách này, hai cuốn sách tiếp theo hơi thuần lý thuyết.

### GitOps and Kubernetes

**GitOps**, đây là một khái niệm khá mới đối với mình và mình đã học được nó thông qua cuốn này: _GitOps and Kubernetes_.

![image.png](https://images.viblo.asia/5baa0f7b-d1fc-43e3-b1af-2dbbf8cee920.png)

_[GitOps and Kubernetes](https://www.manning.com/books/gitops-and-kubernetes)_

Đây là cuốn sách sẽ giải thích cho các bạn về khái niệm GitOps và cách xây dựng CI/CD trong Kubernetes. Trong cuốn này các bạn sẽ học được các cách để tổ chức môi trường và xây dựng chiến lược về triển khai hệ thống với Git + Kubernetes như:

- Ta sẽ tổ chức môi trường thế nào?
- Xây dựng Pipelines ra sao?
- Các chiến lược để triển khai sản phẩm: canary, blue-green, ...
- Các vấn đề về bảo mật.
- Cách sử dụng cách công cụ GitOps như: ArgoCD, Jenkins X, Flux.
- ...

### Core Kubernetes

Cuối cùng là cuốn sách sẽ nâng tầm hiểu biết về Kubernetes của bạn sang một trang mới: _Core Kubernetes_.

![image.png](https://images.viblo.asia/357f2cf2-e2d5-4299-bbc2-0a29d8b5365f.png)

_[Core Kubernetes](https://www.manning.com/books/core-kubernetes)_

Như tên của cuốn sách, trong cuốn này nó sẽ dạy cho các bạn những thành phần _core_ của Kubernetes. Đi từ những khái niệm cơ bản về Container và những thành phần cấu tạo nên Container, cho tới Pod, hệ thống lưu trữ và network của Kubernetes, sau khi đọc xong chắc các bạn sẽ có cái nhìn rất sâu về công cụ Kubernetes, mình thì chưa đọc xong cuốn này nhưng chỉ vài chương đầu thì hiểu biết về Kubernetes của mình đã được bổ sung rất nhiều. Ví dụ đây là hình minh họa của Pod ở trong quyển sách, vẽ cả tầng Linux Namespaces.

![image.png](https://images.viblo.asia/922316fb-a2b4-44c8-9c7e-077d2fc3bf31.png)

Cuốn này rất hay. Các bạn like page [DevOps VN](https://www.facebook.com/profile.php?id=100085570585155) để nhận thông báo về bài viết sớm nhất nhé 😁.

## Kết luận

Ở trên là những cuốn sách đã giúp mình trong quá trình tìm hiểu về Kubernetes, mong rằng sẽ hữu ích với mọi người. Nếu các bạn có biết cuốn nào hay thì hãy giới thiệu cho mọi người ở phần bình luận với nhé 😁.


