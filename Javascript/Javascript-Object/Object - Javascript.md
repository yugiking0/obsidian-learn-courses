# Ôn kiến thức về Javascript
---
## Các mục cần xem lại
- Object 
- Object Contructors [[Javascript/Javascript-Object/detail/phan03-038/index|Contructors]] - Thiết kế đối tượng
- Object Prototypes [[Javascript/Javascript-Object/detail/phan03-040/index|Prototypes]] - Thuộc tính nguyên mẫu
- Object Map, new Map
- Class [[Javascript/Javascript-Object/detail/phan06-103/index| Class]] - Lớp đối tượng
- Module [[Javascript/Javascript-Object/detail/phan06-109/index| Module]]
- Enhanced object literals [[Javascript/Javascript-Object/detail/phan06-105/index| Object literal]]

---
## Object - Đối tượng

```js
const person = {  
  // Object Properties : Value
  firstName: "John",  
  lastName: "Doe",  
  id: 5566,  
  // Object methods : Function
  fullName: function() {  
    return **this**.firstName + " " + **this**.lastName;  
  }  
};
```

- Đối tượng sẽ bao gồm:
	- Key - Value : **Properties** - Thuộc tính - giá trị
	- Function : **Methods** - Phương thức
- Phân cách bởi dấu phẩy (,)

## Object Contructors - Thiết kế đối tượng

```js
function Person(first, last, age) { // Viết hoa 
  this.firstName = first; // Dấu ; mỗi giá trị  
  this.lastName = last;  
  this.age = age;  
  this.name = function() {  
    return this.firstName + " " + this.lastName;  
  };  
}

// Khởi tạo 1 đổi tượng từ constructor Person
var person01_Tuan = new Person('Tuan','Tran', 27)
var person02_Hoa = new Person('Hoa','Nguyen', 22)
```

- Là một Function được khai báo viết Hoa để phân biệt 
- Đối tượng Mẫu được thiết kế sẽ giúp cho việc tạo các đối tượng nhanh hơn, với các đặc điểm được mô tả sẵn.
- Gán các thuộc tính là ***this.key*** 
- Phân cách bởi các dấu chấm phẩy (;)

## Object Prototype - Thuộc tính nguyên mẫu của đổi tượng

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
User.className01 = 'Lớp JavaScript'; // Cách này không được.
User.prototype.className = 'Lớp JavaScript'; // Phải thêm kiểu này

var author = new User('Sơn', 'Đặng', 'Avatar');
var writer = new User('Vũ', 'Nguyễn', 'Avatar');

console.log(User.className01);  // Lớp JavaScript
console.log(User.className);    // undefined

console.log(author.className01); // undefined
console.log(writer.className);  // Lớp JavaScript
```

![[Object_Prototype-002.png]]

- Dùng để bổ sung thêm  thuộc tính nguyên mẫu cho Object Contructors, để áp dụng chi tiết cho các đối tượng tạo ra từ Object Contructors
- Khi show đối tượng được tạo từ Object Contructors sẽ không thấy thông tin, thông tin được bổ sung từ Prototype sẽ ở mục _ *Proto* _

![[Javascript/Javascript-Object/detail/phan03-040/images/003.png| prototype_003]]

## Map
```js
// Create a Map  
const fruits = new Map([  
  ["apples", 500],  
  ["bananas", 300],  
  ["oranges", 200]  
]);
```

## Class - Lớp đối tượng
```js
class Car {  
  constructor(brand) {  // Constructor  
    this.carname = brand;  
  }  
}  
mycar = new Car("Ford");
```
- Bắt đầu là **class** thay cho **function**
- Tiếp theo nằm trong khối **contructor**
- 