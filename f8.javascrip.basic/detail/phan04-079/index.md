# InnerHTML vs OuterHTML Property

---

- Cách thêm Element vào một Element khi dùng html DOM
- Thêm được Attribute và Text Node vào element
- innerHTML và OuterHTML
- Sự khác nhau của InnerHTML vs OuterHTML Property

---

## 1. Thêm Element vào Element (InnerHTML)

- Ta có file html như sau:

```html
<body>
  <div class="box"></div>
</body>
```

- Cần thêm 1 thẻ `h1 Heading` vào `div class= 'box'`
- Ta sử dụng thử những phương thức như `innerText` và `textContent` để gán.

```js
var boxElement = document.querySelector('.box');
boxElement.innerText = '<h1>Heading</h1>';
boxElement.textContent = '<h1>Heading2</h1>';
```

![innerText](./images/002.png 'innerText')
![textContent](./images/003.png 'textContent')

- Với cách gán Text Node Value này không thêm được.

## 2. InnerHTML Property

- Ta dùng InnerHTML vs OuterHTML Property

```js
var boxElement = document.querySelector('.box');
boxElement.innerHTML = '<h1>Heading</h1>';
```

![innerHTML](./images/004.png 'innerHTML')

- Nếu bỏ đi cặp thẻ tag h1

```js
var boxElement = document.querySelector('.box');
boxElement.innerHTML = 'Heading';
```

![Text Node](./images/005.png 'Text Node')

- Như vậy đã có thể thêm `Text Node` của thẻ `<div class = 'box'> </div>`

```js
var boxElement = document.querySelector('.box');
boxElement.innerHTML = `<div class = 'Heading'></div>`;
```

![Attribute Node](./images/006.png 'Attribute Node')

- Đã thêm được 1 Attribute Node vào thẻ `<div class = 'box'> </div>`

![innerHTML](./images/007.png 'innerHTML')
![innerHTML](./images/008.png 'innerHTML')

- Với `innerHTML` có thể lấy được nội dung Element html để xử lý.

## 3. OuterHTML Property

- Có sẵn file html như sau:

```html
<body>
  <div class="box">
    <h1 title="heading">New Heading</h1>
  </div>
</body>
```

- Xử lý outerHtml

```js
var boxElement = document.querySelector('.box');
console.log(boxElement.outerHTML);
```

![outerHTML](./images/009.png 'outerHTML')

- Lấy được cả thẻ `<div class="box">`

## 4. Sự khác nhau giữa innerHTML và outerHTML

- Có file html như sau:

```html
<body>
  <div class="box">
    <h1 title="heading">New Heading</h1>
  </div>
</body>
```

- Xử lý innerHTML

```js
var boxElement = document.querySelector('.box');
boxElement.innerHTML = '<h1>Text</h1>';
console.log(boxElement.textContent);
```

![innerHTML](./images/010.png 'innerHTML')

- Với innerHTML đã xử lý là:

  - Bỏ Text Node value của `<div class="box">` mất chữ `New Heading`
  - Thêm 1 thẻ `<h1>Text</h1>`

- Xử lý outerHTML

```js
var boxElement = document.querySelector('.box');
boxElement.outerHTML = '<h1>Text</h1>';
console.log(boxElement);
```

![outerHTML](./images/011.png 'outerHTML')

- Đã thay thể thẻ `<div class="box">` bằng thẻ `<h1>Text</h1>`, ghi đè đối tượng Element luôn.

![outerHTML](./images/012.png 'outerHTML')

- Lưu ý mặc dù đã mất đi thẻ `<div class="box">`, nhưng khi lấy thông tin ra vẫn lấy thông tin thẻ `<div class="box">` từ trong bộ nhớ.

```js
var boxElement = document.querySelector('.box');
boxElement.outerHTML = '<h1>Text</h1>';
var h1Element = document.querySelector('h1');

console.log(h1Element);
console.log(boxElement);
```

![outerHTML](./images/013.png 'outerHTML')


---