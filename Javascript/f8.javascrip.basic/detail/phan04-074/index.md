# Get element method - Phần 2

---

Cho trước DOM có cấu trúc HTML như sau:

```html
<div class="box-1">
  <ul>
    <li>Javascript 1</li>
    <li>PHP 1</li>
  </ul>
</div>

<div class="box-2">
  <ul>
    <li>Javascript 2</li>
    <li>PHP 2</li>
  </ul>
</div>
```

> Yêu cầu

1. Lấy các thẻ `li` của `class box-1`

## Cách 1

- Ta dùng theo cách bài cũ

```js
var listItemNodes = document.querySelectorAll('.box-1 li');
var listItemNodes = document.querySelectorAll('.box-1 > ul >  li');
console.log(listItemNodes);
```

## Cách 2

- Lấy đối tượng box-1
- Từ đối tượng box-1 lấy tiếp thẻ li

```js
var boxNode = document.querySelector('.box-1');
var listItemNodes = boxNode.querySelectorAll('li');
console.log(listItemNodes);
```

---

## Bài tập

Cho trước DOM có cấu trúc HTML như sau:

```html
<div class="box">
  <div class="children">Children</div>
  <div class="children">Children</div>
</div>
```

> Yêu cầu

1. Get element có class box và lưu vào biến boxElement
2. Từ biến boxElement get elements có class children lưu vào biến childrenElements

```js
// Làm bài tập tại đây

var boxElement = document.querySelector('.box');
var childrenElements = boxElement.querySelectorAll('.children');
```
