# DOM CSS

---

- Thuộc tính nằm trong Element Node
- Thuộc tính Getter hoặc Setter cho CSS inline của Element.

---

## 1. CSS Style Inline - CSSStyleDeclaration

- Ta có html

```html
<div class="box"></div>
```

```js
var boxElement = document.querySelector('.box');
console.log([boxElement]);
console.log(boxElement.style);

console.log(typeof boxElement.style); // object
```

![style CSS Inline](./images/001.png 'style CSS Inline')

### 1.1 Style size

- Thử thay đổi kích thướt cho `.box`

```js
var boxElement = document.querySelector('.box');

boxElement.style.backgroundColor = 'red';
boxElement.style.width = `200px`;
boxElement.style.height = `50px`;
```

### 1.2 Sử dụng gán Object style

- Để tránh việc viết lại nhiều lần gán `xxElements.style = yy`, nên sử dụng khai báo đối tượng có các thuộc tính sẵn, sau đó gán với element.style Object

> Object.assign()

```js
Object.assign(boxElement.style, {
  height: '20px',
  width: '100px',
  backgroundColor: 'red',
});

// Theme
var themeStyle = {
  height: '20px',
  width: '100px',
  backgroundColor: 'red',
};

Object.assign(boxElement.style, themeStyle);
console.log(boxElement.style.width); // 100px
```

```html
<div
  class="box"
  style="height: 20px; width: 100px; background-color: red;"
></div>
```

- Đây là cách dùng CSS DEMO xử lý inline đối tượng ở trường hợp đặc biệt.
- Bình thường thì nên dùng cách dùng file CSS External bên ngoài link vào
