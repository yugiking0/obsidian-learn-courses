# InnerText vs textContent Property

---

Học về thuộc tính Property của Text Node của Element:

- InnerText
- textContent

---

## 1. Giới thiệu

- Sẽ nghiên cứu về Text Node, các thuộc tính Property

![Text Node](./images/001.png 'Text Node')

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>My Web Page</title>
  </head>

  <body>
    <h1 class="headingClass">Welcome To My Web Page</h1>
  </body>
</html>
```

- `Text node` ở đây là `My Web Page` và `Welcome To My Web Page` tương ứng với 2 Elements có Tag `<title>` và `<h1>`
- Giúp lấy ra nội dung của `Text Node`, và sửa lại nội dung của `Text Node`.
- Để tương tác với Text Node thì đầu tiên phải lấy được Element Node.

```js
var h1Element = document.querySelector('h1');
console.log(h1Element);

// <h1 class="heading">Heading Text</h1>
```

## 2. InnerText và textContent Property

- Để lấy nội dung của `Text Node` thì chỉ cần . thuộc tính như sau:

```js
var h1Element = document.querySelector('h1');
console.log('innerText: ', h1Element.innerText);
console.log('textContent: ', h1Element.textContent);
```

![Text Node](./images/002.png 'Text Node')

- Để điều chỉnh nội dung của `Text Node` ta dùng Setter

```js
var h1Element = document.querySelector('h1');

setTimeout(() => {
  h1Element.innerText = 'New Heading';
}, 3000);

setTimeout(() => {
  h1Element.textContent = 'New Heading 2';
}, 6000);
```

- Ta sẽ thấy được sự thay đổi nội dung của `<h1>` từ : `Heading Text` => `New Heading` => `New Heading 2`

## 3. Sự khác nhau của InnerText và textContent

- Ta xem ví dụ:

```html
<h1 class="heading">
  <span class="heading">Heading </span>
  <span>Text</span>
</h1>
```

```js
var h1Element = document.querySelector('h1');

console.log(h1Element.innerText);
console.log(h1Element.textContent);
```

![Text Node](./images/003.png 'Text Node')

- Thấy `innerText` sẽ thể hiện giống như nội dung trên page hiển thị
- Còn `textContent` thể hiện thông tin như ở file `html` được thiết kế.

![Text Node](./images/004.png 'Text Node')

- Thử ẩn đi nội dung `Heading` như sau:

```html
<h1 class="heading">
  <span style="display: none">Heading </span>
  <span>Text</span>
</h1>
```

```js
var h1Element = document.querySelector('h1');

console.log(h1Element.innerText);
console.log(h1Element.textContent);
```

- Thấy `innerText` sẽ thể hiện giống như nội dung trên page hiển thị, bị mất đi `Heading` bởi `style="display: none"`
- Còn `textContent` thể hiện thông tin như ở file `html` được thiết kế.

![Text Node](./images/005.png 'Text Node')

- Nếu ta thêm 1 số thẻ xử lý `style` như sau ở html

```html
<h1 class="heading">
  <span style="display: none">Heading </span>
  <span>Text</span>

  <style>
    .box {
      width: 100px;
      height: 50px;
    }
  </style>
</h1>
```

![Text Node](./images/006.png 'Text Node')

## 4. Bài tập

- Cho html như sau:

```html
<div class="box"></div>

<div></div>
```

> Sử dụng thuộc tính textContent để giải các bài tập trong phần này.
> **Yêu cầu**

- 1. Thêm nội dung text `Học lập trình tại F8` vào thẻ `div` có `class box`
- 2. Thêm nội dung text `Thao tác với DOM qua bài tập tại F8` vào thẻ `div` thứ hai

```js
var boxElement = document.querySelector('.box');
boxElement.textContent = 'Học lập trình tại F8';

var div2Elements = document.querySelectorAll('div');
div2Elements[1].textContent = 'Thao tác với DOM qua bài tập tại F8';
```

## ![Text Node](./images/007.png 'Text Node')
