# Classes

---

## 1. Lý thuyết

- Ở **`ES6`** đã bổ sung thêm Classes để hướng ngôn ngữ javascript có thể viết được lập trình OOP dễ dàng hơn.
- Có thể xem class gần giống như Function constructor và được mở rộng hơn.

## 2. Vài ví dụ liên quan Function Constructor

### 2.1 Tạo mới Function Constructor

- Ta xét câu lệnh tạo một Function Constructor như sau:

```js
// Constructor Function : Đối tượng nguyên mẫu
function Course(name, price) {
  this.name = name;
  this.price = price;
}

var jsCourse = new Course('JavaScript Cơ Bản', 1000);
console.log('Course Name: ', jsCourse);
// Course Name:
// Course {name: 'JavaScript Cơ Bản', price: 1000}
```

- Với class sẽ viết lại thành:

```js
class Course {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
}

var jsCourse = new Course('JavaScript Cơ Bản', 1000);
console.log('Course Name: ', jsCourse);
```

- Sẽ gom lại chung ở Block code `constructor` và kết quả hiển thị giống y như Function Constructor

### 2.2 Bổ sung Method cho Đối tượng nguyên mẫu

- Việc bổ sung method cho Class cũng tương tự như Function Constructor

```js
class Course {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
}

var jsCourse = new Course('JavaScript Cơ Bản', 1000);
jsCourse.getName = function () {
  return this.name;
};

console.log('Course Name: ', jsCourse.getName());
```

## 3. Bố cục Class

- Khối block constructor
- Nhóm lệnh getValues, setValue liên quan.
- Nhóm lệnh static method

```js
class Course {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  // getter/setter method
  getName() {
    return this.name;
  }
  setName(newName) {
    this.name = newName;
  }
  getPrice() {
    return this.price;
  }

  // static method
  run() {
    let isSucceeded = false;
    if (true) {
      isSucceeded = true;
    }
  }
}

var jsCourse = new Course('JavaScript', 1000);
console.log('Course Name: ', jsCourse.getName());
// Course Name:  JavaScript

jsCourse.setName('Python');
console.log('Course Name: ', jsCourse.getName());
// Course Name:  Python
```

## 4. Mục đích dùng Class

- Tổ chức code dễ nhìn hơn, gọn gàng hơn
- Hướng đến áp dụng xử lý theo hướng đối tượng
- Tất cả được viết chung trong Block code của Class sẽ đảm bảo:
  - Hạn chế sử dụng biến Global của các chương trình
  - Scope: Phạm vi biến
  - Closure: Tính đóng gói
  - Phân loại từng đối tượng và chức năng của đối tượng được sử dụng
  - Tính kế thừa
- Áp dụng sử dụng ở Nodejs
- Tối ưu xử lý phát triển chương trình

Xem mục [Object vs Classes](Javascript/f8.javascrip.basic/detail/phan06-103/object-class.md)

Xem mục [Classes](Javascript/f8.javascrip.basic/detail/phan06-103/classes.md)

```js
// Object
const cssCourse = {
  name: 'CSS',
  price: 150,

  getName: function () {
    return this.name;
  },
  setName: function (newName) {
    this.name = newName;
  },
};

console.log('O.Course Name: ', cssCourse.getName());
// Course Name:  CSS
cssCourse.setName('Python');
console.log('O.Course Name: ', cssCourse.getName());
// Course Name:  Python

// Function Constructor
function fcCourse(name, price) {
  this.name = name;
  this.price = price;

  this.getName = function () {
    return this.name;
  };
  this.setName = function (newName) {
    this.name = newName;
  };
}
var jsCourse = new fcCourse('JavaScript', 1000);
console.log('FC Course Name: ', jsCourse.getName());
// Course Name:  JavaScript
jsCourse.setName('PHP');
console.log('FC Course Name: ', jsCourse.getName());
// Course Name:  PHP

// Class
class ClassCourse {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  getName() {
    return this.name;
  }
  setName(newName) {
    this.name = newName;
  }
  getPrice() {
    return this.price;
  }

  run() {
    let isSucceeded = false;
    if (true) {
      isSucceeded = true;
    }
  }
}

var jsCourse = new ClassCourse('JavaScript', 1000);
console.log('Course Name: ', jsCourse.getName());
// Course Name:  CSS
jsCourse.setName('Python');
console.log('Course Name: ', jsCourse.getName());
// Course Name:  Python
```
