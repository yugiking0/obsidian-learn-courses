# My some() and every() method

## 1. My some() method

- Array.some sẽ duyệt lần lượt từng phần tử của mảng, khi gặp phần tử thỏa mãn điều kiện sẽ dừng lại và trả về giá trị True; nếu không có phần tử nào thỏa mãn sẽ trả về giá trị False.

```js
var courses = [
  { name: 'Javascript', coin: 100 },
  { name: 'PHP', coin: 150 },
  { name: 'CSS', coin: 200 },
];
courses.length = 10;

var someCourses = courses.some(function (course, index, array) {
  console.log(course);
  return course.coin > 120;
});
console.log(someCourses);
```

- Ta viết lại

```js
var courses = [
  { name: 'Javascript', coin: 100 },
  { name: 'PHP', coin: 150 },
  { name: 'CSS', coin: 200 },
];
courses.length = 10;

Array.prototype.some2 = function (callback) {
  var output = false;
  for (var index in this) {
    if (this.hasOwnProperty(index)) {
      if (callback(this[index], index, this)) {
        output = true;
        break;
      }
    }
  }
  return output;
};

var someCourses = courses.some2(function (course, index, array) {
  return course.coin > 120;
});
console.log(someCourses);
```

- Không dùng output

```js
Array.prototype.some2 = function (callback) {
  for (var index in this) {
    if (this.hasOwnProperty(index)) {
      if (callback(this[index], index, this)) {
        return true;
      }
    }
  }
  return false;
};
```

## 2. My Every() method

- Array.every sẽ duyệt lần lượt từng phần tử của mảng, khi gặp phần tử sai điều kiện sẽ dừng lại và trả về giá trị false; nếu tất cả đềy đúng sẽ trả về giá trị True.
- Array.every sẽ ngược 1 tý so với Array.some:
  - Giá trị ban đầu every là false, gặp đúng sẽ trả về true và dừng lại.
  - Giá trị ban đầu some là true, gặp sai sẽ trả về false và dừng lại.

```js
var courses = [
  { name: 'Javascript', coin: 100 },
  { name: 'PHP', coin: 150 },
  { name: 'CSS', coin: 200 },
];
courses.length = 10;

Array.prototype.every2 = function (callback) {
  var output = true;
  for (var index in this) {
    if (this.hasOwnProperty(index)) {
      var result = callback(this[index], index, this);
      if (!result) {
        output = false;
        break;
      }
    }
  }

  return output;
};

var everyCourses = courses.every2(function (course, index, array) {
  return course.coin < 180;
});
console.log(everyCourses);
```
