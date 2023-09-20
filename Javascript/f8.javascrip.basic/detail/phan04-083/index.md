# DOM events

---

## 1. DOM events là gì?

- Là sự kiện xảy ra khi trang web được tương tác.
- Các sự kiện này có thể là:
  - Khi trang web được load lên
  - Khi đóng trang web
  - Khi người dùng thao tác các elements của trang web như:
    - Click chuột, click double vào đối tượng
    - Chọn đối tượng, kéo thả đối tượng
    - Cuộn chuột, bôi đen
    - Nhập liệu vào textbox hoặc bấm nút submit
- DOM events gồm:
  - Attribute Event: Các thuộc tính Event
  - Assign event using the node element: gán các event cho đối tượng element

## 2. Tìm hiểu các loại DOM Events

- Các tên gọi Event có thể xem ở link:

  - Xem [HTML DOM Events ](https://www.w3schools.com/jsref/dom_obj_event.asp)
  - Xem [HTML Event Attributes](https://www.w3schools.com/tags/ref_eventattributes.asp)

![DOM Events](Javascript/f8.javascrip.basic/detail/phan04-083/images/001.png 'DOM Events')

- Common HTML Events

| Event       | Description                                        |
| ----------- | -------------------------------------------------- |
| onchange    | An HTML element has been changed                   |
| onclick     | The user clicks an HTML element                    |
| onmouseover | The user moves the mouse over an HTML element      |
| onmouseout  | The user moves the mouse away from an HTML element |
| onkeydown   | The user pushes a keyboard key                     |
| onload      | The browser has finished loading the page          |

## 3. Attribute Event

- Sử dụng Event khi thêm trực tiếp vào element bên file html như sau:

```html
<body>
  <h1 onclick="console.log(Math.random());">DOM Events</h1>
</body>
```

- thêm chữ `on` vào sự kiện: `onclick="console.log(Math.random());"`
  vd: onclick, ondblclick, onmouseover

```html
<body>
  <h1 onmouseover="changeColor("red")" onmouseout="changeColor("black")">DOM Events</h1>
</body>
```

```js
function changeColor(color) {
  h1.style.color = color;
}
```

- Tính chất nổi bọt của sự kiện của đối tượng Element, kiểm tra sự kiện từ đối tượng con, sau đó kiểm tra tiếp sự kiện của đối tượng cha của đối tượng đó.

```js
<body>
  <h1 onclick="console.log(this);">
    <span>DOM Events</span>
  </h1>
</body>
```

## 3. Assign Event

- Gán sự kiện cho qua Element Node bằng function

```js
var h1 = document.querySelector('h1');

h1.onclick = function (e) {
  console.log(e);
  alert('Hello World!');
};
```

![Assign Event](Javascript/f8.javascrip.basic/detail/phan04-083/images/003.png 'Assign Event')

```html
<body>
  <h1>
    <span>DOM Events 1</span>
  </h1>
  <h1>
    <span>DOM Events 2</span>
  </h1>
  <h1>
    <span>DOM Events 3</span>
  </h1>
</body>
```

- Nếu viết kiểu này sẽ bị lỗi:

```js
var h1 = document.querySelectorAll('h1');

for (var i = 0; i < h1.length; i++) {
  h1[i].onclick = function (e) {
    console.log(h1[i]);
  };
}

// undefined : Do không xác định i
```

- Mà nên phải dùng event target để xử lý.

```js
var h1 = document.querySelectorAll('h1');

for (var i = 0; i < h1.length; i++) {
  h1[i].onclick = function (e) {
    console.log(e.target);
  };
}
```
