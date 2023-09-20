# Hypervisor
---

**Hypervisor** là chương trình dùng để quản lý các máy ảo phổ biến trên thế giới hiện nay. Bài viết này sẽ cho biết cụ thể **Hypervisor là gì**. Bên cạnh đó là phân loại và ví dụ về Hypervisor.

Hypervisor được tạo ra vào năm 1965 để làm việc với IBM RPQ cho IBM 360/65. Ban đầu chúng được thiết kế để kiểm tra hệ thống chia sẻ giữa các máy ảo. Đồng thời xem xét các khái niệm hardware mới mà không gây nguy hiểm cho hệ thống sản xuất chính. Hiện nay, hypervisor thường được sử dụng để phân bổ tài nguyên phần cứng vật lý cho các máy ảo. Chúng được gọi là “guest” trên máy host.

Hypervisor được sử dụng cho nhiều tác vụ khác nhau. Trong đó bao gồm cả điện toán đám mây và quản lý server. Hay chỉ đơn giản là chạy các chương trình tương thích với hệ điều hành mà bạn không có. Bạn có thể sử dụng Hypervisor để chạy các quy trình và hệ điều hành trên máy ảo. Chúng hoàn toàn tách biệt với hệ thống chính của bạn.

Sau đây, tôi sẽ giải thích Hypervisor là gì. Đồng thời giải thích tại sao cách hoạt động của nó rất quan trọng trong quản lý hiệu suất hệ thống, giám sát bảo mật cũng như việc tối ưu hóa network và hardware của bạn.

## **Hypervisor là gì?**

![Hypervisor là gì?](https://www.dnsstuff.com/wp-content/uploads/2019/10/what-is-hypervisor-1024x536.jpg)

Hypervisor là hardware, software, hoặc [firmware](https://vietnix.vn/firmware-la-gi/) có khả năng tạo ra các máy ảo. Sau đó quản lý và phân bổ các tài nguyên cho chúng. Máy ảo là máy được thiết lập để sử dụng host machine. Bạn có thể chia các resources này bao nhiêu lần tùy thích để chứa các “guest” máy ảo cần thiết. (Nếu bạn đã nghe đến thuật ngữ ” virtual machine monitor”, bạn có thể tò mò về sự khác biệt giữa virtual machine monitor và hypervisor. Thật ra chúng giống nhau.)

Ví dụ, bạn có một PC với 8GB RAM và hệ điều hành Windows. Nếu muốn chạy các chương trình yêu cầu [Linux](https://vietnix.vn/linux-la-gi/), bạn có thể tạo một máy ảo chạy Linux. Sau đó sử dụng trình Hypervisor để quản lý tài nguyên của nó. Chẳng hạn như phân bổ cho nó 2GB RAM. Một số tài nguyên của máy host sẽ chạy HĐH Windows và một số resources sẽ được phân bổ cho máy ảo chạy Linux.

## **Hypervisor hoạt động như thế nào?**

Hypervisor và bộ sưu tập máy ảo được sử dụng cho nhiều tác vụ khác nhau trong môi trường kinh doanh bao gồm [data replication](https://www.manageengine.com/device-control/data-replication.html), server consolidation, desktop virtualization, và cloud computing

Thông thường, khi bạn muốn sao chép một máy ảo, bạn phải sao chép toàn bộ dung lượng của nó theo cách thủ công. Sử dụng hypervisor, bạn chỉ cần chọn máy ảo và các bộ phận mà bạn muốn sao chép. Sau đó, nó sẽ thực hiện quy trình cho bạn.

Nếu bạn có một doanh nghiệp có nhiều server hoạt động các dịch vụ khác nhau cho khách hàng qua internet, thì việc quản lý tập trung tất cả chúng có thể trở nên khó khăn. Đặc biệt nếu chúng chạy các hệ điều hành khác nhau. Một hypervisor cho phép bạn ảo hóa các server này. Sau đó quản lý tất cả chúng trong một physical machine, để chúng hoạt động hiệu quả hơn. Nói một cách đơn giản, bạn có thể phân bổ resources cho tất cả các máy. Từ đó có thể sử dụng tốt hơn tổng tài nguyên vật lý mà bạn có sẵn, thay vì để chúbng ở chế độ chờ khi không sử dụng.

Desktop virtualization rất hữu ích khi bạn muốn sử dụng một phần mềm tương thích với một hệ điều hành (Windows), nhưng bạn có hệ điều hành khác (MacOS), trên máy của mình. Với hypervisor, bạn có thể thiết lập một máy ảo Windows để chạy software mà không cần phải thay đổi HĐH.

## Ứng dụng của hypervisor là gì?

Một trong những lợi ích chính của việc chạy máy ảo là nếu một trong số chúng gặp sự cố, nó sẽ không ảnh hưởng đến các máy ảo khác. Nó cũng không ảnh hưởng phần cứng vật lý chính hay HĐH. Bởi vì, mặc dù chúng sử dụng cùng một phần cứng vật lý. Nhưng chúng tách biệt với nhau về mặt logic.

Một lý do khác để sử dụng hypervisor và các máy ảo đi kèm là vì mục đích bảo mật. Nó tạo ra một lớp khác giữa hệ điều hành của bạn và bất kỳ file nào. Chúng có thể có vấn đề khi bạn đang tải xuống hoặc truy cập từ internet. Ngay cả khi quá trình tải xuống gây ra sự cố trong máy ảo của bạn, hệ điều hành chính của bạn sẽ được bảo vệ bởi hypervisor.

## **Các loại Hypervisor**

![](https://static-xf1.vietnix.vn/wp-content/uploads/2021/03/Types-of-Hypervisors-1024x536-1.jpg)

Có hai loại hypervisor chính:

1. Native hoặc “bare metal” hypervisors
2. Hosted hoặc “embedded” hypervisors

Một bare metal hypervisor được cài đặt trực tiếp trên hardware của máy tính của bạn. Một hypervisor được lưu trữ được cài đặt trên hệ điều hành của bạn.

Các bare metal hypervisor thường nhanh hơn và hiệu quả hơn. Vì chúng có quyền truy cập trực tiếp vào hardware và không cần phải đi qua lớp hệ điều hành. Và chúng không phải cạnh tranh với các ứng dụng khác hoặc HĐH. Nên có thể sử dụng tất cả sức mạnh phần cứng vật lý hiện có và phân bổ nó cho các máy ảo. Chúng cũng thường an toàn hơn, bởi vì không có hệ điều hành trên host. Nên có ít khả năng tấn công hơn đối với những kẻ xâm nhập độc hại.

Tuy nhiên, hypervisor thiết lập và chạy dễ dàng hơn nhiều. Vì bạn có thể sử dụng HĐH thân thiện với người dùng hơn. Chúng thường được sử dụng cho mục đích thử nghiệm và phát triển. Sỡ vì chúng có thể chạy trên HĐH để thử các chương trình hoặc tính năng mới mà không ảnh hưởng đến HĐH.

VMware và Hyper-V là hai ví dụ chính về hypervisor. Với VMware thuộc sở hữu của Dell và Hyper-V do Microsoft tạo ra. VMware software được tạo ra cho cloud computing và ảo hóa, và nó có thể cài đặt một hypervisor trên các physical machine của bạn để cho phép nhiều máy ảo chạy cùng một lúc. Hyper-V làm điều tương tự, nhưng bạn cũng có thể ảo hóa các server. Hyper-V được cài đặt sẵn Windows 10. Cả hai đều là các bare metal (native) hypervisors. Oracle VM VirtualBox là một hosted hypervisor.

## **Phần mềm tốt nhất để quản lý Hypervisor là gì?**

Bạn nên sử dụng phần mềm quản lý hypervisor của bên thứ ba để đảm bảo hypervisor và các máy ảo của bạn hoạt động bình thường. Lựa chọn yêu thích của tôi là SolarWinds Virtualization Manager (VMAN). Tại sao? Công cụ này cung cấp một cái nhìn toàn diện về Hyper-V và VMWare của bạn song song với nhau. Nó cho bạn thấy cách ảo hóa của bạn được kết nối với các ứng dụng, các server và bộ nhớ.

![Hypervisor là gì?](https://www.dnsstuff.com/wp-content/uploads/2019/10/VMAN.jpg)

VMAN cũng cho bạn thấy những kết nối này đang hoạt động như thế nào và cung cấp cho bạn thông tin về capacity planning cũng như các đề xuất tối ưu hóa. Sau đó, Virtualization Manager cho phép bạn khắc phục sự cố máy ảo bằng cách sử dụng tính năng PerfStack ™ độc quyền. Nó hiển thị cho bạn các vấn đề về hiệu suất và cách chúng tương quan với nhau. Từ đó giúp bạn khám phá nguyên nhân gốc rễ dễ dàng hơn.

Một tính năng hữu ích khác mà nó cung cấp là quản lý tích hợp. Có nghĩa là bạn không cần đăng nhập và làm việc thông qua hypervisor. Vì mục đích bảo mật, công cụ này cũng bao gồm tính năng giám sát và cảnh báo được tích hợp sẵn. Nhằm giúp đảm bảo hypervisor của bạn không bị xâm phạm. Phần tốt nhất? Bạn có thể tự mình dùng thử công cụ này với bản dùng thử miễn phí, đầy đủ chức năng trong 30 ngày.

## Lời kết

Hypervisor đã xuất hiện từ lâu, nhưng với việc sử dụng ngày càng nhiều cloud computing, tầm quan trọng của chúng ngày càng rõ ràng hơn. Đảm bảo hypervisor của bạn được thiết lập chính xác và hoạt động bình thường là rất quan trọng để giữ cho máy ảo của bạn hoạt động hiệu quả. Cùng với đó là để quản lý việc sử dụng resource và duy trì bảo mật thiết bị. Để làm điều này, tôi khuyên bạn nên sử dụng trình giám sát của bên thứ ba như Virtualization Manager để có được bức tranh toàn cảnh về hiệu suất máy ảo của bạn.