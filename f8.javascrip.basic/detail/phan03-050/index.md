# VÒNG LẶP FOR/OF LOOP

---

## Array

- Sử dụng lấy các phần tử của mảng Arr.

```js
// prettier-ignore
var languages = [
    'Javascript', 
    'CSS',
    'Html', 
    'Java'];

for (var course of languages) {
  console.log(course);
}
```

![Loop for/of](./images/001.png 'Loop for/of')

```js
// prettier-ignore
var languages = [
    'Javascript', 
    'CSS',
    'Html', 
    'Java'];

// 1.for/of
console.log('---1. for/of----');
for (var course of languages) {
  console.log(course);
}
// 2.for/in
console.log('---2. for/of----');
for (var index in languages) {
  console.log(index, languages[index]);
}
```

- Sẽ khác với for/in sẽ lấy ra index, và cần xử lý thêm mới lấy được phần tử của mảng.

---

## 2. String

- Lấy mỗi ký tự trong một chuỗi.

```js
var myString = 'Javascript';
for (var char of myString) {
  console.log(char);
} // J a v a s c r i p t
```

---

## 3. Object

- Nếu dùng kiểu này sẽ bị báo lỗi.

```js
var myInfo = {
  firstName: 'Dinh',
  lastName: 'Quang Duy',
  birthYear: 1985,
  address: 'Đà Nẵng',
  country: 'Việt Nam',
};

for (var char of myInfo) {
  console.log(char); // Uncaught TypeError: myInfo is not iterable
}
```

- Áp dụng cho đối tượng Object, sử dụng `Object.keys(myObject)` và `Object.values(myObject)`

```js
var myInfo = {
  firstName: 'Dinh',
  lastName: 'Quang Duy',
  birthYear: 1985,
  address: 'Đà Nẵng',
  country: 'Việt Nam',
};
console.log(Object.keys(myInfo));
console.log(Object.values(myInfo));

for (var item of Object.keys(myInfo)) {
  console.log(item);
}

for (var item of Object.values(myInfo)) {
  console.log(item);
}
```

![Loop for/of Object](./images/002.png 'Loop for/of Object')

---
