# Callback Phần 2

## Nội dung

**Callback** :

1. Là hàm
2. Truyền qua đối số
3. Được gọi lại trong hàm nhận đối số

## Ví dụ

- Xét ví dụ xử lý hàm map như sau:

```js
var courses = ['Javascript', 'CSS', 'Html'];

var htmls = courses.map(function (course) {
  return `<h1>${course}</h1>`;
});
console.log(htmls.join(''));
```

Ta viết lại 1 hàm map2 xử lý chức năng giống như hàm map như sau:

- Cần khai báo method này thuộc Prototype của mảng Array.
- Các đối số truyền vào sẽ là: các phần tử của mảng và index vị trí.
- Trả về kết quả là 1 mảng mới với các phần tử đã xử lý bởi hàm truyền vào.

```js
// 1. Khai báo vào Prototype của Array thêm 1 Method mới
Array.prototype.map2 = function (callBack) {
  //console.log(this); // Kiểm tra key word this gọi lại
  // Vì map sẽ trả về 1 mảng nên ta sẽ thêm 1 mảng tạm và return về mảng này
  var output = [];
  var lengthArray = this.length;
  for (var i = 0; i < lengthArray; i++) {
    var result = callBack(this[i], i);
    output.push(result);
  }
  return output;
};

var html2s = courses.map2(function (course) {
  return `<h1>${course}</h1>`;
});
console.log(html2s.join(''));
```

- Cần kiểm tra các đối số truyền vào để phù hợp xử lý và cảnh báo lỗi.

## Bài tập

Viết lại các phương thức mới tương tự như:

- forEach
- reduce
- find
- filter
- some
- every
- ...

### 1. forEach2

```js
var courses = ['Javascript', 'CSS', 'Html'];

courses.forEach(function (value, index, arr) {
  console.log(value, index, arr);
});

// Viết lại

Array.prototype.forEach2 = function (callBack) {
  var lengthArr = this.length;
  for (var i = 0; i < lengthArr; i++) {
    callBack(this[i], i, this);
  }
};

courses.forEach2(function (value, index, arr) {
  console.log(value, index, arr);
});
```

### 2. reduce2

```js
var courses = [
  { course: 'Javascript', value: 10 },
  { course: 'CSS', value: 20 },
  { course: 'Html', value: 30 },
];

var total = courses.reduce(function (acc, cur, index, arr) {
  return acc + cur.value;
}, 0);

console.log(total);

// Viết lại
Array.prototype.reduce2 = function (callBack, initialValue) {
  // console.log(arguments.length); // 1. Kiểm tra số tham số truyền vào.
  var i = 0;
  var lengthArr = this.length;
  if (arguments.length < 2) {
    initialValue = this[0];
    i = 1;
  }
  for (i; i < lengthArr; i++) {
    initialValue = callBack(initialValue, this[i], i, this);
  }
  return initialValue;
};

var total2 = courses.reduce2(function (acc, cur, index, arr) {
  return acc + cur.value;
}, 0);

console.log(total2);
```

### 3. Reduce3

```js
var courses = [
  { course: 'Javascript', value: 10 },
  { course: 'CSS', value: 20 },
  { course: 'Html', value: 30 },
];

Array.prototype.reduce3 = function (callBack) {
  // console.log(arguments.length); // 1. Kiểm tra số tham số truyền vào.
  var acc = this[0];
  var i = 1;
  var lengthArr = this.length;
  if (arguments.length > 1) {
    acc = arguments[1];
    i = 0;
  }
  for (i; i < lengthArr; i++) {
    acc = callBack(acc, this[i], i, this);
  }
  return acc;
};

var total3 = courses.reduce3(function (acc, cur, index, arr) {
  return acc + '<h1>' + cur.course + '</h1>';
}, '');

console.log(total3);
```

### 4. find

- Tìm phần tử đầu tiên thỏa mãn điều kiện

```js
var courses = [
  { course: 'Javascript', value: 10 },
  { course: 'CSS', value: 20 },
  { course: 'Html', value: 30 },
];

var findArr = courses.find(function (item) {
  return item.value > 10;
});
console.log(findArr); // {course: 'CSS', value: 20}

// Viết lại
Array.prototype.find2 = function (callBack) {
  for (var i = 0; i < this.length; i++) {
    if (callBack(this[i], i, this) === true) {
      return this[i];
      break;
    }
  }
};
findArr = courses.find2(function (item) {
  return item.value > 10;
});
console.log(findArr); // {course: 'CSS', value: 20}
```

### 5. filter

- Tìm tất cả các phần tử thỏa mãn điều kiện và trả về mảng mới chứa các phần tử đó.

```js
var courses = [
  { course: 'Javascript', value: 10 },
  { course: 'CSS', value: 20 },
  { course: 'Html', value: 30 },
];

var filterArr = courses.filter(function (item) {
  return item.value > 10;
});
console.log(filterArr);

// Viết lại
Array.prototype.filter2 = function (callBack) {
  var output = [];
  var lengthArr = this.length;
  for (var i = 0; i < lengthArr; i++) {
    if (callBack(this[i], i, this) === true) {
      output.push(this[i]);
    }
  }
  return output;
};

filterArr = courses.filter2(function (item) {
  return item.value > 5;
});
console.log(filterArr);
```

### 6. flat

- Làm phẳng mảng, chuyển qua mảng 1 cấp độ từ 1 mảng chứa nhiều cấp mảng.

```js
const arr1 = [0, 1, 2, [3, 4]];

console.log(arr1.flat());
// expected output: [0, 1, 2, 3, 4]

const arr2 = [0, 1, 2, [[[3, 4]]]];

console.log(arr2.flat(2));
// expected output: [0, 1, 2, [3, 4]]
```

- Viết lại Function

```js
/**
 * flat : Làm phẳng mảng
 */
const arr1 = [0, 1, 2, [3, 4]];
const arr2 = [0, 1, 2, [[[3, 4]]]];

function flat2(arr) {
  var output = [];
  var lengthArr = arr.length;
  for (var i = 0; i < lengthArr; i++) {
    if (!Array.isArray(arr[i])) {
      output = output.concat(arr[i]);
    } else {
      output = output.concat(flat2(arr[i]));
    }
  }
  return output;
}
console.log(flat2(arr1)); //[0, 1, 2, 3, 4]
console.log(flat2(arr2)); //[0, 1, 2, 3, 4]
```

- Viết lại prototype

```js
const arr1 = [0, 1, 2, [3, 4]];
const arr2 = [0, 1, 2, [[[3, 4]]]];

Array.prototype.flat2 = function (callBack) {
  var output = [];
  var lengthArr = this.length;
  for (var i = 0; i < lengthArr; i++) {
    if (!Array.isArray(this[i])) {
      output = output.concat(this[i]);
    } else {
      output = output.concat(this[i].flat2());
    }
  }
  return output;
};
console.log(arr1.flat2());
console.log(arr2.flat2(2));
```

```js
Array.prototype.flat2 = function (callBack) {
  var output = [];
  var lengthArr = this.length;
  output = this.reduce(function (acc, cur) {
    return !Array.isArray(cur) ? acc.concat(cur) : acc.concat(cur.flat2());
  }, []);

  return output;
};
```

### 8. some

- Tồn tại một phần tử trong mảng, thỏa mãn điều kiện thì sẽ trả về True.

```js
var courses = [
  { course: 'Javascript', value: 10 },
  { course: 'CSS', value: 20 },
  { course: 'Html', value: 30 },
];

var newCourses = courses.some(function (course, index, arr) {
  return course.value > 15; // 20
});
console.log(newCourses); // true

//Viết lại

Array.prototype.some2 = function (callBack) {
  var lengthArr = this.length;
  var output = false;
  for (var i = 0; i < lengthArr; i++) {
    if (callBack(this[i], i, this)) {
      output = true;
      break;
    }
  }
  return output;
};
var newCourses2 = courses.some2(function (course, index, arr) {
  return course.value > 15;
});
console.log(newCourses2);
```

### 9. every

- Tất cả mọu phần tử trong mảng thỏa mãn thì trả về true
- Tồn tại một phần tử không thỏa mãn, thì trả về false ngay.

```js
var courses = [
  { course: 'Javascript', value: 10 },
  { course: 'CSS', value: 20 },
  { course: 'Html', value: 30 },
];

var newCourses = courses.every(function (course, index, arr) {
  return course.value > 15;
});
console.log(newCourses);

Array.prototype.every2 = function (callBack) {
  var lengthArr = this.length;
  var output = true;
  for (var i = 0; i < lengthArr; i++) {
    if (!callBack(this[i], i, this)) {
      output = false;
      break;
    }
  }
  return output;
};
var newCourses2 = courses.every2(function (course, index, arr) {
  return course.value > 15;
});
console.log(newCourses2);
```
