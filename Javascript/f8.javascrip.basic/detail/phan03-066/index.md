# My filter() method

### 1. Array.forEach

- Array.forEach sẽ duyệt qua các phần tử của mảng và không trả về mảng mới.

### Ví dụ

```js
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

courses.forEach(function (course, index, array) {
  console.log(course, index);
});
```

- Viết lại forEach duyệt qua các phần tử của mảng, ở đây dựa theo bài trước ta sẽ không dùng loop for kiểu:

```js
for (var i = 0; i < this.length; i++) {
  callback(this[i], i, this);
}
```

Nguyên nhân do cách này sẽ lấy toàn bộ những phần tử Empty của mảng và lọc theo độ dài của mảng sẽ không chính xác.

- Thay vào đó sẽ sử dụng: for/in và `this.hasOwnProperty` như sau:

```js
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

Array.prototype.forEach2 = function (callback) {
  for (var index in this) {
    if (this.hasOwnProperty(index)) {
      callback(this[index], index, this);
    }
  }
};
courses.forEach2(function (course, index, array) {
  console.log(course, index);
});
```

### 2. Array.filter

- Array.filter sẽ duyệt qua tất cả các phần tử trong mảng và trả về mảng mới với các phần tử thỏa mãn điều kiện.

  > Chú ý: Tham khảo Value Type(Tham trị) và Reference Type(Tham chiếu)

- Tham khảo ở:

  - Xem thêm ở [Value Type và Reference Type](value-reference.md)
  - [Value Type và Reference Type](https://www.javascripttutorial.net/javascript-primitive-vs-reference-values) https://www.javascripttutorial.net/javascript-primitive-vs-reference-values
  - [Value Type và Reference Type](https://dmitripavlutin.com/value-vs-reference-javascript) https://dmitripavlutin.com/value-vs-reference-javascript/

Ví dụ: Tìm những khóa học mà có coin lớn hơn 120.

```js
var courses = [
  { name: 'Javascript', coin: 100 },
  { name: 'PHP', coin: 150 },
  { name: 'CSS', coin: 200 },
];
courses.length = 10;

var filterCourses = courses.filter(function (course, index, array) {
  return course.coin > 120;
});
console.log(filterCourses);
```

- Viết lại method filter2 và lưu ý sử dụng for/in và hasOwnerProperty để xử lý duyệt qua các phần tử của mảng cho đúng.

```js
var courses = [
  { name: 'Javascript', coin: 100 },
  { name: 'PHP', coin: 150 },
  { name: 'CSS', coin: 200 },
];
courses.length = 10;

Array.prototype.filter2 = function (callback) {
  var output = [];
  for (var index in this) {
    if (this.hasOwnProperty(index)) {
      if (callback(this[index], index, this)) {
        output.push(this[index]);
      }
    }
  }
  return output;
};
var filterCourses = courses.filter2(function (course, index, array) {
  return course.coin > 120;
});
console.log(filterCourses);
```
