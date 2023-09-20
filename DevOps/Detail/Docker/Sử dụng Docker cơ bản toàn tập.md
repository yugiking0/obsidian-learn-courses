## Hướng dẫn sử dụng Docker cơ bản toàn tập

![[Pasted image 20230907100015.png]]

### Docker Container

Docker container là một instance của image. Một container chỉ cần kết hợp với các thư viện và thiết lập cần thiết để làm cho ứng dụng hoạt động. Nó là một môi trường đóng gói gọn nhẹ và di động cho một ứng dụng.

#### Cách chạy một docker container

Sử dụng lệnh **docker** để khởi chạy docker container trên hệ thống của bạn. Ví dụ lệnh bên dưới sẽ tạo một Docker Container từ image có tên **“hello-world”**.


```bash
docker run hello-world
```

Bây giờ tạo một **instance docker** chạy hệ điều hành CentOS. Tùy chọn **-it** sẽ cung cấp một phiên tương tác với pseudo-TTY. Nó cung cấp cho bạn shell của container ngay lập tức.


```bash
docker run -it centos
```

#### Liệt kê danh sách docker container

Dùng lệnh **docker ps** để liệt kê các container đang chạy trên hệ thống hiện tại. Nó sẽ không liệt kê các container bị dừng. Nó sẽ hiển thị Container ID, name và các thông tin hữu ích khác về container.


```bash
docker ps
```

Dùng tùy chọn **-a** với lệnh ở trên để liệt kê tất cả các container bao gồm cả container bị dừng.


```bash
docker ps -a
```

#### Tìm kiếm tất cả thông tin chi tiết về container


```bash
docker inspect cc5d74cf8250

Trong đó: cc5d74cf8250 là id container
```

#### Xóa Docker container

Dùng lệnh **docker rm** để xóa docker container đang tồn tại. Bạn cần cung cấp docker container id hoặc container name để xóa một container cụ thể.


```bash
docker stop cc5d74cf8250
docker rm cc5d74cf8250
```

### Docker image

Image là tệp tin không thay đổi, giống như file iso được sử dụng để cài hệ điều hành, về cơ bản nó là bản snapshot của container. Image có thể được tạo với các lệnh có sẵn, được sử dụng để tạo container khi bắt đầu bằng lệnh run.

#### Liệt kê danh sách các images

Dùng lệnh **docker images** để liệt kê tất cả images có sẵn trên máy tính chạy docker của bạn.


```bash
docker images
```

#### Tìm kiếm docker images

Dùng lệnh docker search để tìm kiếm các images trên docker hub. Ví dụ, dùng lệnh sau để tìm docker images centOS.


```bash
docker search centos
```

#### Download docker image

Bạn dùng lệnh **docker pull** để download bất kỳ image từ docker hub. Ví dụ để download image centOS phiên bản mới nhất từ docker hub về máy local và tạo container.


```bash
docker pull centos
```

#### Xóa docker image

Ta dùng lệnh **docker rmi** để xóa bất kỳ docker image từ hệ thống local. Ví dụ, để xóa image tên centos dùng lệnh sau:


```bash
docker rmi centos
```

### Dockerfile

Dockerfile là một file được dùng để build một image bằng cách đọc các chỉ dẫn từ file đó. Tên file mặc định được dùng là **Dockerfile**. Bạn có thể tạo dockerfile trong thư mục hiện tại với các chỉ dẫn cụ thể và build một image tùy chỉnh theo yêu cầu của bạn.

#### Cách build image với Dockerfile

Dockerfile là một file được đặt ở vị trí gốc trong container khi build xong. Bạn có thể dùng lệnh sau đây để build docker image. Trong câu lệnh bên dưới, docker sẽ đọc Dockerfile tại vị trí thư mục hiện tại.

```bash
docker build -t image_name .
```

Bạn cũng có thể dùng cờ **-f** với lệnh docker build để trỏ đến Dockerfile tại bất kỳ nơi nào trong hệ thống file của bạn.


```bash
docker build  -t image_name -f /path/to/Dockerfile .
```

#### Tạo Dockerfile

Trong bài hướng dẫn này, Vietnix đã tạo một project ví dụ trên github. Các bạn chỉ cần clone repository bằng cách dùng lệnh sau:

```bash
git clone https://github.com/vietnix/Docker.git
cd Docker
```

Bây giờ build docker image với tên Vietnix

```bash
docker build -t vietnix .
```

Sau khi build, bạn có thể thấy image bằng cách dùng lệnh “docker images”

#### Khởi chạy container với image

Bây giờ mình sẽ tạo instance sử dụng image mới tạo.


```bash
docker run -it -p 8080:80 vietnix
```

Lệnh bên trên khởi chạy docker container sử dụng Vietnix.

### Có gì bên trong Dockerfile

Trong Dockerfile, có một số điểm mà các bạn cần phải biết với những chỉ thị như sau

#### FROM

FROM được dùng để thiết lập image cơ sở cho chỉ dẫn tiếp theo. Dockerfile phải có chỉ thị FROM với tên image hợp lệ là chỉ thị đầu tiên.


```bash
FROM ubuntu
```

```bash
FROM tecadmin/ubuntu-ssh:16.04
```

#### LABEL

Sử dụng label, bạn có thể tổ chức các image đúng cách. Nó cực kỳ hữu ích để thiết lập địa chỉ nhà phát triển, tên nhà cung cấp, phiên bản image, ngày phát hành,… Dòng này phải bắt đầu bằng từ khóa LABEL

```bash
LABEL maintainer="seovietnix@gmail.com"
LABEL vendor="Vietnix"
LABEL com.example.version="1.1.1"
```

Bạn có thể thêm nhiều label vào một dòng với dấu cách, hoặc định nghĩa nhiều dòng như sau:

```bash
LABEL maintainer="seovietnix@gmail.com" vendor="Vietnix" \
      com.example.version="1.1.1"
```

#### RUN

Dùng chỉ thị RUN, bạn có thể chạy bất kỳ lệnh nào tới image trong thời gian build. Ví dụ, bạn có thể cài đặt các package bắt buộc trong thời gian build.


```bash
RUN apt-get update 
RUN apt-get install -y apache2 automake build-essential curl
```

Hoặc sử dụng chạy một chỉ thị RUN như sau:


```bash
RUN apt-get update && apt-get install -y \
    automake \
    build-essential \
    curl \
```

#### COPY

Chỉ thị COPY được dùng để copy file và thư mục từ hệ thống host tới image trong khi build. Ví dụ, lệnh đầu tiên sẽ copy tất cả file từ thư mục host html/ tới thư mục **/var/www/html** trên image. Lệnh thứ hai sẽ copy tất cả file với phần mở rộng .conf tới địa chỉ thư mục **/etc/apache2/sites-available/** .

```bash
COPY html/* /var/www/html/
COPY *.conf /etc/apache2/sites-available/
```

#### WORKDIR

Chỉ thị WORKDIR được dùng để thiết lập thư mục làm việc hiện tại cho bất kỳ chỉ thị RUN, CMD, ENTRYPOINT, COPY… trong quá trình build.

```bash
WORKDIR /opt
```

#### CMD

Chỉ thị CMD được dùng để chạy các dịch vụ hoặc phần mềm có chứa bên trong image, cùng với bất kỳ tham số khác trong khi khởi chạy container. CMD dùng cú pháp đơn giản sau đây:


```bash
CMD ["executable","param1","param2"]
CMD ["executable","param1","param2"]
```

Ví dụ, để khởi động dịch vụ Apache khi khởi chạy container, dùng lệnh sau đây:


```bash
CMD ["apachectl", "-D", "FOREGROUND"]
```

#### EXPOSE

Chỉ thị EXPOSE chỉ ra các port mà container sẽ lắng nghe cho các kết nối. Sau đó bạn có thể liên kết các port hệ thống với container và dùng chúng.


```bash
EXPOSE 80
EXPOSE 443
```

#### ENV

Chỉ thị ENV được dùng để thiết lập biến môi trường cho các dịch vụ cụ thể của container.


```bash
ENV PATH=$PATH:/usr/local/pgsql/bin/ \
    PG_MAJOR=9.6.0
```

#### VOLUME

Chỉ thị VOLUME tạo một **mount point** với tên được chỉ định và đánh dấu nó là nơi giữ mount volume từ host bên ngoài hoặc container khác.

```bash
VOLUME ["/data"]
```

### Docker – quản lý ports

Docker containers chạy các dịch vụ bên trong nó trên các port được chỉ định cụ thể. Để truy cập dịch vụ của một container đang chạy trên một port, bạn cần liên kết container port với port trên Docker host (máy thật).

#### Ví dụ 1:

Nhìn vào hình bên dưới, bạn sẽ thấy docker host đang chạy hai containers, một cái chạy Apache và cái còn lại chạy MySQL.

Bây giờ, bạn cần truy cập vào website đang chạy Apache container trên port 80. Chúng ta sẽ liên kết docker port 8080 tới container port 80. Bạn cũng có thể dùng port 80 trên docker port.

Container thứ hai chạy MySQL trên port 3306. Có nhiều cách khác để truy cập MySQL từ docker host. Nhưng trong bài viết này, mình sẽ liên kết docker port 6603 tới container port 3306. Bây giờ, mình sẽ truy cập trực tiếp MySQL từ Docker container bằng cách kết nối docker host trên port 6603.

Câu lệnh bên dưới sẽ liên kết host docker port với container port.

```bash
$ docker run -it -p 8080:80 apache_image
$ docker run -it -p 6603:3066 mysql_image
```

#### Ví dụ 2:

Trong ví dụ thứ hai dùng project có sẵn của mình trên github. Nó sẽ show cho bạn ví dụ đang chạy trên port 8080 trên docker host. Đơn giản bạn chỉ cần clone repository bằng cách chạy câu lệnh sau:

```bash
$ git clone https://github.com/tecrahul/dockerfile
$ cd dockerfile
```

Bây giờ, build docker image với tên apacheimage


```bash
docker build -t apacheimage .
```

Chạy container bằng cách sử dụng lệnh **docker run**. Dịch vụ apache sẽ khởi động trên container port 80. Bạn cần chỉ ra port cụ thể bằng cách dùng option -p 8080:80 để liên kết host system port 8080 với container port 80.

```bash
docker run -it -p 8080:80 apacheimage
```

Bây giờ truy cập địa chỉ IP docker host với port 8080 trên trình duyệt web. Bạn sẽ xem được trang web đang chạy trên Apache của container như bên dưới. Địa chỉ IP của docker host của mình là 192.168.1.237.

#### Thêm một ví dụ nữa:

Bạn có thể liên kết nhiều ports với một container, nhưng cần đảm bảo bạn đã sử dụng chỉ dẫn EXPOSE tất cả các ports trong Dockerfile trước khi build image.

```bash
docker run -it -p 8080:80,8081:443 image_name
```

Nếu bạn cần liên kết port với interface của docker host cụ thể, khai báo địa chỉ IP như bên dưới. Trong ví dụ bên dưới, port 8080, 8081 sẽ có thể truy cập với địa chỉ 127.0.0.1

```bash
$ docker run -it -p 127.0.0.1:8080:80,127.0.0.1:8081:443 image_name
$ docker run -it -p 192.168.1.111:8080:80,92.168.1.111:8081:443 image_name
```

### Networking

Docker cung cấp một tùy chọn để tạo và quản lý network riêng giữa các container. Dùng lệnh **docker network** để quản lý Docker networking.

Cú pháp


```bash
docker network [options]
```

Dùng cách lệnh theo hướng dẫn bên dưới để tạo, liệt kê và quản lý Docker networking.

#### Liệt kê Docker networks

Dùng tùy chọn **ls** với lệnh docker network để liệt kê các network khả dụng trên system host.


```bash
docker network ls
```

#### Tạo docker network

Docker cung cấp nhiều loại network. Lệnh bên dưới sẽ tạo bridge network trên hệ thống của bạn.

Cú pháp


```bash
docker network create -d [network_type] [network_name]
```

#### Ví dụ


```bash
docker network create -d bridge my-bridge-network
```

#### Kết nối container với network

Bạn có thể kết nối bất kỳ container nào tới một docker network đang tồn tại bằng cách sử dụng tên container hoặc ID. Một khi container được kết nối tới network, nó có thể giao tiếp với các container khác trong cùng mạng.

Cú pháp


```bash
docker network connect [network_name] [container_name]
```

Ví dụ


```bash
docker network connect my-bridge-network centos
```

#### Ngắt kết nối docker khỏi network

Bạn có thể ngắt kết nối một container khỏi một network cụ thể bất cứ khi nào bằng cách dùng lệnh dưới đây

Cú pháp


```bash
docker network disconnect [network_name] [container_name]
```

Ví dụ

```bash
docker network disconnect my-bridge-network centos
```

#### Kiểm tra Docker network

Dùng tùy chọn **inspect** để kiểm tra với lệnh docker network để xem chi tiết docker network


```bash
docker network inspect my-bridge-network
```

Bạn sẽ nhận được kết quả như sau

#### Xóa Docker network

Dùng tùy chọn **rm** để xóa bất kỳ Docker network nào đang không sử dụng. Bạn có thể chỉ định một hoặc nhiều network hơn bằng cách sử dụng dấu cách (space) để xóa.

Ví dụ


```bash
docker network rm my-bridge-network network2 network3
```

Bạn cũng có thể xóa tất cả network không sử dụng khỏi system host bằng cách sử dụng tùy chọn prune.


```bash
docker network prune
```

### Ví dụ Docker network

Giờ chúng ta sẽ học cách truy cập MySQL server đang sử dụng phpAdmin chạy trên container khác.

#### 1. Tạo network

Đầu tiên, tạo một docker network. Dùng lệnh bên dưới để tạo bridge network mới với tên my_bridge_network

```bash
 docker network create -d bridge my-bridge-network
```

#### 2. Chạy MySQL container

Bây giờ, chạy Mysql container mới. Thiết lập mặc định user password root với biến **MYSQL_ROOT_PASSWORD**  giống như lệnh bên dưới.


```bash
docker run --name mysql -e MYSQL_ROOT_PASSWORD=secret -d mysql/mysql-server
```

Sau khi tạo container thì thêm nó vào network


```bash
docker network connect my-bridge-network mysql
```

Giờ chúng ta sẽ xem địa chỉ IP của MySQL container.


```bash
docker inspect mysql | grep "IPAddress"
```

#### 3. Chạy PHPMyadmin container

Giờ ta sẽ chạy Docker container chứa MySQL bằng cách sử dụng câu lệnh sau. Thay đổi giá trị PMA_HOST với địa chỉ IP của MySQL container trong bước trước.

```bash
 docker run --name phpmyadmin -d -e PMA_HOST=172.21.0.2 -p 8080:80 phpmyadmin/phpmyadmin
```

Thêm container này vào network

```bash
docker network inspect my-bridge-network
```

#### 4. Kiểm tra network

Ở trên mình đã thêm 2 container vào network. Bây giờ sẽ kiểm tra cài đặt network hiện tại.


```bash
docker network inspect my-bridge-network
```

Bạn sẽ nhận được kết quả như bên dưới

#### 5. Cho phép MySQL kết nối đến PHPmyadmin host

Mặc định thì MySQL không cho phép host từ xa kết nối đến. Và để cho phép phpmyadmin kết nối MySQL, truy cập shell MySQL container dùng lệnh bên dưới.


```bash
docker exec -it mysql bash
```

Đăng nhập vào MySQL server dùng password đã cung cấp trong quá trình tạo instance.


```bash
bash-4.2# mysql -u root -p
```

Tạo user mới với địa chỉ ip phpmyadmin. Trong trường hợp địa chỉ ip phpmyadmin là ‘127.21.0.3’ như bên trên.


```bash
mysql> GRANT ALL on *.* to 'dbuser'@'172.21.0.3' identified by 'secret';
Query OK, 0 rows affected, 1 warning (0.00 sec)
 
mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)
 
mysql> exit
Bye
```

#### 6. Truy cập MySQL với PHPmyadmin

Cuối cùng, kết nối docker host trên port 8080 để truy cập giao diện web phpmyadmin

Dùng thông tin đăng nhập MySQL đã tạo ở các bước bên trên để đăng nhập vào phpmyadmin

### Docker compose

Docker compose là một công cụ khác cho docker để thiết lập môi trường multi-container. Sử dụng để tạo một file compose định nghĩa tất cả container với môi trường đó. Bạn có thể dùng một lệnh dễ dàng để build image và chạy tất cả container.

Quá trình gồm ba bước để làm việc với Docker compose

- Định nghĩa môi trường ứng dụng với Dockerfile cho tất cả các dịch vụ
- Tạo file docker-compose-yml định nghĩa tất cả các dịch vụ bên dưới ứng dụng
- Chạy lệnh docker-compose up để chạy tất cả các dịch vụ bên dưới ứng dụng.

#### Cài đặt Docker compose

Truy cập trang web chính thức của Docker compose trên github và download phiên bản mới nhất của công cụ Docker compose. Bạn cũng có thể cài đặt Docker compose 1.16.1 bằng cách dùng lệnh bên dưới. Trước khi cài đặt phiên bản cụ thể, bạn phải kiểm tra khả năng tương thích trên trang phát hành với phiên bản docker của bạn.


```bash
$ curl -L https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
$ chmod +x /usr/local/bin/docker-compose
```

#### Ví dụ file Docker compose

File docker-compose.yml được yêu cầu khi bạn muốn sử dụng docker compose. Bên dưới là file cấu hình ví dụ của docker-compose version 3. File này chỉ có một dịch vụ được thêm vào và đặt tên là web.

```bash
version: '3'
services:
  db:
     image: mysql
     container_name: mysql_db
     restart: always
     environment:
        - MYSQL_ROOT_PASSWORD="secret"
  web:
    image: apache
    build: .
    container_name: apache_web
    restart: always
    ports:
      - "8080:80"
```

#### Tham khảo một số lệnh Docker compose

Lệnh docker-compose cung cấp một số các tùy chọn để quản lý docker container với docker-compose.

**build –**

Tùy chọn build được dùng để build images cho các dịch vụ được định nghĩa


```bash
$ docker-compose build             ## Build all services
$ docker-compose build web         ## Build single service
```

**up –**

Dùng để tạo docker container với các dịch vụ có sẵn trong file docker-compose.yml trong thư mục hiện tại. Dùng -d để khởi động container trong chế độ chạy ngầm.

```bash
$ docker-compose up -d            ## Create all containers
$ docker-compose up -d web        ## Create single container
```

**down –**

Sẽ dừng và xóa tất cả container, network và các images được liên kết cho các dịch vụ được định nghĩa trong file config.

```bash
$ docker-compose down           ## Restart all containers
$ docker-compose down web       ## Restart single container
```

**ps –**

Sẽ liệt kê tất cả container được tạo cho các dịch vụ được định nghĩa trong file config với status, ports và command

```bash
$ docker-compose ps 
```

**exec –**

Sẽ thực thi một lệnh tới container đang chạy. Ví dụ, liệt kê danh sách các file trong container được liên kết với dịch vụ web.


```bash
$ docker-compose exec web ls -l
```

**start –**

Sẽ dừng các container của các dịch vụ được định nghĩa trong file config.

```bash
$ docker-compose start            ## Start all containers
$ docker-compose start web        ## Start single container
```

**stop –**

Sẽ dừng các container đang chạy cho các dịch vụ được định nghĩa trong file config

**restart –**

Sẽ khởi động lại các container của các dịch vụ trong file config.

**pause –**

Sẽ tạm dừng các container dịch vụ được định nghĩa trong config

**unpause –**

Sẽ bắt đầu các container bị tạm dừng

**rm –**

Sẽ xóa các container bị dừng đối với các dịch vụ được khai báo trong file config

### Ví dụ về docker-compose

Trong ví dụ này, mình sẽ tạo hai docker container sử dụng Docker compose. Một docker container chạy MySQL và container còn lại chạy Apache web server.

Các bạn hãy làm theo hướng dẫn của mình và xem những gì xảy ra ở đây

#### Bước 1: Tạo cấu trúc thư mục

Đầu tiên, tạo cấu trúc thư mục. Ở đây, webapp là thư mục ứng dụng web của mình. Cũng tạo luôn file index.html trong thư mục webapp.


```bash
$ mkdir dockercompose && cd dockercompose
$ mkdir webapp
$ echo "<h2>It Works</h2>" > webapp/index.html
```

#### Bước 2: Tạo Dockerfile cho webapp

Bây giờ tạo Dockerfile trong thư mục webapp để tạo image tùy chỉnh cho ứng dụng bao gồm cả Apache webserver.

```bash
$ vim  webapp/Dockerfile
```

Và nội dung sau


```node
FROM tecadmin/ubuntu-ssh:16.04

RUN apt-get update \
   && apt-get install -y apache2

COPY index.html /var/www/html/
WORKDIR /var/www/html
CMD ["apachectl", "-D", "FOREGROUND"]
EXPOSE 80
```

#### Bước 3: Tạo file Docker compose

Cuối cùng, tạo file cấu hình docker compose (docker-compose.yml) trong thư mục hiện tại. Nó sẽ định nghĩa tất cả container sẽ được dùng trong phần thiết lập hiện tại.


```bash
$ vim  docker-compose.yml
```

Và thêm nội dung sau


```bash
version: '3'
services:
  db:
     image: mysql
     container_name: mysql_db
     restart: always
     environment:
        - MYSQL_ROOT_PASSWORD="secret"
  web:
    image: apache
    build: ./webapp
    depends_on:
       - db
    container_name: apache_web
    restart: always
    ports:
      - "8080:80"
```

File docker compose ở trên được thiết lập cho hai container. Container đầu tiên là mysql database server và container thứ hai là web server. Container web sẽ chạy ứng dụng của mình trên Apache server. Vì nó được tùy chỉnh nên mình xác định thư mục build cho webapp.

#### Bước 4: Build webapp image

Bây giờ, build một image sử dụng câu lệnh sau đây. Nó sẽ tạo một image tên là apache sử dụng Dockerfile và nội dung từ thư mục webapp.


```bash
$ docker-compose build
```

Đọc dữ liệu đầu ra của lệnh trên. Mình đã bỏ qua vài phần đầu ra không cần thiết. Dòng đầu tiên của output cho thấy nó bỏ qua việc build db container do build không được định nghĩa. Đối với web container nó dùng webapp/Dockerfile để build image.


```bash
db uses an image, skipping
Building web
Step 1/6 : FROM tecadmin/ubuntu-ssh:16.04
16.04: Pulling from tecadmin/ubuntu-ssh
b3e1c725a85f: Pull complete
4daad8bdde31: Pull complete
63fe8c0068a8: Pull complete
4a70713c436f: Pull complete
bd842a2105a8: Pull complete
c41407f48fa7: Pull complete
1fcfeb9b5ef4: Pull complete
13195a7d2240: Pull complete
b86be64bbda8: Pull complete
8c951fe917dc: Pull complete
f74bc80103b6: Pull complete
Digest: sha256:523d6fbc97954e9f77231bf54bfcfbbdd4805349887477fbac4a63dc735d777d
Status: Downloaded newer image for tecadmin/ubuntu-ssh:16.04
 ---> bb63b492da01
Step 2/6 : RUN apt-get update    && apt-get install -y apache2
 ---> Running in 00be0dd717ce
[[[Removed long output from here]]]
 ---> 41c731590234
Removing intermediate container 00be0dd717ce
Step 3/6 : COPY index.html /var/www/html/
 ---> 42f84d4c2243
Removing intermediate container 945aaee6cbde
Step 4/6 : WORKDIR /var/www/html
 ---> 40bebd21e352
Removing intermediate container e13f5f412906
Step 5/6 : CMD apachectl -D FOREGROUND
 ---> Running in ab0db1ef1c6e
 ---> 587bf2323289
Removing intermediate container ab0db1ef1c6e
Step 6/6 : EXPOSE 80
 ---> Running in 7bcbef52d585
 ---> 8f03d4135394
Removing intermediate container 7bcbef52d585
Successfully built 8f03d4135394
Successfully tagged apache:latest
```

#### Bước 5: Khởi động docker compose

Cuối cùng, khởi động container sử dụng lệnh docker-compose up Dùng -d để chạy chúng trong chế độ ngầm.

```bash
$ docker-compose up -d
```

Bạn có thể truy cập ứng dụng web trên thư mục apache_web bằng cách truy cập system host port 8080. Ví dụ, http://dockerhost:8080 trong đó dockerhost là địa chỉ ip hoặc hostname của máy đang chạy docker.

#### Bước 6: Cập nhật nội dung trong ứng dụng web

Giờ mình sẽ thêm ít nội dung vào ứng dụng web. Mình đã thêm ít nội dung tới file webapp/index.html như sau:


```bash
$ echo "Welcome to Docker Compose Tutorial" >> webapp/index.html
```

Sử dụng lệnh sau để rebuild container webapp và khởi chạy bằng cách sử dụng docker-compose

```bash
$ docker-compose build
$ docker-compose up -d
```

Dữ liệu đầu ra như sau:

Bạn có thể thấy rằng container mysql_db đang hiển thị không thay đổi gì so với lúc mình chưa thêm nội dung. Chỉ có apache_web container được tạo do lần build image mới đã được sử dụng.

Truy cập lại ứng dụng web trên port 8080 của máy chạy docker. Bạn sẽ thấy kết quả đã được cập nhật nội dung.


```bash
http://dockerhost:8080/
tecadmin.net/tutorial/docker/docker-introduction/
```


