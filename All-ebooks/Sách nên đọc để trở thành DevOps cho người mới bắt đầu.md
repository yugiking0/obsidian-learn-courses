# Những cuốn sách nên đọc để trở thành DevOps cho người mới bắt đầu
---
**Giới thiệu**

Trong bài này mình chỉ muốn giới thiệu tới các bạn những cuốn sách mà mình đã đọc để từ một Full-stack Developer trở thành DevOps và Cloud Engineer. Và mình cũng sẽ chia sẻ về kinh nghiệm học tập của mình, và mong có thể đem tới cho các bạn chưa biết gì một con đường học tập để trở thành DevOps Engineer.

![[Pasted image 20230909110914.png | 600]]

Những cuốn sách mà mình giới thiệu sẽ đi từ cơ bản lên nâng cao, mình sẽ nói qua những thứ mà chúng ta cần nắm để bắt đầu trên hành trình trở thành một DevOps Engineer.

## Basic

Đầu tiên, thứ căn bản nhất mà chúng ta cần phải nắm đó là Linux, không cần phải trở thành master linux (vì không ai có thể tự nhận mình là master về linux được) mà ta chỉ cần hiểu rõ về Linux là gì, Linux với Ubuntu hay Centos khác nhau cái gì, hệ thống file của Linux và những câu command line đơn giản.

Để tìm hiểu về linux cho người chưa biết gì, mình giới thiệu các bạn cuốn sách này.

![[Pasted image 20230909110932.png | 300]]

[_Linux for Beginners_](https://www.amazon.com/Linux-Beginners-Introduction-Operating-Command-ebook/dp/B00HNC1AXY)

Cuốn sách này sẽ chỉ cho các bạn những thứ cơ bản nhất về linux, khác biệt giữa linux và ubuntu, hệ thống file của linux ra sao, những câu lệnh command line nào là cần thiết, cách tạo và quản lý user trên linux.

Nếu các bạn muốn tìm hiểu sâu hơn về linux thì mình giới thiệu cuốn này.

![[Pasted image 20230909110954.png | 300]]

[_Ubuntu Linux Unleashed 2021 Edition_](https://www.amazon.com/Ubuntu-Linux-Unleashed-2021-14th/dp/0136778852)

## The first step

Sau khi ta đã tìm hiểu xong cơ bản về hệ điều hành linux, thì bước tiếp theo ta cần học là cách để chạy chương trình của ta trên các hệ điều hành khác nhau, đặc biệt là linux.

Ta cần tìm hiểu cơ bản về nodejs, java hoặc .NET, nhưng lưu ý là ta không cần phải học về cách lập trình của ngôn ngữ mà chỉ cần tìm hiểu về cách chạy, install thư viện và build code của những ngôn ngữ này.

Ví dụ đối với nodejs, ta chỉ cần tìm hiểu cách cài nodejs, cách chạy nodejs dùng pm2, cách cài các thư viện của nodejs dùng npm. Còn đối với java ta cần tìm hiểu cách java chạy, cách tải thư viện và build source code dùng maven.

Sau đó để ta có thể chạy các chương trình khác nhau dễ dàng nhất có thể thì ta phải tìm hiểu về container và docker. Để tìm hiểu cơ bản về Docker, mình giới thiệu mọi người cuốn này.

![[Pasted image 20230909111009.png | 300]]

[_Docker in Action, Second Edition_](https://www.manning.com/books/docker-in-action-second-edition)

Trong cuốn này nó sẽ chỉ cho ta những thứ cơ bản nhất về Docker và cách chạy container, cách build code thành container image, cách xài docker-compose, cách tự dựng docker registry để tự host container image của ta. Sau khi đọc xong các bạn sẽ có cái nhìn tổng quan hơn về cách dùng docker để chạy chương trình của ta trên các hệ điều hành khác nhau.

## Step on the road to become a DevOps

Sau khi học xong và hiểu cơ bản về linux và docker, bây giờ các bạn có thể tự tin để bước chân lên con đường để trở thành một DevOps Engineer. Thứ tiếp theo ta cần tìm hiểu là cách tự động delivery sản phẩm hoặc chương trình của chúng ta tới người dùng một cách dễ dàng nhất có thể. Cách để làm việc đó người ta gọi là CI/CD, để tìm hiểu đơn giản về CI/CD mình giới thiệu các bạn cuốn này.

![[Pasted image 20230909111023.png | 300]]

[_Continuous Delivery with Docker and Jenkins_](https://www.amazon.com/Continuous-Delivery-Docker-Jenkins-Delivering/dp/1787125238)

Cuốn này sẽ chỉ cho ta những thứ cần thiết để thiết lập luồng CI/CD cho chương trình của ta, tìm hiểu cơ bản về Jenkins, kiến trúc của jenkins, cách cài đặt và thiết lập jenkins, cách sử dụng jenkins với docker.

Và song song với việc học về CI/CD, ta cũng cần tìm hiểu về **Container Orchestration**. Đây là cách vận hành và quản lý hàng ngàn container trên môi trường sản phẩm thực tế mà khách hàng của ta đang sử dụng, ta sẽ tìm hiểu về kubernetes và đây là cuốn mình đã đọc.

![[Pasted image 20230909111037.png | 300]]

[_Kubernetes in Action, Second Edition_](https://www.manning.com/books/kubernetes-in-action-second-edition)

Trong cuốn này nó sẽ giải thích cho ta mọi thứ ta cần biết về kubernetes, đây là một cuốn sách cực kì hay. Ta sẽ tìm hiểu về kubernetes là gì, cách dùng nó để chạy và quản lý container, cách chạy cả trăm container một lúc, triển khai ứng dụng với thời gian downtime gần như bằng 0, các best pratice về cách dùng kubernetes để triển khai ứng dụng.

Nếu các bạn muốn đọc bản tiếng việt thì có thể đọc series của mình: [Kubernetes Series](https://viblo.asia/s/kubernetes-series-bq5QL8QGlD8). Đây là series mình tham khảo từ cuốn trên và thêm cách hiểu của mình vào đó.

Và nhớ là thực hành và thực hành càng nhiều càng tốt về CI/CD và Kubernetes.

## Middle

Nếu đọc xong những cuốn sách trên và thực hành nhiều thì bây giờ các bạn có thể tự tin nói mình là một Fresher DevOps rồi. Thứ tiếp theo ta cần học là cách vận dụng những thứ trên vào thực tế, tuy đây là việc rất khó nhưng mình cũng có hai cuốn sách sau để giới thiệu tới mọi người.

Đầu tiên là cuốn **Managing Kubernetes**.

![[Pasted image 20230909111055.png | 300]]

[_Managing Kubernetes_](https://www.oreilly.com/library/view/managing-kubernetes/9781492033905)

Đây là cuốn sẽ chỉ cho ta cách vận hành kubernetes trên môi trường production, cách cài kubernetes trên môi trường production thế nào, quản lý cụm kubernetes của ta thế nào, cách backup và restore nó ra sao.

Thứ hai là cuốn **Kubernetes Best Practices - Blueprints for Building Successful Applications on Kubernetes**.

![[Pasted image 20230909111108.png | 300]]

[_Kubernetes Best Practices_](https://www.oreilly.com/library/view/kubernetes-best-practices/9781492056461)

Đây là cuốn sách sẽ mang tới cho các bạn rất nhiều ví dụ thực tế, cách cài rất nhiều ứng dụng trên môi trường kubernetes, cách monitoring ứng dụng.

## Become a Good DevOps

Có cách nào để khiến giá trị của ta tốt hơn so với các ứng viên DevOps khác không? Theo quan điểm mình, để giá trị của ta có thể tốt hơn so với các ứng viên DevOps còn lại, ta cần phải biết về Cloud. Tương lai sẽ sân chơi của là Cloud.

Để học Cloud thì ta nên chọn các nhà cung cấp lớn nhất và nhiều người xài nhất, ở thời điểm hiện tại mình viết bài này thì Cloud nổi nhất là AWS, và mình cũng rất thích AWS.

Đế bắt đầu với Cloud thì mình giới thiệu các bạn hai cuốn sách và một khóa học trên Udemy. Đầu tiên là cuốn.

![[Pasted image 20230909111122.png | 300]]

[_Amazon Web Services in Action, Second Edition_](https://www.manning.com/books/amazon-web-services-in-action-second-edition)

Xuyên suốt cuốn này ta sẽ được tìm hiểu về AWS là gì, các dịch vụ cơ bản của AWS, cách sử dụng nó làm sao, cách thiết kế một hệ thống chịu tải cao, và cách thiết kế hệ thống dễ dàng mở rộng trên AWS.

Tiếp theo là khóa học dạy ta cách lấy chứng chỉ của AWS.

![[Pasted image 20230909111135.png | 700]]

[_Ultimate AWS Certified Solutions Architect Associate 2022_](https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c02/)

Khóa này của một giảng viên rất nổi tiếng là Stephane Maarek, trong khóa này anh sẽ dạy cho ta toàn bộ những thứ cần thiết về AWS để đi thi lấy chứng chỉ. Tuy là khóa học dạy thi chứng chỉ nhưng sau khi học xong thì ta sẽ có cái nhìn tổng quan nhất về AWS.

Và tiếp theo là cuốn về Infrastructure as Code.

![[Pasted image 20230909111157.png | 300]]

[_Terraform in Action_](https://www.manning.com/books/terraform-in-action)

Thông thường khi làm việc với AWS ta sẽ dùng một công cụ khác để hỗ trợ việc tạo hạ tầng trên AWS, và công cụ phổ biến nhất thời điểm mình viết là Terraform, trong cuốn trên nó sẽ chỉ cho ta toàn bộ những thứ cần thiết về Terraform và cách dùng nó với AWS. Hoặc nếu các bạn muốn đọc bằng tiếng Việt thì có thể xem series của mình [Terraform Series](https://viblo.asia/s/terraform-series-3m5WB8JvlO7).

## Keep Learning

Nếu các bạn có thể hoàn thành được toàn bộ những thứ trên thì chúc mừng, bạn đã trở thành một DevOps Engineer rồi đấy 😁. Nhưng con đường học tập thì không bao giờ kết thúc, để có nhiều kiến thức hơn thì ta phải học và học. Đây là những cuốn mình đang xem để nâng cao kiến thức.

Đầu tiên là một cuốn về monitoring, tất nhiên là trong quá trình vận hành của ta thì việc monitoring là không thể thiếu.

![[Pasted image 20230909111210.png | 300]]

[_Monitoring with Prometheus_](https://www.amazon.com/Monitoring-Prometheus-James-Turnbull-ebook/dp/B07DPH8MN9)

Cuốn này sẽ dạy cho ta về cách sử dụng Prometheus để monitoring hệ thống, cách xài Grafana để vẽ chart biểu diễn tình trạng của hệ thống.

Tiếp theo là về Search Engine.

![[Pasted image 20230909111224.png | 300]]

[_Elasticsearch in Action_](https://www.manning.com/books/elasticsearch-in-action)

Đây là cuốn sẽ dạy ta về Elasticsearch, tuy trong cuốn này nó dạy về Elasticsearch 5.x, nhưng từ đó ta có thể google thêm để tìm hiểu về cách hoạt động của Elasticsearch 7.x, việc này sẽ đem lại cho ta cái nhìn chi tiết hơn về nó.

Cuối cùng là cuốn về Event Streaming.

![[Pasted image 20230909111236.png | 300]]

[_Kafka: The Definitive Guide_](https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/)

Khi ta làm việc với hệ thống lớn thì Event Streaming là thứ không thể thiếu, và Kafka là một trong những công cụ mạnh nhất để làm việc này.

## Kết luận

Ở trên là những cuốn mình đã đọc và đang đọc để từ một Full-stack developer trở thành một DevOps và Cloud Engineer, mong rằng nó sẽ hữu ích với mọi người. DevOps và Cloud là một mảng rất rộng, tuy ta không bao giờ có thể tìm hiểu hết về nó nhưng cứ keep learning nhé mọi người 😁.

*Tác giả **Quân Huỳnh***