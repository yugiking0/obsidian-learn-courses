# GÁN GIÁ TRỊ CHO BIẾN

Các bạn hãy tưởng tượng biến như một chiếc hộp và giá trị gán cho biến như là đồ vật được bỏ vào hộp. Vì vậy ta có thể đặt bất cứ giá trị gì vào hộp và ta cũng có thể thay thế chúng nếu muốn:

<!-- prettier-ignore -->
```js
var fullName; // tạo chiếc hộp

fullName = 'Sơn Đặng'; // cho đồ vật vào hộp

fullName = 'Nguyễn Văn A'; // thay thế đồ vật khác

alert(fullName); // Nguyễn Văn A
```

> Khi giá trị của biến được thay đổi, giá trị cũ sẽ bị xóa khỏi biến.

Ta cũng có thể sao chép giá trị từ biến này sang biến khác:

<!-- prettier-ignore -->
```js
var currentCourse = 'Javascript';

var newCourse;

// copy giá trị 'Javascript' từ biến
// 'currentCourse' sang biến 'newCourse'
newCourse = currentCourse;

// bây giờ, biến 'newCourse' và 'currentCourse'
// đều có giá trị là 'Javascript'

alert(currentCourse); // Javascript

alert(newCourse); // Javascript
```

> Có thể bạn chưa biết có những ngôn ngữ lập trình như Scala, Erlang không cho phép thay đổi giá trị của biến đã định nghĩa. Ta bắt buộc phải tạo biến mới khi cần lưu giá trị và không thể gán lại giá trị cho biến cũ.

## Đặt tên biến như nào cho đúng?

Đặt tên biến hợp lệ theo quy tắc của Javascript là việc đơn giản, tuy nhiên trong thực tế đặt tên biến không chỉ dừng lại ở việc đặt cho hợp lệ mà ta còn phải quan tâm tới các yếu tố khác như:

1. Tên biến phải có ý nghĩa cụ thể, phải rõ ràng và thể hiện được nó đang lưu trữ cái gì.
2. Sử dụng tiếng Anh để đặt tên biến, sử dụng các từ có thể đọc lên được như userName, phoneNumber, verifyEmail, …
3. Tránh đặt tên biến ngắn như a, b, p trừ khi bạn chỉ đang làm ví dụ hoặc bạn thật sự hiểu trường hợp đó có thể đặt tên như vậy.
4. Tránh đặt tên biến chung chung kiểu như data, value. Vì khi nhìn vào không thể hiểu data là data của cái gì, value là value của cái gì. Chỉ sử dụng tên dạng này khi đang trong ngữ cảnh cụ thể giúp bổ nghĩa cho những từ chung chung đó.

### Đặt tên biến chung chung (trường hợp nên tránh)

Ví dụ:

<!-- prettier-ignore -->
```js
var data = '...'; // không biết data là data của cái gì
var value = '...'; // không biết value là value của cái gì

// var documentData = '...' ; Nên đặt rõ ràng ra như này
// var documentValue = '...'; và như này
```

### Đặt tên biến chung chung (trường hợp nên dùng)

Ví dụ:

<!-- prettier-ignore -->
```js
function Document() {
     var data = '...';
    // hoặc
     var value = '...';
     
    // var documentValue = '...'; Đặt như này sẽ bị lặp lại chữ "document" không cần thiết
}
```

Bạn chưa cần quan tâm function là gì vì ta sẽ học nó ở những bài sau. Trong trường hợp này biến data hoặc value nằm trong Document. Vì vậy Document đã giúp lập trình viên khi nhìn vào hiểu được data, value là thuộc về Document. Trong trường hợp này thì tên biến giúp đơn giản hóa và vẫn truyền đạt được đầy đủ ý nghĩa.

---

## Có thể bạn chưa biết

1. Đặt tên biến là một trong những kỹ năng quan trọng và phức tạp nhất trong lập trình. Nhìn lướt qua các tên biến có thể biết code nào được viết bởi người mới và người đã có nhiều kinh nghiệm.

2. Trong thực tế nhiều khi chúng ta phải làm việc trên code đã có sẵn thay vì viết hoàn toàn mới. Có khi bạn sẽ làm việc trên code cũ của người khác và ngược lại. Vì vậy đặt tên biến rõ ràng, dễ hiểu, truyền đạt đúng mục đích sử dụng là quan trọng hơn cả.

3. Chỉ sau vài tháng bạn có thể quên đi đoạn mã do chính tay mình viết. Để chính bạn hiểu bạn đã từng code cái gì trong quá khứ thì việc đặt tên biến tuân thủ các nguyên tắc trên là vô cùng quan trọng.

4. Khi phải lựa chọn giữa performance (hiệu năng) và clean code (code sạch) người ta thường lựa chọn clean code. Việc đánh đổi này là cần thiết để giúp code dễ hiểu, dễ bảo trì và nâng cấp về sau. Và đặt tên biến chính là một trong những yếu tố giúp code của bạn trở nên clear hơn.

> Fact: Code cho máy hiểu thì dễ, code cho người hiểu mới khó!
