# OBJECT CONSTRUCTOR - THIẾT KẾ ĐỐI TƯỢNG

Giống như xây dựng 1 ngôi nhà, thì cần có 1 bản thiết kế các chi tiết của ngôi nhà mẫu, sau đó tùy theo mỗi ngôi nhà thực tế sẽ bổ sung hay điều chỉnh lại.

**OBJECT CONSTRUCTOR** tạm hiểu là thiết kế đối tượng mẫu.

---

## LỢI ÍCH

- Việc tạo sẵn đối tượng thiết kế sẽ giúp tiết kiệm thời gian, vì có thể khởi tạo nhiều đối tượng dựa trên đối tượng mẫu này.
- Khi thay đổi, bổ sung đặc điểm chung nào đó cần có ở tất cả các đối tượng thì chỉ cần điều chỉnh ở đối tượng thiết kế.

## VÍ DỤ

Vì các tài khoản đăng nhập vào trang web đều có các đặc điểm chung:

    - Họ
    - Tên
    - Tên đầy đủ tài khoản
    - Hình đại diện
    - Phân quyền
    - ...

- Nên có thể tạo 1 đối tượng thiết kế cơ sở ban đầu có các thuộc tính, đặc điểm chung.
- Sau đó dựa trên đối tượng thiết kế này để tạo các tài khoản khi khởi tạo mới.

```js
// Object Constructor
function User(firstName, lastName, avatar) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.avatar = avatar;

  this.getName = function () {
    return `${this.firstName} ${this.lastName}`;
  };
}
```

Lưu ý:

- Object Constructor được tạo gần như Function
- Qui tắc chữ cái đầu tiên phải viết Hoa
- Sử dụng `this.` để đại diện cho `Object Constructor`
- `Object Constructor` sẽ bao gồm các `Prototype`(_Thuộc tính nguyên mẫu_):

  - Thuộc tính - this.Property
  - Phương thức - this.Method (Function)

- Khi tạo các tài khoản chỉ cần gọi `new Object Constructor` như sau:

```js
var author = new User('Sơn', 'Đặng', 'Avatar');
var user = new User('Vũ', 'Nguyễn', 'Avatar');

console.log(author);
console.log(user);
```

![Object Constructor](Javascript/f8.javascrip.basic/detail/phan03-038/images/001.png 'Object Constructor 1')

- Mỗi đối tượng được tạo ra từ đối tượng thiết kế mẫu, khi log ra sẽ thấy có Kiểu đối tượng mẫu ở đầu, và có thuộc tính `constructor` gọi đến đối tượng thiết kế `User`

![Object Constructor](Javascript/f8.javascrip.basic/detail/phan03-038/images/002.png 'Object Constructor 2')

![Object Constructor](Javascript/f8.javascrip.basic/detail/phan03-038/images/004.png 'Object Constructor 2')

- Vì mỗi đối tượng ngoài việc có chung một số đặc điểm thì còn có các đặc điểm riêng biệt khác nhau mà đối tượng khác không có như:

  - _author:_ Có chức danh Title
  - _user:_ Có comment

- Ta có thể bổ sung vào các đối tượng này, cách tạo như thêm thuộc tính của Object bình thường như sau:

```js
author.tittle = 'Comment dạo tại F8';
user.comment = 'Có dạy React không vậy?';

console.log(author);
console.log(user);
```
