# ClassList Property

---

- Thuộc tính ClassList Property chỉ có thể truy cập khi truy cập được Element

```js
var boxElement = document.querySelector('.box');
console.log([boxElement]);
```

![ClassList](./images/001.png 'ClassList')

## 1. Chức năng

- là Đối tượng DOMTokenList quản lý các class của Element

```html
<body>
  <button type="submit" id="load-id">Load</button>

  <div class="box box1 box2 box3" id="box-id"></div>
</body>
```

```js
var boxElement = document.querySelector('.box');
console.log([boxElement.classList]); // object
```

![ClassList](./images/002.png 'ClassList')

- Ta thấy `class="box box1 box2 box3"` sẽ thể hiện DOMTokenList gồm 4 phần tử.

```js
var boxElement = document.querySelector('.box');
console.log(boxElement.classList); // object
console.log(boxElement.classList[2]); // box2
```

![DOMTokenList](./images/003.png 'DOMTokenList')

- Với thuộc tính ClassList Property có thể điều chỉnh các class của Element thông qua các phương thức là:
  - add
  - contains
  - removed
  - toggle

![Prototype](./images/004.png 'Prototype')

## 2. ClassList.length

- Sử dụng biết số lượng class của Element

```html
<div class="box box1 box2 box2" id="box-id"></div>
```

```js
console.log(boxElement.length); // 3
```

## 3. ClassList.add

- Thêm class vào element

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Demo</title>
    <style>
      .red {
        color: red;
      }
    </style>
  </head>

  <body>
    <div class="box box1 box2 box2" id="box-id">
      <h1>CLASSLIST</h1>
    </div>
  </body>
  <script src="../main.js"></script>
</html>
```

```js
boxElement.classList.add('red');
```

- Element `.box` đã được thêm vào Class `red`
- Đối tượng đã có màu đỏ.

![ClassList.add](./images/005.png 'ClassList.add')

- Thêm nhiều class, cách nhau bởi dấu phẩy ','

```js
boxElement.classList.add('blue', 'green');
```

## 3. ClassList.contains

- Kiểm tra một class có tồn tại trong Element

```js
console.log(boxElement.classList.contains('red'));
```

## 4. ClassList.remove

```js
console.log(boxElement.classList.remove('red'));
```

- Ta có thể áp dụng để xóa màu dòng sau vài giây.

```js
function iniLoad() {
  setTimeout(() => {
    boxElement.classList.remove('red');
  }, 3000);
}
```

## 5. ClassList.toggle

- Sẽ kiểm tra nếu element chưa có class này thì thêm vào, nếu đã có thì xóa đi
- Chức năng như 1 công tắc.
- Có thể áp dụng làm dòng chữ nhấp nháy

```js
setInterval(() => {
  boxElement.classList.toggle('red');
}, 1000);
```
- Ứng dụng là nút đống mở 1 tab menu 
----------------------------------------------------------------