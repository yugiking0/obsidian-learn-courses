# DOM attribute

---

## 1. Lấy Element

- Vì Attribute là thuộc tính của Element
- Nên để lấy được Attribute thì ta cần lấy Element ra.

```html
<h1 id="heading1">Heading</h1>
```

- Ta lấy thẻ h1 element

```js
var headingElement = document.querySelector('h1');
console.log(headingElement);

// Heading
```

## 2. Thêm Attribute vào Element

## 2.1 Thêm bằng Setter

- Gán trực tiếp thuộc tính cho Element

- Chỉ cần từ đối tượng Element ta chấm thêm các thuộc tính và gán giá trị là sẽ thêm được.

```js
var headingElement = document.querySelector('h1');
headingElement.title = 'heading';
console.log(headingElement);

// <h1 title="heading">Heading</h1>
```

Lưu ý:

- Ta xem `inspect` ở tab `Elements` sẽ thấy được `Attribute` được thêm vào.
- Nhưng xem ở `View Page Source` sẽ không thấy được `Attribute` được thêm, nguyên nhân là khi chạy `Script` thì `Attribute` mới được thêm vào.
- Muốn thêm `class` thì phải dùng thuộc tính `.className` không phải `.class`

```js
var headingElement = document.querySelector('h1');
headingElement.className = 'heading';
console.log(headingElement);

// <h1 class="heading">Heading</h1>
```

## 2.2 Thêm bằng .setAttribute

- Bắt cách dùng phương thức để ép gán thuộc tính cho Element
- .setAttribute(className,value)

```js
var headingElement = document.querySelector('h1');
headingElement.setAttribute('data-box', 'heading');
console.log(headingElement);

// <h1 data-box="heading">kiểm tra</h1>
```

## 3. Lấy value Attribute từ Element

## 3.1 Lấy bằng phương thức .getAttribute

- Để lấy giá trị value của thuộc tính từ Element ta dùng phương thức .getAttribute
- Cấu trúc sẽ là element.getAttribute(attributeName)
- Dùng cho tất cả mọi Attribute

```html
<body>
  <h1 class="class-heading">Heading</h1>

  <script src=".\main.js"></script>
</body>
```

```js
var headingElement = document.querySelector('h1');

// Lấy Attribute có sẵn trên file html
console.log(headingElement.getAttribute('class'));

// Lấy Attribute được thêm vào từ JavaScript
headingElement.setAttribute('data-box', 'Data Test'); // attribute `data-box` không có sẵn
console.log(headingElement.'data-box');

// class-heading
// Data Test
```

## 3.2 Lấy attribute mặc định

- Đối với những Attribute được mặc định có sẵn theo Element đó thì chỉ cần chấm thuộc tính, gần giống như cách khi Setter vào.

```js
var headingElement = document.querySelector('h1');
headingElement.title="Title Header"; // Bằng Setter

// Lấy Attribute có sẵn trên file html
console.log(headingElement.getAttribute('title'));
console.log(headingElement.getAttribute('class'));
// Title Header
// class-heading

// Lấy Attribute được thêm vào từ JavaScript
headingElement.setAttribute('data-box', 'Data Test'); // attribute `data-box` không có sẵn
console.log(headingElement.data-box');
// undefined // -> Không lấy kiểu này đối với Attribute được thêm vào từ Script
```

> _**Lưu ý**: Chỉ dùng cách này đối với những thuộc tính hợp lệ đi theo từng loại Element được html qui định sẵn._

## 4. Tổng kết

- Trong thực tế sẽ hay sử dụng cách `.setAttribute` và `.getAttribute` để xử lý những `Element` những thuộc tính được customize bổ sung.
