# NGINX Configuration: Tìm hiểu về context NGINX configuration cho người mới
---
**NGINX** là một phần mềm web server mã nguồn mở. Nó được ứng dụng trong web HTTP, reverse proxy, HTTP load balancer và email proxy. Bài viết này sẽ cung cấp những kiến thức nền tảng về NGINX config.

## Giới thiệu về NGINX

[[NGINX]] (đọc là “engine-ex”), là một server web hiệu suất cao. Nó chịu trách nhiệm xử lý tải của những trang web lớn nhất trên internet. NGINX đặc biệt tốt trong việc xử lý nhiều kết nối đồng thời. Ngoài ra, nó cũng vượt trội trong việc phục vụ các nội dung tĩnh (static content).

Bên cạnh nhiều người dùng đã nhận thức được khả năng của NGINX, các newbie vẫn thường bị nhẫm lẫn trong việc sử dụng phần mềm này. Vì vậy, bài viết này sẽ tập trung vào cấu trúc cơ bản của file NGINX config. Cùng với đó là một số nguyên tắc cơ bản về cách thiết kế các file.

## Tìm hiểu về context NGINX config

Hướng dẫn dưới đây sẽ bao gồm các cấu trúc cơ bản được tìm thấy trong file NGINX config chính. Vị trí của file này sẽ tùy vào cách người dùng cài đặt phần mềm trên máy. Thông thường , nó sẽ nằm ở đường dẫn `/etc/nginx/nginx.conf.` Nếu không, có thể file này sẽ ở `/usr/local/nginx/conf/nginx.conf` hay `/usr/local/etc/nginx/nginx.conf.`

Về tổng quan, file config chính sẽ được sắp xếp theo cấu trúc cây, xác định bởi các tập hợp hay dấu hoặc ({ }). Trong thuật ngữ NGINX, thành phần được xác định bởi các dấu ngoặc gọi là “context”. Các context này chứa thông tin chi tiết về cấu hình, được phân chia theo từng loại cụ thể. Về cơ bản, cách chia này cho ta một cấu trúc có tổ chức tốt.

Các context có thể được xếp lớp trong nhau. Vì vậy NGINX cung cấp một cấp độ directive kế thừa. Theo quy tắc chung, nếu một directive có giá trị trong nhiều phạm vi được lồng vào nhau, một khai báo trong context lớn hơn sẽ được truyền vào bất kỳ context con nào dưới dạng giá trị mặc định. Các context con sẽ ghi đè các giá trị này theo ý muốn. Nên nhớ rằng, ghi đè vào bất kỳ directive loại mảng nào sẽ thay thế giá trị trước đó, chứ không thêm vào nó.

Các directive chỉ được sử dụng trong các context được thiết kế cho nó. NGINX sẽ báo lỗi khi đọc một file config với các directive được khai báo trong một context không chính xác. Để tham khảo, tài liệu của NGINX có chứa thông tin về các context tương ứng với mỗi directive.

Dưới đây là các loại context phổ biến nhất mà ta sẽ gặp khi sử dụng NGINX.

![[Pasted image 20230907102425.png]]


## Các Context chính trong NGINX config

Trong nhóm đầu tiên, ta sẽ tìm hiểu về các context cốt lõi của NGINX. Nó dùng để xây dựng cấu trúc cây phân cấp (hierarchical tree) và phân tách các mặt của block config rời rạc. Chính các context này sẽ bao gồm những cấu trúc chính của NGINX config.

### Main Context (Global Context)

Context khái quát nhất của NGINX config chính là main context. Đây là context duy nhất không nằm trong các khối context điển hình có dạng:

```node
# The main context is here, outside any other contexts
. . .

context {
    . . .
}
```

Bất kỳ directive nào tồn tại bên ngoài các khối này sẽ được cho là “main” context. Cần nhớ rằng, nếu NGINX config được cấu hình theo kiểu module, một số file sẽ chứa các lệnh tồn tại bên ngoài context. Nhưng nó sẽ được chứa trong các context khi config được kết nối lại với nhau.

Main context thể hiện một môi trường rộng nhất dành cho NGINX config. Nó được sử dụng để cấu hình các chi tiết ảnh hưởng đến toàn bộ ứng dụng ở cấp độ cơ bản. Khi các directive trong phần này ảnh hưởng những context ở cấp độ thấp hơn, một trong số chúng sẽ không được kế thừa. Sở dĩ vì các directive này không thể bị ghi đè ở các tầng thấp hơn.

Một số chi tiết phổ biến được cấu hình trong main context là người dùng và nhóm để chạy worker processess. Như số lượng worker, file để lưu PID của main process, CPU worker. File error_log mặc định của toàn bộ ứng dụng có thể được thiết lập ở cấp độ này (nó cũng có thể bị ghi đè ở các context cụ thể khác).

### Event Context

Event Context là một context được chứa bên trong main context. Nó dùng để đặt các tùy chọn ở mức độ blogal, ảnh hưởng đến cách NGINX xử lý các kết nối ở cấp độ chung. Trong NGINX config, chỉ có một event context duy nhất được xác định.

Event context ở trong file config sẽ có dạng sau:

```node
# main context

events {

    # events context
    . . .

}
```

NGINX sử dụng mô hình xử lý kết nối dựa trên các event. Do đó, các directive được xác định trong context này sẽ xác định cách worker processes ở trên xử lý các kết nối. Chủ yếu, các directive được tìm thấy ở đây được sử dụng để chọn ra kỹ thuật xử lý kết nối để sử dụng. Hoặc là sửa đổi cách các phương thức được triển khai.

Thông thường, phương thức xử lý kết nối được chọn tự động, dựa trên sự lựa chọn tối ưu mà nền tảng có sẵn. Đối với các hệ thống của Linux, sự lựa chọn tốt nhất thường là `epoll`.

Các mục khác có thể được cấu hình là số lượng kết nối mỗi worker có thể xử lý. Hay quyết định mỗi worker chỉ đảm nhận 1 kết nối hay tất cả kết nối đang chờ cùng lúc. Và quyết định xem các worker có thay phiên nhau respond các event không.

### HTTP Context

Khi cấu hình NGINX như một web server hay một [reverse proxy,](https://vi.wikipedia.org/wiki/Reverse_proxy) http context sẽ chiếm phần lớn cấu hình. Context này sẽ chứa mọi directive cũng như các context cần thiết khác để xác định cách các chương trình xử lý kết nối HTTP hay [HTTPS](https://vietnix.vn/https-la-gi/).

HTTP context thực ra tương đương với event context, nên chúng sẽ được liệt kê cạnh nhau, thay vì lồng vào nhau. Cả hai đều là context con của main context:


```node
# main context

events {
    # events context
    . . .
}

http {
    # http context
    . . .
}
```

Các context thấp hơn sẽ cụ thể hơn về cách xử lý request. Nhưng các directive ở cấp độ này sẽ kiểm soát mặc định cho mỗi máy chủ ảo được xác định trong nó. Một lượng lớn các directive có thể được cấu hình theo context này và những context thấp hơn. Việc này tùy thuộc cách người dùng xác định quyền thừa kế.

Một số directive thường gặp kiểm soát location mặc định cho các truy cập và nhật ký lỗi (`access_log` và `error_log`). Nó cũng cấu hình I/O không đồng bộ cho các hoạt động của file (`aio, sendfile, directio`_)_. Cấu hình trạng thái server khi xảy ra lỗi (`error_page)`_._ Một số directive khác cấu hình nén (`gzip, gzip_disable`_)_, fine-tune cài đặt keep alive TCP (`keepalive_disable, keepalive_requests, keepalive_timeout`_)_. Hoặc cấu hình các quy tắc mà NGINX sẽ theo để tối ưu hóa các packet và system call (`sendfile, tcp_nodelay, tcp_nopush`_)._ Các directive bổ sung cấu hình root các tài liệu tầng ứng dụng và index file (`root, index`_)_. Nó cũng thiết lập các hash table dùng để chứa nhiều loại dữ liệu khác nhau (`*_hash_bucket_size` và `*_hash_max_size` cho `server_names, types, variables`).

### Server Context

Server Context được khai báo trong http context. Đây cũng là một ví dụ về các context lồng nhau. Server context cũng là context đầu tiên cho phép khai báo nhiều lần.

Định dạng chung của server context có dạng như sau:

```http
# main context

http {
    # http context
    server {
        # first server context
    }

    server {
        # second server context
    }
}
```

Trong context này, mỗi trường hợp sẽ xác định một virtual server cụ thể để xử lý yêu cầu của client. Do đó, server context cho phép khai báo nhiều lần. Ta có thể có bao nhiêu server block tùy ý. Mỗi block có thể xử lý một subnet cụ thể.

Đồng thời, server context cũng là context đầu tiên là NGINX phải sử dụng một thuật toán lựa chọn để đưa ra quyết định. Mỗi client request sẽ được xử lý dựa trên cấu hình được xác định trong mỗi server context. Do đó, NGINX cần quyết định server context nào phù hợp nhất cho request đó. Các directive được sử dụng để quyết định server context là:

- **listen:** là sự kết hợp địa chỉ IP/port mà server block này được thiết kế để respond. Nếu một request từ client phù hợp với các giá trị này, block này có khả năng sẽ được lựa chọn để xử lý kết nối.
- **server_name:** directive này là một thành phần khác, dùng để chọn một server block để xử lý. Nếu có nhiều server đáp ứng được directive listen, NGINX sẽ phân tích cú pháp header “Host” của request và lựa chọn block phù hợp.

Các directive trong context này có thể ghi đè lên nhiều directive được xác định trong http context. Bên cạnh các directive từ http context, ta cũng có thể cấu hình file để phản hồi lại các request (`try_files`), redirect và rewrite (`return, rewrite`), đặt giá trị cho biến (`set`).

### Location Context

Location text có tương đối nhiều điểm chung với server context. Lấy ví dụ, nhiều location context có thể được xác định, mỗi location được dùng để xử lý một loại client request xác định. Và mỗi location được chọn để phù hợp với định nghĩa location với client request thông qua một thuật toán lựa chọn.

Các directive xác định xem một server block có được xác định trong server context hay không. Thành phần quyết định khả năng xử lý yêu cầu của location sẽ nằm trong định nghĩa location (dòng mở đầu location block).

Cú pháp chung của location context:


```node
location match_modifier location_match {
    . . .
}
```

Location block không giống với server block – lồng bên trong nhau, chúng sẽ nằm bên trong các server context. Việc này sẽ hữu ích khi tạo một location context chung hơn để bắt một subnet lưu lượng cụ thể. Sau đó, các process sau sẽ dựa trên các tiêu chí cụ thể hơn, với các context bổ sung bên trong:


```node
# main context

server {
    # server context

    location /match/criteria {
        # first location context
    }

    location /other/criteria {
        # second location context

        location nested_match {
            # first nested location
        }

        location other_nested {
            # second nested location
        }
    }
}
```

Location block phân chia các request trong một server block thông ua URI của request. Đây là phần xuất hiện sau tên miền hoặc tổ hợp địa chỉ IP/port.

Các directive mới ở tầng parent cho phép truy cập vào location bên ngoài document root (`alias`). Ngoài ra còn có thể đánh dấu location để chỉ có thể truy cập nội bộ (`internal`). Proxy đến các server hay location khác (sử dụng http, fastcgi, scgi, uwsgi proxying).

## Các context khác trong NGINX config

Các context trong phần này phụ thuộc vào các module tùy chọn. Ngoài ra các context này còn có thể được sử dụng cho các chức năng ít cần đến. Có một vài context mà chúng tôi sẽ chỉ nói sơ qua về chức năng:

- `split_clients:` Dùng để phân loại các client mà server nhận bằng cách dán nhãn chúng với các biến (dựa trên %). Context này có thể dùng để thử nghiệm A / B bằng cách cung cấp các content khác nhau cho từng host khác nhau.
- `pert / perl_set:` Cấu hình location mà Perl sẽ xuất hiện. Context này chỉ được sử dụng với Perl.
- `map:` Thường dùng để đặt giá trị của các biến không độc lập. Context này cho một ánh xạ của giá trị một biến, nhằm xác định giá trị của biến thứ hai.
- `geo:` Như context trên, geo thường dùng để chỉ định các ánh xạ. Dù vậy, ánh xạ này được sử dụng để phân loại địa chỉ IP client. Geo đặt giá trị của một biến tùy thuộc vào địa chỉ IP đang kết nối.
- `types:` Cũng là một context liên quan đến các ánh xạ. Types dùng để ánh xạ các loại MIME đến phần mở rộng của file cần được liên kết. Nó thường được dùng với NGINX thông qua một file bắt nguồn từ file config chính `nginx.conf.`
- `charset_map:` Dùng để ánh xạ bảng chuyển đổi từ một tập hợp ký tự thành một tập hợp khác. Trong header của context, cả hai tập hợp đều được liệt kê. Trong body, ánh xạ sẽ được thực hiện.

Các context dưới đây không hẳn là phổ biến như những context đã được đề cập. Tuy nhiên, chúng vẫn rất hữu dụng trong quá trình sử dụng.

### Upstream Context

Upstream Context được dùng để định nghĩa và cấu hình các server upstream. Về cơ bản, context này xác định một nhóm các máy chủ mà NGINX có thể proxy các request đến. Context này chủ yếu được dùng khi cấu hình proxy của các loại khác nhau.

Upstream Context được đặt trong http context. Đồng thời nằm bên ngoài bất kỳ server context nào khác. Nó có dạng chung như sau:

```node
# main context

http {
    # http context

    upstream upstream_name {
        # upstream context

        server proxy_server1;
        server proxy_server2;
        . . .
    }

    server {
        # server context
    }
}
```

Upstream Context sau đó có thể được tham chiếu theo tên trong máy chủ hoặc các location block để pass các request của một loại xác định, đi đến nhóm các server cụ thể. Sau đó, upstream sẽ sử dụng một thuật toán (mặc định là round-robin) để xác định server nó sẽ gửi request. Context này cho phép NGINX cân bằng tải khi đang proxy các request.

### Mail Context

Bên cạnh việc được sử dụng như một server web hay reverse proxy, NGINX cũng có thể được sử dụng như một mail proxy server hiệu suất cao. Mail context được xác định trong main context, bên ngoài http context.

Chức năng chính của context này là cung cấp khu vực để cấu hình một giải pháp mail proxy trên server. Khi đó, NGINX có thể chuyển hướng các request xác thức đến một server bên ngoài. Sau đó cung cấp quyền truy cập vào các mail server POP3 và IMAP. Bên cạnh đó, mail context cũng có thể được cấu hình để kết nối đến một SMTP Relayhost.

Dạng chung của mail context:


```node
# main context

events {
    # events context
}

mail {
    # mail context
}
```

### If Context

If context có thể được thiết lập để cung cấp xử lý các directive có điều kiện. Trong NGINX, context này sẽ thực hiện các câu lệnh nếu được trả về “true”, giống như trong lập trình.

If context trong NGINX được cung cấp bởi module rewrite, đồng thời cũng là mục đích sử dụng chính của nó. Vì NGINX kiểm tra các điều kiện của một request với nhiều directive có mục đích. Nên if không nên được sử dụng cho hầu hết các loại thực thi có điều kiện.

Vấn đề cơ đây cơ bản là thứ tự xử lý của NGINX thường dẫn đến các kết quả bất ngờ. Và nó dường như trái ngược hoàn toàn với ý nghĩa của một if block. Directive duy nhất đủ an toàn để sử dụng bên trong context này là `return` và `rewrite`.

Hầu hết if context được sử dụng trong location block. Cho nên chúng sẽ có dạng sau:


```node
# main context

http {
    # http context

    server {
        # server context

        location location_match {
            # location context

            if (test_condition) {
                # if context
            }
        }
    }
}
```

### Limit_except Context

Context này được sử dụng để giới hạn việc sử dụng các phương thức HTTP nhất định trong location context. Lấy ví dụ khi ta muốn chỉ vài client nhất định được truy cập vào nội dung POST. Tuy nhiên vẫn muốn mọi người được phép đọc các nội dung. Khi đó ta có thể sử dụng block `limit_except.`

Ví dụ trên sẽ có dạng như sau:


```html
. . .

# server or location context

location /restricted-write {
    # location context

    limit_except GET HEAD {
        # limit_except context

        allow 192.168.1.1/24;
        deny all;
    }
}
```

Theo ví dụ trên, khi gặp phải bất kỳ phương thức HTTP nào không được liệt kê trong context header, NGINX sẽ áp dụng của directive bên trong context (tức là hạn chế các truy cập). Kết quả của ví dụ này là bất kỳ client nào cũng có thể sử dụng GET, HEAD. Nhưng các phương thức khác chỉ có thể được thực hiện bởi client từ subnet `192.168.1.1/24.`

## Quy tắc chung trong Context, NGINX config

Trong phần cuối, ta sẽ tìm hiểu về cách để xử lý các context trong NGINX hiệu quả nhất.

### Áp dụng các directive trong context cao nhất có thể

Nhiều directive có thể được sử dụng trong nhiều hơn một context. Lấy ví dụ, một số directive có thể được sử dụng trong các context http, server, location. Vì vậy, ta có thể linh hoạt khi thiết lập các directive này.

Tuy nhiên, có một quy tắc chung trong việc này. Hãy luôn khai báo các directive trong context cao nhất có thể. Đồng thời, ghi đè chúng ở các context thấp hơn nếu cần thiết. Có nhiều lý do để sử dụng chiến thuật này:

Đầu tiên, nó tránh sự lặp lại không cần thiết giữa các context tương đương. Lấy ví dụ trên, khi mỗi location được khai báo trong cùng một document root:

Copy

```http
http {
    server {
        location / {
            root /var/www/html;
            . . .
        }

        location /another {
            root /var/www/html;
            . . .
        }
    }
}
```

Ta có thể đưa root ra server block. Hay thậm chí là ra http block:

Copy

```http
http {
    root /var/www/html;
    server {
        location / {
            . . .
        }

        location /another {
            . . .
        }
    }
}
```

Hầu hết thì server level sẽ là phù hợp nhất. Nhưng khai báo ở level cao hơn cũng có cái lợi của nó. Việc này không những cho phép đặt directive ở ít địa điểm hơn. Mà nó còn cho phép xếp tầng các giá trị mặc định xuống tất cả các yếu tố con, ngăn việc gặp lỗi nếu chẳng may quên một directive ở cấp thấp hơn. Thậm chí đây là một vấn đề lớn đối với các cấu hình dài hạn.

### Sử dụng nhiều context tương đương thay vì if logic trong processing

Khi muốn xử lý nhiều request khác nhau, phụ thuộc vào từng thông tin khác nhau của client, nhiều người thường sử dụng if context để điều hòa việc processing. Tuy nhiên, ta đã biết là có một số vấn đề với context này.

Đầu tiên, if directive thường trả về các kết quả không tương xứng với mong đợi của quản trị. Mặc dù processing trả về kết quả như nhau với các input sống nhau. Nhưng cách NGINX phiên dịch môi trường lại có nhiều khác biệt tương đối lớn.

Lý do thứ hai là hiện đã có nhiều directive được tối ưu hóa cho mục đích này. NGINX đã sử dụng một thuật toán lựa chọn phù hợp với mục đích này. Vì vậy, nếu có thể, hãy di chuyển các cấu hình khác nhau vào block của chúng. Khi đó thuật toán có thể xử lý logic process lựa chọn.

## Lời kết

Đến dòng này, chắc hẳn bạn đã nắm được nhiều kiến thức cơ bản về các context phổ biến của NGINX, NGINX config cũng như về các directive. Lời cuối cùng, hãy luôn kiểm tra tài liệu của NGINX để biết được các location cụ thể cho từng directive khác nhau. Cần thận trong việc khởi tạo các cấu hình. Khi đó, không nhưng độ bền bỉ mà cả hiệu suất đều được cải thiện đáng kể.


