# Làm việc với mảng

- Include Array Methods:
  - forEach()
  - every()
  - some()
  - find()
  - filter()
  - map()
  - reduce()

---

Cho mảng ví dụ như sau:

```js
var courses = [
  { id: 1, name: 'Javascript', coin: 100 },
  { id: 2, name: 'HTML,CSS', coin: 200 },
  { id: 3, name: 'Ruby', coin: 300 },
  { id: 4, name: 'PHP', coin: 200 },
  { id: 5, name: 'React', coin: 480 },
];
```

---

## 1. Array.forEach()

- Sẽ duyệt qua từng phần tử của mảng và lấy giá trị ra tương tự như for/of; nhưng thêm giá trị index vị trí của phần tử và truy xuất vào được ô nhớ của mảng đang xử lý.
- Không trả về kết quả (not return)

```js
var a = courses.forEach(function (value, index, originArray) {
  console.log('Lần: ' + index);
  console.log(value);
  value.coin += 30;
  console.log(originArray);
  return 1;
});

console.log(a); // undefined
// For/of
for (var value of courses) {
  console.log(value);
}
```

> SYNTAX : Array.forEach(function(itemCurrent,indexCurrent,originArray))

---

## 2. Array.every()

- Kiểm tra trong mảng tồn tại phần tử so với điều kiện, sẽ trả về giá trị Boolean.
- Cần return lại.

```js
var a = courses.every(function (value, index, originArray) {
  console.log('Lần: ' + index);
  return value.coin < 400;
});

console.log(a); // false
```

- Sẽ đi qua từng phần tử theo thứ tự index, khi gặp phần tử sai (False) so với điều kiện sẽ ngừng lại, nếu đúng mới kiểm tra phần từ tiếp theo.

- Khi điều kiện Sai(false) sẽ ngừng lại liền, false có index càng nhỏ thì sẽ chạy càng ít.

  > SYNTAX : Array.every(function(itemCurrent,indexCurrent,originArray)) => Return true/false

- Áp dụng: Kiểm tra tất cả phần tử thỏa mãn điều kiện nào đó.
  Ví dụ: Kiểm tra mảng tồn tại giá trị âm hay không?

---

## 3. Array.some()

- Sẽ đi qua từng phần tử theo thứ tự index, khi gặp phần tử thỏa mãn điều kiện Đúng (True) thì sẽ ngừng lại liền, nếu sai thì sẽ tiếp tục kiểm tra phần tử tiếp theo; ngược với every.

```js
var a = courses.some(function (value, index, originArray) {
  console.log('Lần: ' + index);
  return value.coin > 150;
});

console.log(a); // true
```

- Khi gặp Đúng (`true`) sẽ ngừng lại liền, nếu gặp `true` `index` càng nhỏ sẽ chạy càng ít .

---

## 4. Array.find()

- Đi qua các phần tử của mảng, khi gặp phần tử thỏa mãn điều kiện thì sẽ dừng lại và trả về phần tử đó.
- Khác với `some` chỉ trả về `True`, thì `find` sẽ trả về phần tử đó.

```js
var a = courses.find(function (value, index, originArray) {
  console.log('Lần: ' + index);
  return value.coin > 150;
});

console.log(a); // {id: 2, name: "HTML,CSS", coin: 200}

// Find course Ruby
var course = courses.find(function (value, index, originArray) {
  return value.name == 'PHP';
});

console.log(course); // {id: 4, name: "PHP", coin: 200}
```

- Nếu không có phần tử nào thỏa mãn điều kiện lọc sẽ báo Undefined

```js
var course = courses.find(function (value, index, originArray) {
  return value.name == 'SQL'; // undefined
});

console.log(course); // undefined
```

---

## 5. Array.filter()

- Lọc các phần tử của mảng thỏa điều kiện lọc; sẽ trả về 1 mảng các phần tử thỏa mãn điều kiện lọc.

```js
var a = courses.filter(function (value, index, originArray) {
  return value.coin > 200;
});
console.log(a);
```
