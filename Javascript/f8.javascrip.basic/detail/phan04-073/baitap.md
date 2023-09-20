# Bài tập

---

- [Bài tập](#bài-tập)
  - [Bài 01](#bài-01)
  - [Bài 02](#bài-02)
  - [Bài 03](#bài-03)
  - [Bài 04](#bài-04)
  - [Bài 05](#bài-05)
  - [Bài 06](#bài-06)

---

## Bài 01:

Cho trước DOM có cấu trúc HTML như sau:

```html
<main id="app">
  <header>
    <h1 id="first-heading">Học JS HTML DOM tại F8!</h1>
  </header>

  <div id="app-body">
    <h2 id="second-heading">Học qua video + làm bài tập!</h2>
  </div>
</main>
```

> Yêu cầu

1. Get element có ID app và lưu vào biến appElement
2. Get element có ID first-heading lưu vào biến firstHeadingElement
3. Get element có ID app-body lưu vào biến appBodyElement
4. Get element có ID second-heading lưu vào biến secondHeadingElement

```js
// Làm bài tập tại đây

var appElement = document.getElementById('app');
var firstHeadingElement = document.getElementById('first-heading');
var appBodyElement = document.getElementById('app-body');
var secondHeadingElement = document.getElementById('second-heading');
```

## Bài 02:

Cho trước DOM có cấu trúc HTML như sau:

```html
<div class="container">
  <div class="box">
    <ul>
      <li class="item">F8 lý thuyết</li>
      <li class="item">F8 bài tập</li>
      <li class="item">F8 thực hành</li>
    </ul>
  </div>
  <div class="box">
    <ul>
      <li class="item">Kiền trì</li>
      <li class="item">Học mỗi ngày</li>
      <li class="item">Tin vào bản thân</li>
    </ul>
  </div>
</div>
```

> Yêu cầu

1. Get elements box và lưu vào biến boxHTMLCollection
2. Lấy element box thứ nhất lưu vào biến box1Element
3. Lấy element box thứ hai lưu vào biến box2Element
4. Get tất cả li và lưu vào biến allItemElements
5. Get tất cả li là con của box thứ nhất và lưu vào biến box1ItemElements
6. Get tất cả li là con của box thứ hai và lưu vào biến box2ItemElements

```js
// Làm bài tập tại đây
var boxHTMLCollection = document.getElementsByClassName('box');
var box1Element = boxHTMLCollection[0];
var box2Element = boxHTMLCollection[1];
var allItemElements = document.getElementsByTagName('li');
var box1ItemElements = box1Element.getElementsByTagName('li');
var box2ItemElements = box2Element.getElementsByTagName('li');
```

## Bài 03:

Cho trước DOM có cấu trúc HTML như sau:

```html
<h1>Học lập trình tại F8</h1>

<section>
  <h2>Học JS HTML DOM</h2>
</section>

<div>
  <h3>Làm bài tập ngay trên F8</h3>
</div>
```

> Yêu cầu

1. Lấy h1 element và lưu vào biến h1Element
2. Lấy h2 element và lưu vào biến h2Element
3. Lấy h3 element và lưu vào biến h3Element

```js
// Làm bài tập tại đây
var h1Element = document.querySelector('h1');
var h2Element = document.querySelector('h2');
var h3Element = document.querySelector('h3');
```

## Bài 04:

Cho trước DOM có cấu trúc HTML như sau:

```html
<div class="box">getElementsByClassName trả về HTMLCollection</div>

<div class="box">getElementsByTagName cũng trả về HTMLCollection</div>
```

> Yêu cầu
> Get element box thứ hai lưu vào biến box2Element

```js
// Làm bài tập tại đây
var box2Element = document.getElementsByClassName('box')[1];
```

## Bài 05:

Cho trước DOM có cấu trúc HTML như sau:

```html
<div type="checkbox" value="1" name="answer"></div>
<input type="checkbox" value="1" name="answer" />
<input type="checkbox" value="2" name="answer" checked />
<input type="checkbox" value="3" name="answer" disabled />
<input type="checkbox" value="4" name="answer" checked disabled />
```

> Yêu cầu

1. Get checkbox input NodeList lưu vào biến checkboxNodes
2. Get checkbox input element có type="checkbox" value="1" lưu vào biến checkbox1Element
3. Get checkbox element có attribute checked nhưng không có attribute disabled lưu vào biến checkboxCheckedAndNotDisabled
4. Get checkbox element có attribute disabled nhưng không có attribute checked lưu vào biến checkboxDisabledAndNotChecked
5. Get checkbox element có attribute checked và disabled lưu vào biến checkboxCheckedAndDisabled

```js
// Làm bài tập tại đây
var checkboxNodes = document.getElementsByTagName('input');

for (var i of checkboxNodes) {
  console.log(i.checked);
  if (i.value == 1) {
    var checkbox1Element = i;
  }
  if (i.checked == 1 && i.disabled == 0) {
    var checkboxCheckedAndNotDisabled = i;
  }
  if (i.disabled == 1 && i.checked == 0) {
    var checkboxDisabledAndNotChecked = i;
  }
  if (i.disabled == 1 && i.checked == 1) {
    var checkboxCheckedAndDisabled = i;
  }
}
```

```js
var checkboxNodes = document.querySelectorAll('input');
var checkbox1Element = document.querySelector('input[value="1"]');

var checkboxCheckedAndNotDisabled = document.querySelector(
  'input:checked:not(disabled)'
);

var checkboxDisabledAndNotChecked = document.querySelector(
  'input:disabled:not(checked)'
);

var checkboxCheckedAndDisabled = document.querySelector(
  'input:checked:disabled'
);
```

```js
var checkboxNodes = document.getElementsByTagName('input');
var checkbox1Element = document.querySelector(
  'input[type="checkbox"][value="1"]'
);
var checkboxCheckedAndNotDisabled = document.querySelector(
  '[type="checkbox"]:checked:not(disabled)'
);
var checkboxDisabledAndNotChecked = document.querySelector(
  '[type="checkbox"]:disabled:not(checked)'
);
var checkboxCheckedAndDisabled = document.querySelector(
  '[type="checkbox"]:checked:disabled'
);
```

```js
var checkboxNodes = document.querySelectorAll('input');
var checkbox1Element = document.querySelector('input[value = "1"]');
var checkboxCheckedAndNotDisabled = document.querySelector('input:checked');
var checkboxDisabledAndNotChecked = document.querySelector('input:disabled');
var checkboxCheckedAndDisabled = document.querySelector(
  'input:disabled:checked'
);

///---------------------------
var checkboxNodes = document.querySelectorAll("input[type='checkbox']");
const checkbox1Element = document.querySelector(
  "input[type='checkbox'][value='1']"
);
const checkboxCheckedAndNotDisabled = document.querySelector(
  "input[type='checkbox'][checked]:not([disabled])"
);
const checkboxDisabledAndNotChecked = document.querySelector(
  'input[disabled]:not([checked])'
);
const checkboxCheckedAndDisabled = document.querySelector(
  'input[checked][disabled]'
);

///---------------------------
var checkboxNodes = document.querySelectorAll('input[type="checkbox"]');
var checkbox1Element = document.querySelector(
  'input[type="checkbox"][value="1"]'
);
var checkboxCheckedAndNotDisabled = document.querySelector(
  '[checked]:not([disabled])'
);
var checkboxDisabledAndNotChecked = document.querySelector(
  '[disabled]:not([checked])'
);
var checkboxCheckedAndDisabled = document.querySelector('[checked][disabled]');
```

## Bài 06:

Cho trước DOM có cấu trúc HTML như sau:

```html
<ul class="parent">
  <li>"Cày" JS DOM tại F8</li>
  <li>"Cày" JS DOM tại F8</li>

  <ul>
    <li>"Cày" JS DOM tại F8</li>
    <li>"Cày" JS DOM tại F8</li>

    <ul>
      <li>"Cày" JS DOM tại F8</li>
      <li>"Cày" JS DOM tại F8</li>
    </ul>
  </ul>
</ul>
```

> Yêu cầu

1. Get list elements li là con trực tiếp của ul thứ nhất và lưu vào biến listItems1
2. Get list elements li là con trực tiếp của ul thứ hai và lưu vào biến listItems2
3. Get list elements li là con trực tiếp của ul thứ nhất và ul thứ hai sau đó lưu vào biến listItems3

```js
// Làm bài tập tại đây

var listItems1 = document.querySelectorAll('.parent > li');
var listItems2 = document.querySelectorAll('.parent > ul > li');
var listItems3 = document.querySelectorAll('.parent > li,.parent > ul > li');
```

```js
var listItems1 = document.querySelectorAll('ul:nth-child(1)>li');
var listItems2 = document.querySelectorAll('ul:nth-child(1)>ul>li');
var listItems3 = document.querySelectorAll(
  'ul:nth-child(1)>li,ul:nth-child(1)>ul>li'
);

//-------------------
var listItems1 = document.querySelectorAll('.parent>li');
var listItems2 = document.querySelectorAll('.parent>ul>li');
var listItems3 = [...listItems1, ...listItems2];

//-------------------
var listItems1 = document.querySelectorAll('ul:first-child > li');
var listItems2 = document.querySelectorAll('ul:first-child > ul > li');
var listItems3 = Array.from(listItems1).concat(Array.from(listItems2));
```

---
