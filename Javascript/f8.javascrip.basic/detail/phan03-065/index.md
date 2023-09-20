# Empty elements of array

### 1. Phần tử thực tế của mảng và độ dài mảng

- Độ dài của mảng đôi khi không đúng với số lượng phần tử thực tế của mảng hiện có.

> Ví dụ 1:

```js
//Ví dụ 1
var arr1 = new Array(10);

console.log(arr1);
console.log(arr1.length);
```

![vidu01](Javascript/f8.javascrip.basic/detail/phan03-065/images/001.png 'vidu01')

> Ví dụ 2:

```js
//Ví dụ 1
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

console.log(courses);
console.log(courses.length);
```

![vidu02](Javascript/f8.javascrip.basic/detail/phan03-065/images/002.png 'vidu02')

### 2. Duyệt qua các phần tử của mảng

- Hay dùng duyệt qua các phần tử của mảng bằng vòng lặp for như sau:

```js
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

console.log(courses);
for (var i = 0; i < courses.length; i++) {
  console.log(courses[i]);
}
```

![vidu03](Javascript/f8.javascrip.basic/detail/phan03-065/images/003.png 'vidu03')

- Nhưng với cách này sẽ lọc qua tất cả những phần tử empty và như vậy sẽ không đúng.
- Có 1 cách khác xử lý là dùng: for/in để duyệt qua

```js
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

console.log(courses);
for (var index in courses) {
  console.log(courses[index]);
}
```

![vidu04](Javascript/f8.javascrip.basic/detail/phan03-065/images/004.png 'vidu04')

- Nhưng với cách này thì do tính chất của Constructor Array liên kết nhau, nên lúc này những Prototype được tạo ra cũng bị duyệt qua.

```js
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

Array.prototype.testFunc = function (get) {
  get(this);
};
Array.prototype.forEach2 = function (callBack) {
  callBack(this);
};

console.log(courses);
console.log('--------------------');
for (var index in courses) {
  console.log(courses[index]);
}
```

![vidu05](Javascript/f8.javascrip.basic/detail/phan03-065/images/005.png 'vidu05')

- Vậy để xử lý chỉ duyệt qua các phần tử thực của mảng cũng như sẽ bỏ qua những method được khai báo Prototype thì ta dùng một tính chất check phần tử của mảng là: `hasOwnProperties`

```js
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

Array.prototype.every2 = function (callBack) {
  callBack(this);
};
console.log(courses);

console.log('--1---------------------');
for (var index in courses) {
  console.log(courses[index]);
}

console.log('--2---------------------');
for (var index in courses) {
  if (courses.hasOwnProperty(index)) {
    console.log(courses[index]);
  }
}
```

![vidu07](Javascript/f8.javascrip.basic/detail/phan03-065/images/007.png 'vidu07')

```js
var courses = ['Javascript', 'PHP', 'CSS'];
courses.length = 10;

Array.prototype.forEach2 = function (callBack) {
  for (var index in this) {
    if (this.hasOwnProperty(index)) {
      callBack(this[index], index, this);
    }
  }
};

console.log(courses);
console.log('--------------------');
courses.forEach2(function (course, index) {
  console.log(course, index);
});
```

![vidu06](Javascript/f8.javascrip.basic/detail/phan03-065/images/006.png 'vidu06')
