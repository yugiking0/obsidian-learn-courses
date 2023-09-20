 # Docker là gì? Tìm hiểu Docker cơ bản toàn tập
--- 
## Docker là gì?

**[Docker](https://www.docker.com/)** là một dự án mã nguồn mở giúp cung cấp cách để **building**, **deploying** và **running** ứng dụng dễ dàng hơn bằng cách sử dụng các container (trên nền tảng ảo hóa). Ban đầu Docer viết bằng **Python**, nhưng hiện tại đã chuyển sang Golang.

![[Pasted image 20230907091907.png | 500]]


## Lịch sử phát triển Docker

**Docker** được tạo ra từ ông *Solomon Hykes* khi còn đang làm việc trong một dự án nội bộ của **dotCloud** ở Pháp. Đến đầu năm 2013, Docker được phát hành dạng mã nguồn mở và sau đó đến năm 2015, Docker trở thành **top 20 dự án có số sao đánh giá cao nhất** trên **GitHub** với hơn 6,800 fork và 11,00 lập trình viên.

![[Pasted image 20230907091928.png]]
Quá trình Docker phát triển từ 2004
## Container trong Docer là gì?

Docker cho phép các lập trình viên đóng gói các ứng dụng cần thiết vào trong container, như thư viện, gói dưới dạng package. Nhờ vào container, ứng dụng sẽ chạy trên mọi máy **Linux** bất kể mọi tùy chỉnh và cài đặt khác với máy dùng để viết code.

Docker khá giống với Virtual Machine, nhưng Docker phát triển mạnh mẽ và phổ biến nhanh chóng hơn. Dưới đây là một số nguyên nhân:

- **Dễ sử dụng:** Docker rất dễ sử dụng có các developer, Admin System,… vì nó tận dụng container để build và kiểm tra nhanh chóng. Và nó có thể đóng gói các ứng dụng trên laptop của họ và chạy trên public cloud, private cloud, ...
- **Tốc độ:** Nói về tốc độ thì docker container rất nhẹ và nhanh và bạn có thể khởi tạo và chạy docker container chỉ trong vài giây.
- **Môi trường chạy:** Bạn có thể tận dụng và chia nhỏ các container riêng lẻ. Ví dụ bạn có thể chạy Database trên một container và **Redis cache** chạy trên một container khác trong khi ứng dụng Node.js lại có thể chạy trên một container khác nữa. Khi sử dụng Docker bạn rất dễ để liên kết các container với nhau để tạo thành một ứng dụng. Từ đó, làm cho nó dễ dang scale và update các thành phần độc lập với nhau.

> [!infor] Thời điểm hiện tại thì thế giới bắt đầu sử dụng thêm một công cụ quản lý container hiện đại khác là [[03-Kubernestes | Kubernestes]]

## Cách thức hoạt động của Docker
![[Pasted image 20230907094328.png ]]
Về **cách thức hoạt động của docker** thì nó hoạt động bằng cách cung cấp phương thức tiêu chuẩn để chạy mã. Như cách máy ảo – ảo hóa (loại bỏ nhu cầu quản lý trực tiếp) phần cứng của máy chủ, các container sẽ ảo hóa hệ điều hành của máy chủ. Docker được cài đặt trên từng máy chủ và cung cấp các lệnh cơ bản để bạn có thể build, khởi tạo và dừng container.

Còn để hiểu về cơ chế hoạt động của Docker khá là phức tạp. Ở đây, Vietnix sẽ tóm gọn lại cho bạn dễ hiểu về **hoạt động của Docker** thông qua một Docker engine và kết hợp với 2 yếu tố sau:

- 1 server và 1 client.
- Giao tiếp giữa server và client thông qua REST API.

Nếu bạn đang sử dụng hệ điều hành Windows/Mac cũ, bạn có thể tận dụng [Docker toolbox](https://www.docker.com/products/docker-desktop), vì nó cho phép bạn điều kiển docker engine với [Docker Compose](https://docs.docker.com/compose/) và [Kitematic](https://kitematic.com/).

![[Pasted image 20230907094647.png | 700]]

![[Pasted image 20230907095123.png]]

![[Pasted image 20230907095321.png]]

Xem thêm : [Docker Compose (hashnode.dev)](https://pavankumar07.hashnode.dev/docker-compose)
## Tại sao nên sử dụng Docker?

Docker ngày nay phổ biến đến mức **“Docker”** và **“container”** được sử dụng thay thế cho nhau. Nhưng các công nghệ liên quan đến container đầu tiên đã có sẵn trong nhiều năm, thậm chí nhiều thập kỷ qua, trước khi Docker được phát hành ra công chúng vào năm 2013. Đáng chú ý nhất là vào năm 2008, LXC ( cho LinuX Containers) được triển khai ở Linux Kernel. Nó cho phép hoàn toàn ảo hóa cho một phiên bản Linux.

Các phiên bản đầu của Docker đã làm đòn bẩy cho các sản phẩm chỉ sử dụng riêng cho LXC. Nhưng Docker đã sớm phát triển công nghệ chứa tùy chỉnh của riêng mình cho phép những điều sau:

### Cải tiến cùng với sự liền mạch

Trong khi container LXC thường tham chiếu đến các cấu hình máy cụ thể, thì container Docker chạy mà không cần phải cải biến trên bất kỳ máy tính để bàn, trung tâm dữ liệu và môi trường đám mây nào.

### Trọng lượng nhẹ hơn và cập nhật chi tiết hơn

Với LXC, nhiều quy trình có thể được kết hợp trong một container duy nhất. Với container Docker, chỉ một tiến trình mới có thể chạy trong mỗi container. Điều này giúp bạn có thể xây dựng một ứng dụng có thể tiếp tục chạy trong khi một trong các phần của nó bị gỡ xuống để cập nhật hoặc sửa chữa.

### Lập phiên bản container

Docker có thể theo dõi các phiên bản của image container, quay trở lại các phiên bản trước và theo dõi ai đã tạo một phiên bản và cách thức tạo ra nó. Nó thậm chí còn có thể chỉ tải lên các delta giữa phiên bản hiện có và phiên bản mới.

### Thư viện container được chia sẻ

Các nhà phát triển có thể truy cập sổ đăng ký mã nguồn mở chứa hàng nghìn container do người dùng đóng góp.

Vì những lý do này, việc áp dụng Docker nhanh chóng bùng nổ và tiếp tục tăng. Tại thời điểm này, Docker Inc. báo cáo đã có 105 tỷ lượt tải xuống container, tăng từ 50 tỷ chỉ một năm trước và hơn 750 đối tác khách hàng của doanh nghiệp Docker.

## Tìm hiểu các khái niệm về Docker cơ bản

Như vậy là bạn được **Docker là gì** và lý do tại sao cần sử dụng Docker. Tuy nhiên để không gặp khó khăn khi bắt đầu sử dụng Docker bạn sẽ cần nắm rõ các công cụ và thuật ngữ ký thuật của nó.

![[Pasted image 20230907095507.png | 700]]

Tìm hiểu các khái niệm về Docker cơ bản

Một số công cụ và thuật ngữ công nghệ bạn sẽ gặp phải khi sử dụng Docker bao gồm:

### DockerFile

Mọi container Docker bắt đầu bằng một file văn bản đơn giản chứa hướng dẫn về cách tạo image container Docker. **DockerFile** tự động hóa tiến trình tạo image Docker. Về cơ bản, đây là danh sách các lệnh mà Docker Engine sẽ chạy để tập hợp image.

### Docker images

**Docker image** chứa mã nguồn ứng dụng thực thi cũng như tất cả các công cụ, thư viện. Kèm theo dependencies mà ứng dụng cần để chạy dưới dạng container. Khi bạn chạy Docker image, nó sẽ trở thành một phiên bản (hoặc nhiều phiên bản) của container.

![[Pasted image 20230907095526.png | 500]]

Có thể xây dựng Docker image từ đầu, nhưng hầu hết các nhà phát triển kéo chúng xuống từ các kho lưu trữ chung. Nhiều Docker image có thể được tạo từ một base image duy nhất. Docker image được tạo thành từ các lớp và mỗi lớp tương ứng với một phiên bản của image.

Bất cứ khi nào nhà phát triển thay đổi image, một lớp trên cùng mới sẽ được tạo. Lúc này, lớp trên cùng này thay thế lớp trên cùng trước làm phiên bản hiện tại của image. Các lớp trước đó được lưu để khôi phục hoặc được sử dụng lại trong các dự án khác.

Mỗi khi một container được tạo từ Docker image, một lớp mới khác được gọi là lớp container được tạo. Các thay đổi được thực hiện đối với container. Chẳng hạn như nó có thể thêm hoặc xóa file chỉ được lưu vào lớp container và chỉ tồn tại khi container đang chạy.

Quá trình tạo image lặp đi lặp lại này giúp tăng hiệu quả tổng thể. Bởi nhiều phiên bản container có thể chạy chỉ từ một base image duy nhất. Do đó, khi chúng làm như vậy, chúng sẽ tận dụng một ngăn xếp chung.

### Docker containers

**Docker container** là các phiên bản live, running instance của Docker image. Ta thấy Docker image là file chỉ đọc còn container là phiên bản live, executable và người dùng có thể tương tác với chúng. Cùng với đó, quản trị viên có thể điều chỉnh cài đặt và các quy định của họ.

### Docker Hub

**Docker Hub** là kho lưu trữ công khai Docker image. Nó tự gọi mình là “thư viện và cộng đồng lớn nhất thế giới về image container”. Nó chứa hơn 100.000 image container và chúng được lấy từ các nhà cung cấp phần mềm thương mại, các dự án mã nguồn mở, các nhà phát triển cá nhân. Nó bao gồm các image được sản xuất bởi Docker, Inc. Cùng với đó là các image được chứng nhận thuộc Cơ quan đăng ký tin cậy Docker và hàng nghìn image khác.

Tất cả người dùng Docker Hub có thể chia sẻ image của họ theo ý muốn. Họ cũng có thể tải xuống các image cơ sở được xác định trước để sử dụng làm điểm bắt đầu cho bất kỳ dự án container nào.

### Docker Client

Đây là thành phần mà bạn có thể tương tác với Docker thông qua command line. Docker client sẽ gửi lệnh tới Docker Deamon thông qua REST API như đã đề cập ở trên.

### Một số Docker khác

- **Docker Engine:** Đây là thành phần chính của Docker như một công cụ để đóng gói ứng dụng.
- **Docker Deamon:** Dùng để lắng nghe các request từ Docker Client để quản lý các đối tượng như container, image, network và volume thông qua REST API.
- **Docker Volumes:** Là phần dữ liệu được tạo ra khi container được khởi tạo.
- **Docker Machine:** Tạo ra các docker engine trên máy chủ.
- **Docker Compose:** Chạy ứng dụng bằng cách định nghĩa cấu hình các Docker Container thông qua file cấu hình.

## Quy trình thực thi một hệ thống sử dụng Docker

Quy trình để thực thi Docker gồm 3 bước sau:

![[Pasted image 20230907095541.png | 700]]

3 bước thực thi Docker

- **Build**: Bước đầu tiên, bạn cần tạo một dockerfile, trong dockerfile này chính là code của mình. Dockerfile này sẽ được build ở một máy tính có cài đặt Docker Engine. Khi build xong, thì chúng ta sẽ có container và trong container sẽ chứa ứng dụng kèm bộ thư viện.
- **Push**: Bạn thực hiện push Container lên cloud và lưu lại sau khi có được container.
- **Pull & Run**: Nếu máy tính khác của bạn muốn sử dụng container thì máy của bạn phải thực hiện pull container này về máy đó. Và máy đó phải cài đặt trước Docker Engine. Tiếp theo, bạn mới thực hiện Run Container này.

## Khi nào thì nên sử dụng Docker

Trong những trường hợp sau đây bạn có thể sử dụng Docker hiệu quả:

- Triển khai kiến trúc Microservice.
- Sản phẩm công ty cần một cách tiếp cận mới về xây dựng, đẩy lên server và thực thi ứng dụng một cách nhanh chóng.
- Khi build ứng dụng cần scale một cách linh hoạt.
- Config máy local và server trên cùng một môi trường nhanh chóng.

## Hướng dẫn cài đặt Docker
[[Cài đặt Docker]]
## Hướng dẫn sử dụng Docker cơ bản toàn tập
[[Sử dụng Docker cơ bản toàn tập]]

## Lời kết

**Docker là gì?** Khi đọc bài viết này bạn cũng nắm được khái niệm và cách thức vận hàng của docker container. Cùng với đó là một số lệnh cơ bản có thể hỗ trợ bạn trong quá trình sử dụng docker một cách hiệu quả. Chúc các bạn thành công.