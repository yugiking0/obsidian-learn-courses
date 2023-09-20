# ÔN TẬP Get element method - Phần 3

---

- [1. Ôn tập cấu trúc](#1-ôn-tập-cấu-trúc)
  - [getElementById](#getelementbyid)
  - [getElementsByClassName](#getelementsbyclassname)
  - [getElementsByTagName](#getelementsbytagname)
  - [querySelector](#queryselector)
  - [querySelectorAll](#queryselectorall)
  - [HTML collection](#html-collection)
  - [document.write](#documentwrite)
- [2. Sự khác nhau khi lấy: Element, NodeList, HTML Collections](#2-sự-khác-nhau-khi-lấy-element-nodelist-html-collections)

---

## 1. Ôn tập cấu trúc

```html
<h1 id="title">F8 - Javascript Basic</h1>
<h2 id="heading-1" class="heading">Heading 1</h2>
<h2 id="heading-2" class="heading">Heading 2</h2>
<p>Danh sách các đồ phải mua:</p>
<ul id="listItems">
  <li>Trứng</li>
  <li>Chanh</li>
  <li>Cam</li>
</ul>
<form action="" id="form-1">Form 1</form>
<form action="" id="form-2">Form 2</form>
```

### getElementById

- Để chọn được đối tượng ID ta dùng `document.getElementById()`, `getElement` không có s, số ít chỉ 1 đối tượng.
- `Lưu ý`: Vì ID trong HTML chỉ tồn tại duy nhất và tuân theo W3C nên việc getElementById chỉ lấy được 1 đối tượng tương ứng.
- Trả về một Element.

```js
var heading1 = document.getElementById('heading-1');
var heading2 = document.getElementById('heading-2');
var listItem = document.getElementById('listItems');
console.log(heading1);
console.log(heading2);
console.log(listItem);
```

### getElementsByClassName

- Cách để chọn được các đối tượng có cùng class ta dùng lệnh:
  `document.getElementsByClassName()`
- Elements có s, số nhiều do có nhiều đối tượng và trả về một HTMLcollection tương tự như mảng Array nhưng không dùng được các method như: .map, .reduce,...
- Trả về HTMLCollection mảng Elements.

```js
var heading1 = document.getElementsByClassName('heading');
console.log(heading1);
```

### getElementsByTagName

- Tag Name là những thẻ Tag của html như: h1, h2, p, a,...
- Cách để chọn những đối tượng thẻ này sẽ dùng ` document.getElementsByTagName()`
- Elements có s, số nhiều do có nhiều đối tượng
- Trả về HTMLCollection mảng Elements.

```js
var h2tag = document.getElementsByTagName('h2');
console.log(h2tag);
```

### querySelector

- Chọn đối tượng giống như cách mà CSS chọn các đối tượng của html, thông qua câu lệnh `document.querySelector`
- Trả về một Element.

```js
var title = document.querySelector('title');
console.log(title);

var heading1 = document.querySelector('#heading-1');
console.log(heading1);
```

### querySelectorAll

- Thông qua câu lệnh `document.querySelectorAll`
- Trả về 1 danh sách `NodeList` gần giống như mảng Array, gồm các Elements.

```js
var itemsList = document.querySelectorAll('ul li');
console.log(itemsList);

var heading = document.querySelectorAll('.heading');
console.log(heading);

for (var i = 0; i < heading.length; i++) {
  console.log(heading[i]);
}
```

### HTML collection

- Với HTML Collection cho phép chọn trực tiếp 1 số đối tượng từ document trực tiếp có hỗ trợ như:
  - Form
  - Archer: liên kết link
  - ...

```js
var items = document.forms;
console.log(items);

for (var i = 0; i < items.length; i++) {
  console.log(items[i]);
}
```

### document.write

- Sẽ tiến hành tạo 1 dòng đọc ngay sau vị trí chạy lệnh.

```js
document.write('Hello World.');
```

## 2. Sự khác nhau khi lấy: Element, NodeList, HTML Collections

- Chỉ có những `getElementById` và `querySelector` là khi lấy ra đối tượng sẽ là số ít, nên kết quả về trực tiếp sẽ là một phần tử `Element`.
- Những xử lý: `getElementsByClassName` , `getElementsByTagName` có `s` là số nhiều của `Element` nên kết quả trả về một mảng nhiều `Element` kiểu `NodeList` hoặc `HTML Collection`

> **Xem ví dụ:** Cho trước DOM có cấu trúc HTML như sau:

```html
<h1>Học lập trình tại F8</h1>

<section>
  <h2>Học JS HTML DOM</h2>
</section>

<div>
  <h3>Làm bài tập ngay trên F8</h3>
</div>
```

> **Yêu cầu :** Lấy h1 element và lưu vào biến h1Element

- Vì không thấy Class hay ID ở đây nên không dùng được: `getElementById` và `getElementsByClassName`.
- Dễ nhầm lẫn chọn sử dụng `getElementsByTagName` để lấy theo `Tag h1`

```js
var h1Element = document.getElementsByTagName('h1');
console.log(h1Element);

// HTMLCollection [h1]
```

![getElementsByTagName](bt-001.png 'getElementsByTagName')

- Vì ở đây chỉ lấy 1 `Element` không phải lấy `Node List` hay `HTML Collection`
- `Element` sẽ là dùng số ít trả về chỉ 1 đối tượng Element là `querySelector` sẽ phù hợp.

```js
var h1Element = document.querySelector('h1');
console.log(h1Element);

// <h1>Học lập trình tại F8</h1>
```

![querySelector](bt-002.png 'querySelector')

- Tại đây nếu muốn chỉ duy nhất 1 đối tượng `Element` bằng xử lý `getElementsByTagName` thì có thể dùng bằng cách lấy phần tử theo `Index` như sau:

```js
var h1Elements = document.getElementsByTagName('h1');
console.log(h1Elements[0]);

// <h1>Học lập trình tại F8</h1>
```
