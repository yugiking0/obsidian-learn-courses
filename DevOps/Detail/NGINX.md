# NGINX là gì? NGINX có thể làm được gì?
---
**NGINX** là phần mềm mã nguồn mở để phục vụ web, reverse proxy, caching, load balancer, media streaming,… Nó bắt đầu như một web server được thiết kế để có hiệu suất và sự ổn định tối đa. Ngoài các khả năng của máy chủ HTTP. NGINX cũng có thể hoạt động như một máy chủ proxy cho email (IMAP, POP3 và SMTP). Và một trình cân bằng tải và reverse proxy cho các máy chủ HTTP, TCP và UDP.

## NGINX là gì? 

Mục tiêu đằng sau NGINX là tạo ra web server nhanh nhất và duy trì sự xuất sắc đó vẫn là mục tiêu trung tâm của dự án. NGINX luôn đánh bại Apache và các máy chủ khác trong các tiêu chuẩn đo lường hiệu suất của máy chủ web.

![[Pasted image 20230907102656.png]]

NGINX là gì?

Kể từ khi phát hành ban đầu NGINX, các trang web đã mở rộng từ các trang HTML đơn giản sang nội dung động, nhiều mặt. NGINX đã phát triển cùng với nó và hiện hỗ trợ tất cả các thành phần của Web hiện đại, bao gồm WebSocket, HTTP / 2 và phát trực tuyến nhiều định dạng video (HDS, HLS, RTMP và các định dạng khác).

## Lịch sử hình thành

Ban đầu, Igor Sysoev đã viết NGINX để giải quyết ***vấn đề C10K***. Một thuật ngữ được đặt ra vào năm 1999. Để mô tả những khó khăn mà các máy chủ web hiện tại gặp phải khi xử lý số lượng lớn (10K) kết nối đồng thời (C). Với kiến ​​trúc event-driven, asynchronous, NGINX đã cách mạng hóa cách các máy chủ hoạt động trong bối cảnh hiệu suất cao. Và trở thành máy chủ web nhanh nhất hiện có.

![[Pasted image 20230907102751.png]]

Sau khi mở nguồn cung ứng  dự án vào năm 2004. Và nhận thấy ​​việc sử dụng nó tăng theo cấp số nhân. Sysoev đồng sáng lập NGINX, Inc. để hỗ trợ tiếp tục phát triển NGINX. Và tiếp thị NGINX Plus như một sản phẩm thương mại với các tính năng bổ sung được thiết kế cho khách hàng doanh nghiệp. Ngày nay, NGINX và NGINX Plus có thể xử lý hàng trăm ngàn kết nối đồng thời.

## Nginx có tính năng gì?

### Những tính năng của máy chủ HTTP Nginx

- Khả năng xử lý lớn với hơn 10.000 kết nối cùng một thời điểm với bộ nhớ thấp.
- Phục vụ cho các tập tin tĩnh (static files) và thực hiện lập chỉ mục tập tin.
- Gia tăng tốc độ reverse proxy thông qua bộ nhớ đệm (cache).
- Cân bằng quá trình tải đơn giản cùng khả năng chịu lỗi.
- Giúp nâng cao tốc độ cùng bộ nhớ đệm của FastCGI, uwsgi, SCGI, và loạt máy chủ memcached.
- Hỗ trợ Kiến trúc modular, nâng cao tốc độ nạp trang thông qua nén gzip tự động.
- Giúp mã hoá SSL cùng TLS.
- Cấu hình rất linh hoạt; sao lưu nhật ký truy vấn.
- Xoay chiều lỗi 3XX-5XX.
- Rewrite URL (URL rewriting) sử dụng regular expressions.
- Làm giảm tỷ lệ đáp ứng truy vấn.
- Kiểm soát các kết nối cùng một thời điểm và những truy vấn cùng 1 địa chỉ.
- Có khả năng nhúng mã PERL.
- Được hỗ trợ và tương thích trên IPv6.
- Được hỗ trợ ở WebSockets.
- Khả năng truyền tải file FLV và MP4.

### Những tính năng máy chủ mail proxy của Nginx

Gồm các phương pháp xác thực như sau:

- POP3: USER/PASS, APOP, AUTH LOGIN/PLAIN/CRAM-MD5;
- IMAP: LOGIN, AUTH LOGIN/PLAIN/CRAM-MD5;
- SMTP: AUTH LOGIN/PLAIN/CRAM-MD5;
- Hỗ trợ SSL, STARTTLS cùng STLS.

## Khác biệt giữa Apache Server và NGINX server là gì?

Phương thức kết nối được xử lý giữa NGINX server và Apache server chính là sự khác biệt cơ bản nhất của chúng.

Nếu Apache dùng cơ chế phân luồng (**forked threaded**) hay keep-alive để giúp người dùng luôn có một kết nối mở thì ở NGINX lại áp dụng một vòng lặp sự kiện không bị ngăn chặn (non-blocking event loop), để làm cho các kết nối vùng (pools connection) vận hành không đồng bộ bằng các tiến trình công việc. Từ đó, NGINX giúp cho CPU và RAM không gặp sự cố gì khi lượng truy cập gia tăng tại một thời điểm nào đó.

Đồng thời, tại Apache server thực hiện xử lý nội dung tĩnh thông qua những cách thức dựa trên file thông thường cùng nội dung động bằng việc cho nhúng một bộ xử lý của ngôn ngữ thì NGINX chỉ có thể xử lý duy nhất nội dung tĩnh. Chính vì thế, bạn cần thực hiện cấu hình server này và bộ vi xử lý theo những giao thức mà nó được phép kết nối.

Như vậy, NGINX chiếm nhiều ưu thế hơn so với Apache. NGINX gần như sở hữu đa số các tính năng của Apache. Đặc biệt, nhờ tốc độ xử lý các truy vấn tốc độ, hiệu suất sử dụng bộ nhớ trên máy chủ cũng là một điểm cộng cho NGINX. Bên cạnh đó, server này chiếm không quá nhiều Ram cùng CPU cho lượng truy vấn vô cùng khổng lồ.

## Hướng dẫn cài đặt NGINX

Để cài đặt NGINX, bạn có thể sử dụng 2 cách như sau:

- Dùng gói (package) dựng sẵn.
- Cài đặt từ source.

Cách đầu tiên được nhận xét là đơn giản và nhanh chóng hơn, nhưng cài đặt từ source sẽ mang đến khả năng cài đặt thêm các module khác làm cho NGINX trở nên vượt trội hơn. Người dùng được phép tùy chỉnh sao cho phù hợp với nhu cầu của ứng dụng.

Thao tác duy nhất bạn cần thực hiện để cài đặt một gói Debian dựng sẵn là:

Copy

```bash
sudo apt-get update
sudo apt-get install nginx
```

Sau khi hoàn thành quá trình cài đặt, bạn có thể kiểm tra tất cả đã ổn hay chưa thông qua lệnh sau, sẽ hiển thị phiên bản NGINX vừa được cài đặt:

Copy

```bash
sudo nginx -v
nginx version: nginx/1.18.2
```

Web Server mới được cài đặt ở /etc/nginx/. Khi bạn truy cập vào thư mục này, sẽ có nhiều tệp tin cùng thư mục xuất hiện. Tuy nhiên, thứ bạn cần lưu ý nhất đó chính là tệp tin nginx.conf và thư mục `sites-available`.

**Xem thêm:** [Cách thiết lập Video Streaming Server bằng Nginx-RTMP trên Ubuntu 20.04](https://vietnix.vn/cach-thiet-lap-video-streaming-server-bang-nginx-rtmp-tren-ubuntu-20-04/)

## Cấu hình NGINX chi tiết

Dưới đây là thiết lập cần được chú ý tại tập tin nginx.conf:

Copy

```bash
user www-data;
worker_processes 4;
pid /run/nginx.pid;

events {
    worker_connections 768;
    # multi_accept on;
}

http {

    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;
    # server_tokens off;

    # server_names_hash_bucket_size 64;
    # server_name_in_redirect off;

    include /etc/nginx/mime.types;
    default_type application/octet-stream;

    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;

    gzip on;
    gzip_disable "msie6";

    # gzip_vary on;
    # gzip_proxied any;
    # gzip_comp_level 6;
    # gzip_buffers 16 8k;
    # gzip_http_version 1.1;
    # gzip_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript;

    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
```

Tệp tin sẽ được cấu trúc nên các ngữ cảnh. Thứ nhất là **events**, tiếp theo là **http**. Cấu trúc được nhận xét là rất có ích trong việc cấu hình, như từng ngữ cảnh sẽ được chèn trong ngữ cảnh khác. Ngoài ra, còn được thừa hưởng tất cả từ cha mẹ của chúng nhưng cũng được phép ghi đè lên chúng nếu cần thiết.

Ở tập tin này bạn có thể tùy chỉnh chúng theo nhu cầu, tuy nhin bạn cũng có thể tận dụng các thiết lập mặc định. Tập tin này có một số thành phần quan trọng như sau:

- **worker_processes**: Đây là một thiết lập dùng để định nghĩa worker processes mà NGINX sẽ dùng. Do NGINX là đơn luồng (single threaded), nên nó thường bằng lượng lõi CPU.
- **worker_connection**: Đây chính là lượng kết nối tối đa trong một thời điểm cho mỗi worker process và thông báo đến những worker process của chúng ta số lượng người có thể phục vụ cùng lúc bởi NGINX.
- **access_log & error_log**: Đây là những tệp tin mà NGINX sẽ sử dụng để log bất kỳ lỗi và số lần truy cập. Các bản ghi này thường được sử dụng để gỡ lỗi hoặc sửa chữa.
- **gzip**: Thành phần này là các thiết lập nén GZIP của các NGINX reponse. Tại đây có chứa nhiều thiết lập phụ, phần bị comment do mặc định làm cho hiệu suất gia tăng đáng kể. Tại những thiết lập phụ của GZIP, bạn cần lưu ý tới `gzip_comp_level`, đây chính là mức nén nằm ở khoảng từ 1 – 10. Hầu hết, giá trị này sẽ hiếm khi lớn hơn 6 — vì lợi ích sẽ không bao nhiêu nếu trên mức này, do nó cần dùng nhiều CPU hơn. `gzip_types` chính là một danh sách dạng response sẽ được nén.

Số lượng website được NGINX hỗ trợ có thể nhiều hơn 1, cùng những tệp tin định nghĩa các website của bạn nằm ở thư mục `/etc/nginx/sites-available.`

Lưu ý rằng, những tệp tin nằm ở thư mục này không “live” — bạn có thể có nhiều tệp tin định nghĩa các trang web ở đây, nhưng NGINX không tác động đến chúng cho đến khi được symlink (liên kết tượng trưng) tới thư mục `/etc/nginx/sites-enabled` (hoặc có thể sao chép chúng đến thư mục này, nhưng symlink chắc chắn rằng chỉ có một bản sao chép trên một tệp tin được theo dõi).

Nó mang đến cho bạn giải pháp nhanh nhất đưa các website online và offilne mà không phải tiến hành xóa bỏ tập tin nào — Đến lúc bạn hoàn tất chuẩn bị cho trang web, tạo symlink đến `sites-enabled`, sau đó khởi động lại NGINX.

Thư mục site-available sẽ chứa cấu hình cho các host ảo (virtual host). Tại đây, web server được phép cấu hình các website với các từng cấu hình khác nhau. Những website trong thư mục không live và và chỉ được đồng ý nếu chúng ta tạo một symlink đến thư mục `sites-enabled`.

Người dùng dược phép tạo một tệp tin mới hoặc tùy chỉnh một tệp tin mặc định cho ứng dụng. Dưới đây là một cấu hình thông thường:


```bash
upstream remoteApplicationServer {
    server 10.10.10.10;
}

upstream remoteAPIServer {
    server 20.20.20.20;
    server 20.20.20.21;
    server 20.20.20.22;
    server 20.20.20.23;
}


server {
    listen 80;
    server_name www.customapp.com customapp.com
    root /var/www/html;
    index index.html

        location / {
            alias /var/www/html/customapp/;
            try_files $uri $uri/ =404;
        }

        location /remoteapp {
            proxy_set_header   Host             $host:$server_port;
            proxy_set_header   X-Real-IP        $remote_addr;
            proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
            proxy_pass http://remoteAPIServer/;
        }

        location /api/v1/ {
            proxy_pass https://remoteAPIServer/api/v1/;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
            proxy_redirect http:// https://;
        }
}
```

Tương tự `nginx.conf`, nó cũng dùng định nghĩa các ngữ cảnh lồng nhau (đồng thời mọi thứ cũng được lồng trong ngữ cảnh **HTTP** CỦA `nginx.conf`, do đó chúng thừa hưởng tất cả từ nó).

Ngữ cảnh **server** định nghĩa một server ảo dùng để xử lý hết các request do client yêu cầu. Sẽ có nhiều khối server, NGINX sẽ tiến hành lựa chọn trong số đó dựa theo những chỉ thị `listen` và `server_name`.

Ở mỗi khối server, chúng ta định nghĩa lượng lớn ngữ cảnh **location** sẽ được áp dụng để quyết định phương thức xử lý các request cho client. Theo đó, khi nhận được request, NGINX sẽ thử khớp URI tới tới những định nghĩa location và xử lý theo cách hợp lý nhất.

Trong ngữ cảnh location sẽ có nhiều chỉ thị quan trọng được dùng tới, ví dụ như:

- **try_files** sẽ phục vụ các tệp tin tĩnh được tìm thấy ở thư mục được trỏ tới do chỉ thị gốc.
- **proxy_pass** thực hiện mang request đến proxy server xác định.
- **rewrite** thực hiện viết lại URI đến thông qua một regular expression để đạt được một khối location có thể xử lý nó.

Ngữ cảnh **upstream** định nghĩa một pool của những server cái NGINX sẽ ủy quyền những request tới. Sau khi hoàn tất việc tạo khối upstream và định nghĩa một server nằm trong nó chúng có thể xác thực nó thông qua tên nằm trong các khối location.

Ngoài ra, một ngữ cảnh upstream có thể sẽ chứa nhiều server được gán tại đó bởi vì NGINX sẽ làm một vài load balancing khi ủy quyền cho các request tới.

## Khởi động NGINX

Sau khi hoàn tất quá trình cấu hình và đưa ứng dụng website đến thư mục tương thích. Bạn đã có thể khởi động NGINX và bắt đầu sử dụng thông qua câu lệnh:


```bash
sudo service nginx start
```

Trong trường hợp, nếu bạn cần thay đổi cấu hình chỉ cần thực hiện quá trình tải lại (không có thời gian downtime) thông qua lệnh như sau: 


```bash
service nginx reload 
```

Kết thúc bằng việc kiểm tra trạng thái của NGINX theo cách thực hiện lệnh sau: 


```bash
service nginx status
```

## NGINX phục vụ web

Mặc dù NGINX trở nên nổi tiếng là máy chủ web nhanh nhất, kiến ​​trúc cơ bản có thể mở rộng đã chứng minh lý tưởng cho nhiều tác vụ web ngoài việc phục vụ nội dung. Do có thể xử lý khối lượng kết nối lớn, NGINX thường được sử dụng làm reverse proxy và cân bằng tải để quản lý lưu lượng đến và phân phối đến các upstream server – mọi thứ từ máy chủ cơ sở dữ liệu đến dịch microservices.

![[Pasted image 20230907102809.png]]

NGINX cũng thường được đặt giữa máy khách và máy chủ web thứ hai, để phục vụ như một SSL Terminator, [TLS](https://vietnix.vn/tls-la-gi/) hoặc web accelerator. Hoạt động như một trung gian, NGINX xử lý hiệu quả các tác vụ có thể làm chậm máy chủ web của bạn, chẳng hạn như SSL/TLS negotiating hoặc nén và cache nội dung để cải thiện hiệu suất. Các trang web động, được xây dựng bằng cách sử dụng mọi thứ từ Node.js đến PHP, thường triển khai NGINX làm cache nội dung và reverse proxy để giảm tải cho các máy chủ ứng dụng và sử dụng phần cứng hiệu quả nhất .

## NGINX và NGINX Plus có thể làm gì cho bạn?

NGINX Plus và NGINX đang là các giải pháp application delivery và [cho thuê máy chủ web](https://vietnix.vn/thue-may-chu/) tốt nhất được sử dụng bởi các trang web có lưu lượng truy cập cao như Dropbox, Netflix và Zynga. Hơn 400 triệu trang web trên toàn thế giới dựa vào NGINX Plus và NGINX để cung cấp nội dung của họ một cách nhanh chóng, đáng tin cậy và an toàn.

- NGINX làm cho bộ cân bằng tải phần cứng trở nên lỗi thời. Là một bộ cân bằng tải nguồn mở chỉ có phần mềm. NGINX ít tốn kém hơn và có thể dễ cấu hình hơn các bộ cân bằng tải phần cứng. Và được thiết kế cho các kiến ​​trúc đám mây hiện đại. NGINX Plus hỗ trợ cấu hình lại nhanh chóng và tích hợp với các công cụ DevOps hiện đại để giám sát dễ dàng hơn.
- NGINX là một công cụ đa chức năng. Với NGINX, bạn có thể sử dụng cùng một công cụ như bộ cân bằng tải, reverse proxy, cache nội dung và máy chủ web. Giảm thiểu số lượng công cụ và cấu hình mà tổ chức của bạn cần duy trì. NGINX cung cấp các hướng dẫn, hội thảo trên web và một loạt các tài liệu để giúp bạn vững bước. NGINX Plus bao gồm hỗ trợ khách hàng phản ứng nhanh. Do đó bạn có thể dễ dàng nhận trợ giúp chẩn đoán bất kỳ phần nào trong ngăn xếp của bạn sử dụng NGINX hoặc NGINX Plus.

**>> Xem thêm: [NGINX Configuration: Hướng dẫn cho người mới](https://vietnix.vn/nginx-configuration/)**

## Lời kết

Với những thông tin trên về NGINX là gì hy vọng sẽ đem lại thêm kiến thức mới cho bạn. Nếu bạn có thắc mắc hay đóng góp ý kiến, mời bạn để lại bình luận phía dưới bài viết này. Vietnix xin chân thành cảm ơn bạn!