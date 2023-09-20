# Destructuring, Rest

---

## 1. Destructuring

- Phân rả cấu trúc để gán biến tương ứng.
- Áp dụng cho:
  - Array
  - Object

### 1.1 Destructuring Array

- Xét ví dụ sau:

```js
const courses = ['Javascript', 'CSS', 'html'];
const a = courses[0];
const b = courses[1];
const c = courses[2];

console.log('a:', a); // a: Javascript
console.log('b:', b); // b: CSS
console.log('c:', c); // c: html
```

- Với Destructuring áp dụng cho Array, vẫn ra kết quả tương tự như sau:

```js
const courses = ['Javascript', 'CSS', 'html'];
const [a, b, c] = courses;

console.log('a:', a); // a: Javascript
console.log('b:', b); // b: CSS
console.log('c:', c); // c: html
```

- Lưu ý sự tương ứng đồng bộ số biến cần khai báo gán và phần tử của mảng.
- Nếu gán số biến ít hơn số phần tử của mảng thì:

```js
const courses = ['Javascript', 'CSS', 'html', 'NodeJS'];
const [a, b] = courses;

console.log('a:', a); // a: Javascript
console.log('b:', b); // b: CSS
```

- Tách rời các biến phần tử của mảng

```js
const courses = ['Javascript', 'CSS', 'html', 'NodeJS'];
const [a, , b] = courses;

console.log('a:', a); // a: Javascript
console.log('b:', b); // b: html
```

- hoặc

```js
const courses = ['Javascript', 'CSS', 'html', 'NodeJS'];
const [, a, , b] = courses;

console.log('a:', a); // a: CSS
console.log('b:', b); // b: NodeJS
```

### 1.2 Destructuring Object

### 1.2.1 Object Matching, Shorthand Notation

- Gán nhanh key của Property
- Xét ví dụ sau:

```js
var course = {
  name: 'Javascript',
  price: 1000,
};
const name = course.name;
const price = course.price;

console.log('Name:', name); // Name: Javascript
console.log('Price:', price); // Price: 1000
```

```js
var course = {
  name: 'Javascript',
  price: 1000,
};

const { name: a, price: b } = course;

console.log('Name:', a); // Name: Javascript
console.log('Price:', b); // Price: 1000
```

- Hoặc xử lý Destructuring Object đơn giản hơn:

```js
var course = {
  name: 'Javascript',
  price: 1000,
};

const { name, price } = course;

console.log('Name:', name); // Name: Javascript
console.log('Price:', price); // Price: 1000
```

### 1.2.2 Object Matching, Deep Matching

- Gán chuyên sâu
- Xem ví dụ, lấy các thông tin sau:

```js
var student = {
  name: 'Quang Duy',
  age: 27,
  address: {
    city: 'Da Nang',
    ward: 'Son Tra',
    street: 'Ngo Quyen',
  },
  object: {
    nameObject: 'Javascript',
    teacher: 'Minh Thu',
    priceObject: 5000,
  },
};

const name = student.name;
const city = student.address.city;
const nameObject = student.object.nameObject;
const teacher = student.object.teacher;

console.log('Student name:', name); // Student name: Quang Duy
console.log('City:', city); // City: Da Nang
console.log('Teacher name:', teacher); // Teacher name: Minh Thu
console.log('Name Object:', nameObject); // Name Object: Javascript
```

- Có thể viết ngắn lại bằng của

```js
var student = {
  name: 'Quang Duy',
  age: 27,
  address: {
    city: 'Da Nang',
    ward: 'Son Tra',
    street: 'Ngo Quyen',
  },
  object: {
    nameObject: 'Javascript',
    teacher: 'Minh Thu',
    priceObject: 5000,
  },
};

const {name,address:{city},object: {nameObject,teacher}} = student;

console.log('Student name:', name); // Student name: Quang Duy
console.log('City:', city); // City: Da Nang
console.log('Teacher name:', teacher); // Teacher name: Minh Thu
console.log('Name Object:', nameObject); // Name Object: Javascript
```

### 1.2.3 Object Matching, Result of Function

```js
function getInfo() {
  return {
    name: 'Quang Duy',
    age: 27,
    address: {
      city: 'Da Nang',
      ward: 'Son Tra',
      street: 'Ngo Quyen'
    },
  }
}

const { name, address: { city }} = getInfo();

console.log('Student name:', name);     
// Student name: Quang Duy
console.log('City:', city);             
// City: Da Nang
```

### 1.3 Destructuring with Default Values
- Và nếu như trong trường hợp bạn không biết chính xác số lượng phần tử có trong mảng hay object để matching thì trong ES6 cũng hỗ trợ bạn thiết lập giá trị mặc định cho nó như sau:

#### 1.3.1 Đối với mảng

```js
var num = [1];
var [a = "Default", b = "Default"] = num;
console.log(a, b);
// a = 1
// b = Default
```

#### 1.3.2 Đối với Object

```js
var student = { name: "Vũ Thanh Tài"};
var {name = "Not Set", age = "Not Set"} = student;
console.log(name, age);
// name = Vũ Thanh Tài
// age = Not Set
```

### 1.4 Destructuring with Parameter Context Matching

```js
function logArray ([a, b]) {
    console.log(a, b);
}
logArray(["Tham Số A -", "- Tham số B"]);
//Tham Số A - - Tham số B
```

```js
function logObject ({a, b}) {
    console.log(a, b);
}
logObject({a: "Tham Số A -", b: "- Tham số B"});
//Tham Số A - - Tham số B
```

---

## 2. Rest

- Phần còn lại, thường sử dụng để lấy danh sách các phần tử còn lại sau khi xử lý đặt biến.

### 2.1 Kết hợp với Destructuring

#### 2.1.1 Array
```js
const courses = ['Javascript', 'CSS', 'html', 'NodeJS'];
const [a,...rest] = courses;
console.log('a:', a);       // a: Javascript
console.log('rest:', rest); // rest: ['CSS', 'html', 'NodeJS']
```

```js
const courses = ['Javascript', 'CSS', 'html', 'NodeJS'];
const [,a,...rest] = courses;
console.log('a:', a);       // a: CSS
console.log('rest:', rest); // rest: ['html', 'NodeJS']
```

#### 2.1.2 Object

```js
var course = {
  name: 'Javascript',
  description: 'Use font-end va back-end',
  price: 1000,
};

const { name, ...rest } = course;
console.log('Name: ', name);
console.log('Rest: ', rest);
```

![Rest](Javascript/f8.javascrip.basic/detail/phan06-106/images/001.png 'Rest')

- Với xử lý có thể giúp tạo một Object mới bao gồm luôn Properties và Method của Object cũ

```js
var course = {
  name: 'Javascript',
  description: 'Use font-end va back-end',
  price: 1000,
  getName() {
    return `${this.name}`;
  },
};

const { name, ...rest} = course;
console.log('Name: ', name);
console.log('Rest: ', rest);
```

![Rest](Javascript/f8.javascrip.basic/detail/phan06-106/images/002.png 'Rest')


#### 2.1.3 Sử dụng Rest trong Function

```js
function logger(a,...rest) {
  console.log(a);
  if(rest.length>0){
    for(var i=0; i<rest.length; i++){
      console.log(rest[i]);
    }
  }
}

logger('Message','Xin Chao', 'Hello')
// Message
// Xin Chao
// Hello
```

#### 2.1.4 Rest và arguments

- `Rest` sử dụng trong Function gần như biến `arguments` lấy lên được danh sách các tham số truyền vào hàm. 

```js
function logger(...rest) {
  console.log(arguments);
  console.log(rest);
}

logger('Message','Xin Chao', 'Hello')
```

![Rest](Javascript/f8.javascrip.basic/detail/phan06-106/images/003.png 'Rest')

- Ví dụ với Array

```js
function logger([a, b, ...rest]) {
  console.log('a: ', a); // a:  1
  console.log('b: ', b); // b:  2
  console.log('rest: ', rest); // rest:  (6) [3, 4, 5, 6, 7, 8]
}

logger([1, 2, 3, 4, 5, 6, 7, 8]);
```

- Ví dụ với Object

```js
function logger({ name, ...rest }) {
  console.log('Name: ', name);  // Name:  Javascript
  console.log('rest: ', rest); // rest:  {description: 'Description', price: 1000}
}

logger({
  name: 'Javascript',
  description: 'Description',
  price: 1000,
});
```

- So sánh [Rest vs Arguments](Javascript/f8.javascrip.basic/detail/phan06-106/rest_arguments.md)
---