# Kernel là gì? Các chức năng của Kernel
---
**Kernel** là một chương trình máy tính, trái tim và cốt lõi của Hệ điều hành. Do Hệ điều hành có quyền kiểm soát hệ thống nên Kernel cũng có quyền kiểm soát mọi thứ trong hệ thống. Đây là phần quan trọng nhất của Hệ điều hành.

## Kernel là gì?

Bất cứ khi nào một hệ thống khởi động. Kernel là chương trình đầu tiên được tải sau boot loader vì Kernel phải xử lý phần còn lại của hệ thống cho [hệ điều hành]. Kernel vẫn còn trong bộ nhớ cho đến khi Hệ điều hành bị tắt.

![Kernel là gì?](https://static-xf1.vietnix.vn/wp-content/uploads/2022/09/kernel-la-gi-1024x808.webp)

*Kernel là gì?*

Kernel chịu trách nhiệm cho các tác vụ cấp thấp. Như quản lý đĩa, quản lý bộ nhớ, quản lý tác vụ,… Kernel cung cấp giao diện giữa người dùng và các thành phần phần cứng của hệ thống. Khi một tiến trình thực hiện một yêu cầu tới Kernel, thì nó được gọi là System Call.

Một Kernel Space được bảo vệ là một vùng bộ nhớ riêng biệt. Và khu vực này không thể truy cập được bởi các chương trình ứng dụng khác. Vì vậy, code của Kernel được tải vào Kernel Space được bảo vệ này. Ngoài ra, bộ nhớ được sử dụng bởi các ứng dụng khác được gọi là User Space. Vì đây là hai không gian khác nhau trong bộ nhớ, nên giao tiếp giữa chúng chậm hơn một chút.

## Chức năng của Kernel là gì?

Sau khi tìm hiểu khái niệm về Kernel, tiếp đến dưới đây là chức năng chính của nó:

### Đối với hệ điều hành

Nói dễ hiểu, Kernel giống như một dịch giả (translator). Nó thực hiện chuyển đổi những yêu cầu đầu vào / đầu ra của phần mềm một tập lệnh dành cho CPU và GPU. Nó giống như một lớp nằm ở giữa phần mềm cùng phần cứng giúp mọi thứ vận hành trơn tru. Kernel quản lý:

- **Truy cập tài nguyên máy tính:** Kernel có thể truy cập các tài nguyên máy tính khác nhau. Như [CPU](https://vietnix.vn/cpu-la-gi/), thiết bị I/O và các tài nguyên khác. Nó hoạt động như một cầu nối giữa người dùng và tài nguyên của hệ thống.
- **Quản lý tài nguyên:** Nhiệm vụ của Kernel là chia sẻ tài nguyên giữa các process khác nhau.
- **Quản lý bộ nhớ:** Mỗi process cần một số không gian bộ nhớ. Vì vậy, bộ nhớ phải được phân bổ và truy cập để hoạt động. Tất cả những tác vụ quản lý bộ nhớ này được thực hiện bởi Kernel.
- **Quản lý thiết bị:** Các thiết bị ngoại vi được kết nối trong hệ thống được sử dụng bởi các process. Vì vậy, việc phân bổ các thiết bị này được quản lý bởi Kernel.

Theo đó, người dùng được phép truy cập không gian Kernel bằng việc áp dụng những cuộc gọi hệ thống (system call). Trong trường hợp một chương trình truy cập trực tiếp quá nhiều lần sẽ dẫn đến tình trạng lỗi.

### Đối với bảo mật và Bảo vệ

Ngoài ra, Kernel cũng có chức năng bảo vệ phần cứng. Trong trường hợp không có sự bảo vệ này của Kernet thì những chương trình có thể thực hiện tác vụ trên máy tính một cách tùy ý và lộn xộn. Từ đó sẽ làm cho máy tính và dữ liệu của bạn bị hỏng.

Trong các máy tính hiện đại, bảo mật được thực hiện ở cấp độ phần cứng. Ví dụ: Windows sẽ không tải driver từ nguồn không đáng tin cậy và được chứng nhận bằng chữ ký. Secure Boot và Trusted Boot cũng là một minh chứng cụ thể cho ví dụ này.

**Secure Boot (Khởi động an toàn)**

Khởi động an toàn là một tiêu chuẩn bảo mật do những thành viên của ngành công nghiệp máy tính PC phát triển. Nó hỗ trợ người dùng bảo vệ hệ thống tránh khỏi những chương trình độc hại, thông qua việc không cho ứng dụng trái phép nào vận hành trong thời gian khởi động hệ thống.

Nhờ có tính năng này mà khi máy tính của bạn khởi động chỉ sử dụng những phần mềm uy tín và được nhà sản xuất tin cậy. Theo đó, khi máy tính bắt đầu khởi động, [firmware](https://vietnix.vn/firmware-la-gi/) tiến hành kiểm tra chữ ký của những phần mềm khởi động như firmware driver (ROM tùy chọn) cùng hệ điều hành.

Sau khi hoàn tất việc xác minh chữ ký, máy tính của bạn sẽ khởi động và firmware làm nhiệm vụ kiểm soát hệ điều hành.

**Trusted Boot** **(Khởi động đáng tin cậy)**

Trusted Boot dùng Mô-đun nền tảng tin cậy ảo (VTPM) để thực hiện xác minh chữ ký số của Kernel Windows 10 trước khi được tải xuống. Mặt khác, nó xác nhận tất cả thành phần khác nằm trong quy trình khởi động Windows, ví dụ như: Driver khởi động, tập tin khởi động và ELAM. 

Trong trường hợp, tập tin bị thay đổi (dù ở mức độ nào) bộ nạp khởi động sẽ ngay lập tức phát hiện vàtừ chối tải nó, thông qua việc nhận ra nó là thành phần bị lỗi. Qua đó có thể thấy nó cung cấp một chuỗi tin cậy đến mọi thành tố được sử dụng khi khởi động.

## Kernel Mode và User Mode

Có một số lệnh nhất định chỉ nên thực thi bằng Kernel. Vì vậy, CPU chỉ thực hiện các lệnh này trong Kernel Mode. Ví dụ, quản lý bộ nhớ chỉ nên được thực hiện trong Kernel Mode. Khi ở Chế độ người dùng, CPU sẽ thực thi các process do người dùng đưa ra trong User space.

## Các loại Kernel

Nói chung, có năm loại Kernel. Hãy cùng tìm hiểu xem các loại Kernel là gì và tính năng nổi bật của chúng.

### 1. Monolithic Kernels

[Monolithic Kernels](https://vi.wikipedia.org/wiki/Monolithic) là những Kernel mà các user service và kernel service được triển khai trong cùng một không gian bộ nhớ, tức là bộ nhớ khác nhau cho các user service, và kernel service không được sử dụng trong trường hợp này. Bằng cách đó, kích thước của Kernel được tăng lên và điều này sẽ làm tăng kích thước của Hệ điều hành. Vì không có User space và Kernel space riêng biệt, nên việc thực thi process sẽ nhanh hơn trong Monolithic Kernels.

Copy

```plain
<div style="text-align: justify;">
<figure><img class="alignnone size-full wp-image-3373 aligncenter" src="https://vietnix.vn/wp-content/uploads/2021/02/kernel-la-gi1.png" alt="" width="246" height="266"></figure><p></p>
</div>
```

**Ưu điểm:**

- Nó cung cấp CPU Scheduler, Memory Scheduler, File Management thông qua System Call.
- Việc thực thi process diễn ra nhanh chóng vì không có không gian bộ nhớ riêng cho User và Kernel.

**Nhược điểm:**

- Nếu bất kỳ dịch vụ nào thất bại, đều sẽ dẫn đến lỗi hệ thống.
- Nếu các dịch vụ mới được thêm vào thì toàn bộ hệ điều hành cần được sửa đổi.

### 2. Microkernel

Một Microkernel khác với kernel Monolithic vì trong Microkernel, các dịch vụ người dùng và dịch vụ kernel được triển khai vào các không gian khác nhau. Vì sử dụng riêng User space và Kernel space, do đó, điều này làm giảm kích thước của Kernel và làm giảm kích thước của hệ điều hành.

Copy

```plain
<div style="text-align: justify;">
<figure><img class="size-full wp-image-3374 aligncenter" src="https://vietnix.vn/wp-content/uploads/2021/02/kernel-la-gi2.png" alt="" width="301" height="221"></figure><p></p>
</div>
```

Vì bạn đang sử dụng các không gian khác nhau cho các user service và kernel service, do đó việc liên lạc giữa ứng dụng và dịch vụ được thực hiện với sự trợ giúp của IPC và điều này sẽ làm giảm tốc độ thực hiện.

**Ưu điểm:**

- Nếu các dịch vụ mới được thêm vào thì có thể dễ dàng thêm vào.

**Nhược điểm:**

- Vì chúng ta đang sử dụng User space và Kernel space riêng biệt, do đó, giao tiếp giữa chúng có thể giảm thời gian thực hiện chung.

### 3. Hybrid Kernel

Hybrid Kernel là sự kết hợp của cả Microkernel và Monolithic Kernel. Nó sử dụng tốc độ của Monolithic Kernels và tính mô đun của Microkernel.

**Ưu điểm:**

- Được kết hợp từ Hybrid Kernel và Monolithic Kernel.

**Nhược điểm:**

- Vẫn tương tự như Monolithic Kernel.

### 4. Nanokernel

Trong một Nanokrnel, như tên cho thấy, toàn bộ mã của kernel rất nhỏ, tức là mã thực thi trong chế độ đặc quyền của phần cứng là rất nhỏ.

**Ưu điểm:**

- Nó cung cấp trựu tượng phần cứng (hardware abstractions) mà không có dịch vụ hệ thống.

**Nhược điểm**:

- Tương đối giống Microkernel nên ít được sử dụng hơn.

### 5. Exokernel

Exokernel là một nhân hệ điều hành được phát triển bởi song song MIT và nhóm Hệ điều hành phân tán. Ở loại Kernel này, việc bảo vệ tài nguyên được tách ra khỏi quản lý và do đó, điều này dẫn đến việc cho phép chúng ta thực hiện các tùy chỉnh dành riêng cho ứng dụng.

**Ưu điểm:**

- Có ít trừu tượng phần cứng nhất (hardware abstractions).

**Nhược điểm:**

- Có nhiều việc hơn cho các lập trình viên.

## Lời kết

Hy vọng bài viết trên sẽ giúp bạn hiểu hơn về Kernel là gì? Nếu có thắc mắc hay đóng góp ý kiến, mời bạn để lại bình luận phía dưới bài viết này. Vietnix xin chân thành cảm ơn bạn!