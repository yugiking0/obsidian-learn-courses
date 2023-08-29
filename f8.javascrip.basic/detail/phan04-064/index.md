# Get element method - Phần 1

## Tổng quan

Có thể tương tác với Element từ cách cách là:

- ID
- class
- Tag Name
- CSS Selector
- HTML Collection

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>F8 - Javascript Basic</title>
    <style>
      body {
        height: 100vh;
        align-items: center;
        background: linear-gradient(to top left, #28b487, #7dd56f);
      }

      h1 {
        width: 100%;
        text-align: center;
        color: white;
      }
      .hidden {
        display: dis;
      }
    </style>
  </head>
  <body>
    <h1 id="title">F8 - Javascript Basic</h1>

    <h2 class="h2class">Core HTML</h2>
    <h2 class="h2class">XML DOM</h2>
    <h2 class="h2class">HTML DOM</h2>

    <h3 class="h3class">1. Element</h3>
    <h3 id="att">2. Attribute</h3>
    <h3 id="text">3. Text</h3>

    <script src=".\main.js"></script>
  </body>
</html>
```

## 1. ID

- Ta có các ID là id="title", id="att", id="text", để chọn được đối tượng ID ta dùng `document.getElementById()`, getElement không có s, số ít chỉ 1 đối tượng.
  > Lưu ý: Vì ID trong HTML chỉ tồn tại duy nhất và tuân theo W3C nên việc getElementById chỉ lấy được 1 đối tượng tương ứng.

```js
var title = document.getElementById('title');
console.log(title);
```

- Khi chuyển con trỏ vào vị trí console thì sẽ highlight lên được id="title"

![getElementById](./images/001.png 'getElementById')

- Hoặc viết lại để tránh nhầm lẫn với Tab Elements của DevTool khi hiển thị ở Tab Console ta viết đối tượng(Node) trong mảng hoặc Object để dễ quản lý.

```js
var title = document.getElementById('title');
console.log({
  element: title,
});
```

![getElementById](./images/002.png 'getElementById')

## 2. class

- Ta có các class là class="h2class", class="h3class"
- Cách để chọn được các đối tượng có cùng class ta dùng lệnh:
  `document.getElementsByClassName()`
- Elements có s, số nhiều do có nhiều đối tượng và trả về một HTMLcollection tương tự như mảng Array nhưng không dùng được các method như: .map, .reduce,...

```js
var h2class = document.getElementsByClassName('h2class');
console.log(h2class);
```

![getElementById](./images/003.png 'getElementById')

## 3. Tag Name

- Tag Name là những thẻ Tag của html như: h1, h2, p, a,...
- Cách để chọn những đối tượng thẻ này sẽ dùng ` document.getElementsByTagName()`

```js
var h2tag = document.getElementsByTagName('h2');
console.log(h2tag);
```

- Elements có s, số nhiều do có nhiều đối tượng và trả về một HTMLcollection

## 4. CSS Selector

### 4.1 Chọn 1 phần tử: `document.querySelector`

- Chọn đối tượng giống như cách mà CSS chọn các đối tượng của html, thông qua câu lệnh `document.querySelector`

```js
var att = document.querySelector('#att');
console.log(att);

var h2class = document.querySelector('.h2class');
console.log(h2class);

var h2 = document.querySelector('h1');
console.log(h2);
```

![CSS Selector](./images/004.png 'CSS Selector')

- Cần xem ôn lại mục CSS Selector [CSS selector](./css-selector.md)

Ví dụ:

```html
<body>
  <h1 id="title">F8 - Javascript Basic</h1>
  <h2 class="heading-2">Heading 2.0</h2>
  <h1 class="heading">HTML DOM</h1>

  <div class="box">
    <h2 class="heading-2">Heading 2.1</h2>
    <h2 class="heading-2">Heading 2.2</h2>
    <h2 class="heading-2">Heading 2.3</h2>
    <h2 class="heading-2">Heading 2.4</h2>
  </div>
</body>
```

1. Lấy thẻ h2 Đầu tiên thuộc box.

```js
var heading2Node = document.querySelector('.box .heading-2:first-child');
console.log(heading2Node);
```

![Heading 2 đầu tiên thuộc Box](./images/005.png 'Heading 2 đầu tiên thuộc Box')

2. Lấy thẻ h2 thứ 2 thuộc box.

```js
var heading2Node2 = document.querySelector('.box .heading-2:nth-child(2)');
console.log(heading2Node2);
```

![Heading 2 thứ hai thuộc Box](./images/006.png 'Heading 2 thứ hai thuộc Box')

### 4.2 Chọn nhiều phần tử: `document.querySelectorAll`

- Thông qua câu lệnh `document.querySelectorAll` sẽ trả về 1 danh sách `NodeList` gần giống như mảng Array.

> **Ví dụ:**

```html
<body>
  <h1 id="title">F8 - Javascript Basic</h1>
  <h2 class="heading-2">Heading 2.0</h2>
  <h1 class="heading">HTML DOM</h1>

  <div class="box">
    <h2 class="heading-2">Heading 2.1</h2>
    <h2 class="heading-2">Heading 2.2</h2>
    <h2 class="heading-2">Heading 2.3</h2>
    <h2 class="heading-2">Heading 2.4</h2>
  </div>
</body>
```

- Lấy danh sách các đối tượng class="heading-2"

```js
var heading2Nodes = document.querySelectorAll('.box .heading-2');
console.log(heading2Nodes);
```

![querySelectorAll](./images/007.png 'querySelectorAll')

- Từ đây có thể lấy từng phần tử từ danh sách này giống như Array thông qua vòng lặp for hoặc while như sau:

```js
var heading2Nodes = document.querySelectorAll('.box .heading-2');
console.log(heading2Nodes[2]); // lấy phần tử thứ 3 trong danh sách
```

![querySelectorAll](./images/008.png 'querySelectorAll')

## 5. HTML Collection

```html
<body>
    <h1 class="title">F8 - HTML DOM</h1>

    <h2 class="heading-2">Heading 2.1</h2>
    <h2 class="heading-2">Heading 2.2</h2>

    <form action="" class="form-1">Đăng ký</form>
    <form action="" class="test">Form test</form>
    <form action="" class="form-2">Đề nghị</form>

    <a href="https://youtube.com" name="Youtube">Youtube</a>
    </div>

    <script src=".\main.js"></script>
  </body>
```

- Với HTML Collection cho phép chọn trực tiếp 1 số đối tượng từ document trực tiếp có hỗ trợ như:
  - Form
  - Archer: liên kế link

```js
var listForm = document.forms;
console.log(listForm);
console.log(listForm[1]);
console.log(document.forms['form-1']);

console.log(document.forms.test);
console.log(document.anchors);
```

![HTML Collection](./images/009.png 'HTML Collection')

- Nghiên cứu thêm [HTML Collection](https://www.w3schools.com/jsref/dom_obj_htmlcollection.asp) https://www.w3schools.com/jsref/dom_obj_htmlcollection.asp
