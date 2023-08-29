# OBJECT PROTOTYPE - THUỘC TÍNH NGUYÊN MẪU.

Trong một `Object Constructor` sẽ được cấu thành nên bởi các thuộc tính ở bên trong, và các thuộc tính này được gọi là `Object Prototype` - _Thuộc tính nguyên mẫu_.

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

![Object Prototype](./images/001.png 'Object Prototype')

- Xét ví dụ: Thêm 1 thuộc tính tên lớp học cho tất cả mọi user đều phải có.
- Thử thêm vào ở Object Constructor (Đối tượng thiết kế) như sau:

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

// Thêm thuộc tính lớp cho Object Constructor User
User.className = 'Lớp JavaScript'; // Cách này không được.

var author = new User('Sơn', 'Đặng', 'Avatar');
var user = new User('Vũ', 'Nguyễn', 'Avatar');

console.log(User.className); // Lớp JavaScript
console.log(author.className); // undefined
console.log(user.className); // undefined
```

![Add new Prototype 1](./images/002.png 'Add new Prototype 1')

- Cách thêm như `Object.property` sẽ không được, vì chỉ tạo được ở `User` nhưng các đối tượng được tạo từ `User` như author và `user` đều không có.

- Cách thêm sẽ như sau:

```js
// Thêm thuộc tính lớp cho Object Constructor User
User.prototype.className = 'Lớp JavaScript';
```

![Add new Prototype 2](./images/003.png 'Add new Prototype 2')
