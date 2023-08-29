# CÚ PHÁP COMMENTS

## Giới thiệu

Hầu hết các ngôn ngữ lập trình đều có cú pháp dành cho việc comment code. Trình biên dịch sẽ bỏ qua những dòng và khối comment trong code của bạn. Vì vậy comment mang mục đích để lập trình viên có thể chú thích code mà không ảnh hưởng tới việc thực thi của ngôn ngữ lập trình.

---

## Cú pháp

## Comment trên một dòng

Chúng ta sẽ sử dụng 2 dấu gạch chéo `//` trước comment. Cú pháp như sau:

<!-- prettier-ignore -->
```js
// [Nội dung comment]
```

Áp dụng:

<!-- prettier-ignore -->
```js
// Hàm alert sẽ bật lên hộp thoại
// trên trình duyệt
alert('Học lập trình tại F8');
```

Hoặc sử dụng ở phía sau dòng code:

```js
var userName = "sondn"; // Gán 'sondn' cho userName
```

---

## Comment nhiều dòng - một khối

Cú pháp:

<!-- prettier-ignore -->
```js
/* [Nội dung comment] */

// hoặc

/*
[Nội dung comment]
*/
```

Áp dụng:

<!-- prettier-ignore -->
```js
/**
Ở bài trước chúng ta đã học về biến
Và hôm nay chúng ta học về comment
*/

var fullName;
var age;
```

> Bất cứ nội dung gì nằm giữa ký tự **`/*`** và **`*/`** sẽ là comment.

---

## Sử dụng khi nào?

Chúng ta sử dụng comment với 2 mục đích chính:

### 1. Mục đích chú thích code

Chúng ta sẽ chú thích trên các đoạn code để hướng dẫn cách sử dụng, mô tả cách hoạt động hoặc giải thích tại sao ta lại làm như vậy. Việc làm này thường áp dụng đối với những đoạn code phức tạp, với những code đơn giản thì không cần sử dụng comment. Hãy áp dụng nguyên tắc đặt tên biến đã học để code của bạn viết ra sẽ tự giải thích luôn ý nghĩa của chính nó.

Đây là ví dụ cho việc comment để mô tả cách sử dụng:

<!-- prettier-ignore -->
```js
/*
Example:

var checked = true;

<Checkbox
   checked={checked}
   onChange={event => doSomething(event.target.checked)}
>
 Label for Box
</Checkbox>
*/

function Checkbox() {
   ...
}

```

> Việc lạm dụng comment, sử dụng không đúng lúc, không đúng chỗ sẽ gây dư thừa không cần thiết, làm mã của bạn trở nên khó nhìn và gây phản tác dụng. Vì vậy hãy cân nhắc sự cần thiết mỗi khi có ý định sử dụng comment trong mã của bạn.

Ví dụ dưới đây mô tả việc sử dụng comment chưa hiệu quả:

<!-- prettier-ignore -->
```js
// Khai báo biến
var email;
var password;

// Lấy giá trị người dùng nhập vào email input
email = event.target.value;

// Lấy giá trị người dùng nhập vào password input
password = event.target.value;
```

Comment như trên trở nên dư thừa không cần thiết vì đã là lập trình viên Javascript thì ai cũng sẽ hiểu đoạn code như vậy để làm gì.

> Ngoại lệ khi bạn là người mới học, việc sử dụng comment như trên là cần thiết để giúp bạn ghi nhớ chức năng, nhiệm vụ của từng đoạn code. Khi bạn đã hiểu và ghi nhớ được những kiến thức đó - Hãy ngừng comment như vậy!

### 2. Mục đích Vô hiệu hóa đoạn code

Bản chất là trình biên dịch code sẽ bỏ qua những comment (không thực thi chúng). Vì vậy khi một đoạn code được comment lại thì đoạn code đó sẽ không chạy. Đôi khi bạn sẽ muốn tạm bỏ đi một đoạn code nào đó trong ứng dụng của bạn, đó chính là lúc bạn có thể sử dụng comment.

Ví dụ:

<!-- prettier-ignore -->
```js
var email = 'email@domain.com';
var address = 'Hà Nội, Việt Nam';

alert(email); // alert này sẽ chạy
// alert(address); // alert này không chạy
```
