# Arrow Function

---

- Hàm mũi tên: Được tạo nên có mũi tên, tương tự như các cách tạo hàm:
  - Function Declaration: Hàm khai báo
  - Function expression:
  - Arrow Function

---

## 1. Cấu trúc

- Xét ví dụ tạo một hàm như sau:

```js
function logger(log) {
  console.log(log);
}

logger('Message...');
// Message...
```

- Chuyển thành Arrow Function

```js
const logger = log => console.log(log);

logger('Message...');
// Message...
```

- Trình tự:
  - Bỏ chữ function
  - Khai báo biến có tên function
  - Thêm dấu suy ra `=>`

## 2. Sử dụng

### 2.1 Hàm chỉ có 1 biến

- Nếu hàm chỉ có một biến truyền vào

```js
const logger = log => console.log(log);
logger('Message...');
// Message...
```

- Có thể chuyển bỏ đi dấu ngoặc ở biến

```js
const logger = log => console.log(log);
logger('Message...');
// Message...
```

### 2.2 Hàm chỉ có xử lý 1 dòng trả kết quả

- Từ kiểu viết

```js
const sum = (a, b) => {
  return a + b;
};
console.log(sum(2, 3)); // 5
```

- Có thể chuyển thành

```js
const sum = (a, b) => a + b;
console.log(sum(2, 3)); // 5
```

### 2.3 Hàm chỉ có xử lý trả về khối code

```js
const items = [
  { name: 'T-shirt', price: 20 },
  { name: 'hat', price: 12 },
  { name: 'boot', price: 25 },
];

const total = items => {
  return items.reduce((acc, item) => {
    return acc + item.price;
  }, 0);
};
console.log('Total: ', total(items));
// Total:  57
```

- Có thể viết gọn lại, lược bỏ cặp ngoặc `{return ...}`

```js
const total = items => items.reduce((acc, item) => acc + item.price, 0);
console.log('Total: ', total(items));
```

- Nhưng việc viết gọn kiểu này rất khó đọc code, nếu có nhiều khối lồng nhau, nên cần xem xét viết kiểu nào cho thuận tiện đọc và chỉnh sửa sau này.

### 2.4 Hàm trả về một đối tượng

- Ta xem xét câu lệnh sau:

```js
const car = (name, color) => {
  return {
    name: name,
    color: color,
  };
};
console.log(car('Toyota', 'black'));
// {name: 'Toyota', color: 'black'}
```

- Nếu viết ngắn gọn lại bỏ cặp ngoặc nhọn sẽ gây lỗi.

```js
const car = (name, color) => {
    name: name,
    color: color,
  };

console.log(car("Toyota", "black"));
// Uncaught SyntaxError: Unexpected token ':'
```

- Ta cần thêm 1 cặp ngoặc đơn để hiểu đó là 1 nhóm lệnh

```js
const car = (name, color) => ({
  name: name,
  color: color,
});

console.log(car('Toyota', 'black'));
// {name: 'Toyota', color: 'black'}
```

## 3. Lưu ý

### 3.1 Dùng trong Object

- Ta xem xét câu lệnh

```js
const Course = {
  name: 'Javascript',
  getName: function () {
    return this.name; // Context
  },
};
// Hoặc
const Course = {
  name: 'Javascript',
  getName() {
    return this.name; // Context
  },
};

console.log(Course.getName());
// Javascript
```

- Ta viết lại Method thành Arrow Function, thì không ra được kết quả.

```js
const course = {
  name: 'Javascript',
  getName: () => {
    return this;
  },
};

console.log(course.getName());
// Window {window: Window, name: '', …}

const car = {
  name: 'Toyota',
  getName: () => {
    return this.name;
  },
};

console.log('Car name: ', car.getName());
// Car name:  undefined
```

- Như vậy Arrow Function không có Context của This trong Object

### 3.2 Dùng trong Function Constructor

- Xem xét ví dụ sau

```js
const Course = function (name, price) {
  (this.name = name),
    (this.price = price),
    (this.getName = function () {
      return this.name;
    });
};
const jsCourse = new Course('Javascript', 1000);
console.log(jsCourse.getName());
// Javascript
```

- Khi thay đổi hàm xử lý getName thành Arrow Function thì vẫn cho phép, khác với Object ở trên.

```js
const Course = function (name, price) {
  (this.name = name), (this.price = price), (this.getName = () => this.name);
};
const jsCourse = new Course('Javascript', 1000);
console.log(jsCourse.getName());
// Javascript
```

- Nếu viết Function Constructor thành theo kiểu Arrow Function thì sẽ xuất hiện lỗi không hiểu constructor.

```js
const Course = (name, price) => {
  (this.name = name), (this.price = price), (this.getName = () => this.name);
};
const jsCourse = new Course('Javascript', 1000);
console.log(jsCourse.getName());
// Uncaught TypeError: Course is not a constructor
```

- Sử dụng ở Classes

```js
class Course {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  getName = () => this.name;
}

const jsCourse = new Course('Javascript', 1000);
console.log('Name of course: ', jsCourse.getName());
// Name:  Javascript
```

```js
class Course {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  getName = function () {
    return this.name;
  };
}

const jsCourse = new Course('Javascript', 1000);
console.log('Name of course: ', jsCourse.getName());
// Name:  Javascript
```

```js
class Course {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  getName() {
    return this.name;
  }
}

const jsCourse = new Course('Javascript', 1000);
console.log('Name of course: ', jsCourse.getName());
// Name:  Javascript
```
