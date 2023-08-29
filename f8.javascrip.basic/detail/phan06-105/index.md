# Enhanced object literals

- Định nghĩa key : value của Object ngắn gọn hơn.
- Định nghĩa method cho Object.
- Định nghĩa key của Object dưới dạng biến.

---

- `Enhanced object literals` Chuẩn hóa khai báo đối tượng bổ sung thông qua sử dụng biến và viết khai báo đối tượng ngắn gọn hơn.

## 1. Property Shorthand :

- `Property Shorthand` là Khai báo thuộc tính ngắn gọn hơn.
- Định nghĩa `key : value` của Object ngắn gọn hơn.
- Xét ví dụ khai báo đối tượng như sau:

```js
const course = {
  name: 'Javascript',
  price: 2000,
  getName: function () {
    return console.log(this.name);
  },
};

console.log(course);
course.getName();
```

![Object](./images/001.png 'Object')

- Để có thể sừ dụng biến để gán vào.

```js
const name = 'Javascript';
const price = 2000;

const course = {
  name: name,
  price: price,
  getName: function () {
    return console.log(this.name);
  },
};

console.log(course);
course.getName();
```

![Object](./images/001.png 'Object')

- Và có thể viết ngắn gọn hơn ở Thuộc tính - Properties của Object, mà không thay đổi như sau:

```js
const name = 'Javascript';
const price = 2000;

const course = {
  name,
  price,
  getName: function () {
    return console.log(this.name);
  },
};

console.log(course);
course.getName();
```

![Object](./images/002.png 'Object')

## 2. Method Properties

- `Method Properties` khai báo Phương thức Method ngắn gọn hơn.
- Định nghĩa method cho Object ngắn gọn hơn.
- Từ kiểu viết đầy đủ có function như sau:

```js
const name = 'Javascript';
const price = 2000;

const course = {
  name,
  price,
  getName: function () {
    return console.log(this.name);
  },
};

console.log(course);
course.getName();
```

- Thành kiểu viết lược bớt đi như sau:

```js
const name = 'Javascript';
const price = 2000;

const course = {
  name,
  price,
  getName() {
    return console.log(this.name);
  },
};

console.log(course);
course.getName();
```

**_- Vậy Function Constructor??? và Class có áp dụng được không?_**

## 3. Computed Property Names

- Định nghĩa key của Object dưới dạng biến.
  - Gán `key` của Property(tên của thuộc tính) bằng một biến.
  - Tính toán các giá trị trên tên của thuộc tính.

### 3.1 Định nghĩa key của Object dưới dạng biến

- Xét ví dụ sau:

```js
const name = 'name';
const age = 18;

const student = {
  [name]: 'Duy',
  ['full_' + name]: 'Dinh Quang Duy',
  age,
};

console.log(student);
```

![Object](./images/003.png 'Object')

- Cách gán này gần như cách gọi thành phần của Object khi lấy giá trị.

```js
const name = 'student';
const age = 18;

const student = {
  [name]: 'Duy', // student : 'Duy'
  [name + 'Name']: 'Dinh Quang Duy',
  age,
};

console.log(student);
console.log(student[name]); // student[student] : Duy
console.log(student.name);  // undefined
```

![Object](./images/004.png 'Object')

### 3.2 Tính toán các giá trị trên tên của thuộc tính
- Xử lý key theo phép tính toán.
```js
const name = 'student';
const age = 18;

const student = {
  [name] : 'Duy', // student : 'Duy'
  [name +  'Name']: 'Dinh Quang Duy', // studentName : 'Dinh Quang Duy'
  age,
};

console.log(student);
console.log(student[name + 'Name']); // student['studentName']
console.log(student['studentName']);
console.log(student.studentName);
```

![Object](./images/005.png 'Object')