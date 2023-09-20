# Container là gì? Đặc điểm kỹ thuật của Container
## Container là gì?

**Container** là một hình thức ảo hóa hệ điều hành, bên trong là các packages, một số **dependencies** (Thành phần phụ thuộc - giống dùng NodeJS khi khai báo file config ***package.json***). Dùng để giải quyết vấn đề chuyển giao phần mềm một cách đáng tin cậy giữa các môi trường khác nhau. **Docker container image** là một gói phần mềm nhẹ *(Tạm xem như 1 bản ghost hoặc file WinPE được nén lại)*, chạy độc lập và có thể thực thi bao gồm mọi thứ để chạy ứng dụng như: code, runtime, system tools, system libraries và settings mà không bị các yếu tố môi trường hệ thống làm ảnh hưởng và ngược lại.

![[Pasted image 20230907092907.png]]

**Container images** sẽ trở thành containers trong khi chạy. Và nếu đó là **Docker containers** – images trở thành container khi chúng chạy trên [[02-Docker - Tìm hiểu Docker cơ bản toàn tập|Docker]]. Có thể chạy trên cả Linux và Windows, Containerized Software sẽ luôn chạy giống nhau, bất kể hạ tầng nào. Chúng tách biệt với môi trường của nó và đảm bảo chúng sẽ hoạt động đồng nhất mặc dù trong quá trình phát triển hay staging.

## Đặc điểm của Container

Các thành phần trong cấu trúc của Container gồm: [[Server]] là thành phần chính (máy chủ vật lý hoặc máy chủ ảo), host OS (hệ điều hành được cài đặt trên server) và các container. Mỗi ứng dụng đều có sự phụ thuộc riêng về phần mềm và cả phần cứng.

Với những ứng ứng dụng này sẽ được Container (công nghệ ảo hóa) được cài đặt trên host OS và đóng gói thành các container. Process trong một container bị cô lập với các process của các container trong hệ thống, nhưng các container đều chia sẻ [[Kernel - Các chức năng của Kernel | Kernel]] của host OS.

## Các định dạng Container tiêu chuẩn

Năm 2015, công ty CoreOS đã sản xuất một phần mềm container riêng cho mình là App Container Image (ACI). Đây là phần mềm có sự khác biệt đối với Docker containers đã ra mắt trước đó. Tuy nhiên phần mềm này có xu hướng phân mảnh đối với định dạng Linux containers.

1 năm sau, một dự án container mở đã được khởi động với tên gọi Open Container Initiative (OCI). Đây là dự án được phát triển dưới sự quản lý của Linux Foundation. Mục đích chính của OCI là phát triển một tiêu chuẩn chung cho các định dạng container và một phần mềm container runtime cho tất cả các nền tảng.

Điểm xuất phát của các tiêu chuẩn OCP là công nghệ Docker và phần mềm này đã dành tặng khoảng 5% codebase để bắt đầu phát triển dự án. Ngoài ra, dự án này còn có sự góp mặt của các nhà tài trợ khác như AWS, Google, Microsoft, IBM, HP, VMware, Oracle, Twitter, Red Hat, Docker và CoreOS.

## Lợi ích của Container

Những lợi ích nổi bật mà container mang lại cho doanh nghiệp là:

- **Kích thước nhỏ gọn**: Một container chỉ có kích thước khoản mấy chục MB. Trong khi đó kích thước của một virtual machines chứa toàn bộ hệ điều hành riêng có thể lên tới vài GB. Vì vậy nếu sử dụng container thì máy chủ của doanh nghiệp có thể lưu trữ nhiều hơn so với sử dụng virtual machines.
- **Khởi động ngay lập tức**: Các ứng dụng được chứa trong container có thể được khởi tạo ngay lập tức. Điều này giúp lập trình viên có thể sử dụng container “đúng lúc” và giải phóng dung lượng ngay khi không cần thiết nữa.
- **Cho phép module hóa hệ thống với quy mô lớn:** Trong quá trình container hóa, ứng dụng có thể được phân chia thành nhiều module (như cơ sở dữ liệu, giao diện người dùng,…). Điều này giúp việc quản lý và thay đổi các ứng dụng dễ dàng hơn. Đồng thời các container cũng rất nhẹ nên module riêng lẻ có thể được khởi tạo ngay lập tức mỗi khi cần thiết.

## Hệ thống quản lý Container mã nguồn mở miễn phí

Hệ thống quản lý Container mã nguồn mỡ miễn phí phổ biến và được nhiều người sử dụng nhất hiện nay là Kubernetes. Đây là một nền tảng được phát triển bởi Google. Hệ thống này cung cấp các cơ chế triển khai, duy trì và mở rộng các ứng dụng đã được container hóa.

## Những giải pháp quản lý Container

Nhìn chung, Docker Enterprise Edition là giải pháp quản lý Container được nhiều doanh nghiệp lựa chọn nhất hiện nay. Đây nền tảng tích hợp, đã được kiểm tra và chứng nhận cho các ứng dụng chạy trên hệ điều hành Linux hoặc Windows hoặc các nhà cung cấp dịch vụ đám mây.

Bên cạnh đó, một số giải pháp quản lý container khác nhận được nhiều sự chú ý là:

- **CoreOS’s Tectonic:** Nền tảng này sẽ đóng gói trước tất cả các nguồn mở cần thiết để xây dựng cơ sở hạ tầng giống như Google. Đồng thời hệ thống này cũng bổ sung thêm các tính năng thương mại khác như bảng quản lý, tích hợp SSO của doanh nghiệp và Quay.io (cung cấp container registry có sẵn).
- **Red Hat:** Là một nền tảng quản lý container tại chỗ. Red Hat được xây dựng với cốt lõi là container ứng dụng của Docker và theo sự điều phối, quản lý của Kubernetes trên nền tảng của Red Hat Enterprise Linux.
- **Rancher Labs:** Đây là giải pháp quản lý container với mã nguông mở được thiết kế giúp lập trình viên dễ dàng triển khai và quản lý các container trên bất cứ cơ sở hạ tầng nào.

## Bảo mật cho Container

Nhiều người cho rằng hệ thống bảo mật của container không an toàn bằng Virtual Machines. Nguyên nhân là bởi hacker có thể lợi dụng lỗ hổng trong hạt nhân kernel để đi tới các container đang nằm trong máy chủ này.

Tuy nhiên điều này cũng có thể xảy ra với hypervisor – phần mềm giám sát máy ảo. Nhưng vì hypervisor cung cấp ít chức năng hơn hạt nhân kernel Linux nên quy mô tấn công sẽ nhỏ hơn rất nhiều.

Trong những năm gần đây, các nhà sản xuất phần mềm đã rất nỗ lực để phát triển nhiều phần mềm tăng cường bảo mật cho container. Trong đó có thể kể đến một số giải pháp sau:

- Đầu tiên và điển hình nhất có thể kể đến Docker (và các đối tác) hiện đang cung cấp cơ sở hạ tầng cho phép quản trị viên đánh dấu container. Tính năng này sẽ giúp ngăn chặn việc triển khai các container không an toàn. Tuy nhiên vẫn có những trường hợp tồn tại lỗ hổng phần mềm trong các container đã được đánh dấu. Vì vậy Docker và các đối tác đã phát triển thêm giải pháp quét bảo mật để thông báo cho quản trị viên khi xuất hiện hình ảnh bất cứ lỗ hổng nào trong container.

![[Pasted image 20230907093215.png | 500]]

Docker và các đối tác giúp bảo mật container hiệu quả

- Phần mềm bảo mật container do Twistlock cũng là giải pháp hữu ích để giải quyết vấn đề trên. Phần mềm này cung cấp cấu hình hành vi dự kiến của container, danh sách “whitelists”, các hoạt động kết nối và thậm chí các phương pháp lưu trữ nhất định để có thể ngăn chặn và gắn cờ cho mọi hoạt động độc hại hoặc không mong muốn.
- Phần mềm do công ty Polyverse phát triển gia tăng bảo mật cho container dựa trên đặc tính các ứng dụng nằm trong container có thể khởi động ngay lập tức. Cụ thể, sau khi xác định một container là an toàn, ứng dụng sẽ được khởi chạy lại ngay trên đó. Điều này giúp giảm thiểu tối đa thời gian mà hacker có thể khai thác để tấn công vào một ứng dụng đang chạy trong một container.

## Phiên bản Linux phù hợp để chạy Container

Hầu hết các phiên bản của Linux đều có nhiều tính năng không cần thiết nếu người dùng chỉ sử dụng Linux như một máy chủ để chạy container. Vì vậy một số phiên bản Linux đã được đặc biệt thiết kế để chạy container như:

- **Container Linux** (trước đây là CoreOS Linux): Đây là một trong những hệ điều hành container với kích thước nhẹ đầu tiên được xây dựng để chạy container.
- **RancherOS** : Đây là một phiên bản Linux đơn giản được xây dựng từ các container và đặc biệt dùng để chạy container.
- **Photon OS**: Đây là phiên bản lưu trữ container Linux mini được tối ưu hóa để chạy trên nền tảng VMware.
- **Project Atomic Host** : Đây là hệ điều hành container với kích thức nhẹ của Red Hat với nhiều phiên bản trên CentOS và Fedora. Tuy nhiên cũng có một phiên bản trong Red Hat Enterprise Linux.
- **Ubuntu Core**: Đây là phiên bản Ubuntu nhỏ nhất. Ubuntu Core được thiết kế như một hệ điều hành máy chủ cho các thiết bị IoT và có thể triển khai cloud container với quy mô lớn.

## Phiên bản Windows phù hợp để chạy Container

Năm 2016, Microsoft đã bắt đầu phát triển khả năng chạy Windows container trong Windows Server 2016 và Windows 10. Đã có nhiều Docker containers được thiết kế dành riêng cho Windows và chúng có thể được quản lý thông qua bất cứ tài khoản Docker nào hoặc từ PowerShell của Microsoft.

Windows container có thể được khởi chạy trên phiên bản standard của Windows Server 2016, phiên bản streamlined của Server Core hoặc phiên bản Nano Server (phiên bản đặc biệt được thiết kế để chạy các ứng dụng bên trong container hoặc virtual machines.

Ngoài ra, Microsoft cũng giới thiệu thêm Hyper-V container. Đây là Windows container chạy trong Hyper-V virtual machine để gia tăng thêm tính cô lập.

## So sánh Containers và Virtual Machines

Khi bạn đã hiểu được Container là gì thì việc so sánh và phân biệt sẽ trở nên dễ dàng hơn. Nhưng dưới đây sẽ mô tả sâu hơn về khía cạnh hoạt động hơn.

**Containers** và **virtual machines** đều cô lập tài nguyên và phân bổ tài nguyên. Nhưng chúng có cách hoạt động khác nhau vì container ảo hóa hệ điều hành thay vì phần cứng và có tính linh động và hiệu quả hơn.

### Về Containers

![[Pasted image 20230907093252.png | 600]]



Mô hình hoạt động của Container

Là lớp abstraction tại app layer. Nhiều container có thể chạy trên cùng một máy và chia sẻ OS kernel với các container khác. Mỗi container sẽ được cô lập riêng trong user space. Container chiếm ít không gian hơn VMs (container images thường có kích thước chỉ hàng chục MBs). Chúng có thể xử lý nhiều ứng dụng hơn và yêu cầu ít hơn VMs hệ điều hành.

### Về Virtual Machines

![[Pasted image 20230907093335.png | 600]]

Hoạt động của Virtual Machines

Virtual machines (VMs) là lớp abstraction của phần cứng vật lý, chia một server thành nhiều server hơn. [[Hypervisor]] cho phép nhiều VMs chạy trên một máy chủ. Mỗi VM là như là một hệ điều hành đầy đủ – chiếm hàng chục GBs và VMs khởi động chậm hơn.

Container và VMs có thể được sử dụng cùng nhau để cung cấp tính linh hoạt trong việc triển khai, quản lý ứng dụng, hạ tầng.

## Kết hợp giữa Container và Virtual Machine

Container và Virtual Machine có thể được kết hợp sử dụng cùng nhau để cung cấp thêm nhiều tính năng triển khai và quản lý ứng dụng mới.

![[Pasted image 20230907093354.png]]
## Lời kết

Hy vọng bài viết trên cung cấp cho bạn cái nhìn tổng quan, giúp bạn hiểu hơn về **Container là gì** và phân biệt được container với virtual machine. Chúc bạn có thể áp dụng thành công.

_**Vietnix tổng hợp**_