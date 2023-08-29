# Tìm hiểu thêm về querySelector và querySelectorAll

---

- Nghiên cứu sử dụng querySelector và querySelectorAll để lấy các phần tử Element theo CSS Selector

```js
  <div type="checkbox" value="1" name="answer"></div>
  <input type="checkbox" value="1" name="answer" />
  <input type="checkbox" value="2" name="answer" checked />
  <input type="checkbox" value="3" name="answer" disabled />
  <input type="checkbox" value="4" name="answer" checked disabled />
  <p>Nguyên liệu:</p>
  <ul class="menu" id="ul02">
    <li class="class1" id="id0101">Trứng: 3 quả</li>
    <li class="class1" id="id0102">Cá thác lác: 200 gr</li>
    <li class="class1" id="id0103">Thịt nạc băm: 100 gr</li>

    <ul id="ul02">
      <li class="class2" id="id0201">Hành lá</li>
      <li class="class2" id="id0202">Ớt sừng băm</li>

      <ul id="ul03">
        <li>Muối</li>
        <li>Nước mắm</li>
        <li>Bột ngọt</li>
      </ul>
    </ul>
  </ul>
```

### 1. Chọn .class

#### getElementsByClassName

- Lấy các Elements của `class="class1"`
- Không cần dấu chấm khi dùng `getElementsByClassName`

```js
var class1 = document.getElementsByClassName('class1');
console.log(class1);

var class1 = document.getElementsByClassName('class1');
for (var i of class1) {
  console.log(i);
}
```

![getElementsByClassName](./images/css-001.png 'getElementsByClassName')

#### querySelectorAll

- Không thể dùng `querySelector`: vì chỉ lấy được 1 phần tử Element đầu tiên.
- `querySelectorAll` khi này cần thêm dấu chấm '.'

```js
var class1 = document.querySelectorAll('.class1');
console.log(class1);
for (var i of class1) {
  console.log(i);
}
```

![querySelectorAll](./images/css-002.png 'querySelectorAll')

### 2. Chọn .class1.class2

- Chọn những element có class kiểu `class="class1 class2"` hoặc `class="class2 class1"`
- Lấy các Element là: Trứng, thịt, cá.

```html
<ul>
  <li class="menu class1">Trứng</li>
  <li class="menu class1">Thịt</li>
  <li class="menu class1">Cá</li>
  <li>Rau</li>
  <li>Củ</li>
</ul>
```

```js
var items = document.querySelectorAll('.menu.class1');
console.log(items);

for (var i of items) {
  console.log(i);
}
```

![querySelectorAll](./images/css-003.png 'querySelectorAll')

### 3. Chọn .class1 .class2

- Chọn tất cả các phần tử Element có class2 là con của một phần tử có class1

```html
<ul class="menu">
  <li class="class1 class2">Trứng</li>
  <li class="class1">Thịt</li>
  <li class="class1">Cá</li>

  <li class="class2">Rau</li>
  <li class="class2">Củ</li>
</ul>
<div class="menu class2">Cơm gà</div>
```

- Chọn: Trứng, Rau, Củ.
- Những phần tử này nằm trong `class="menu"` và có `class="class2"`

```js
var items = document.querySelectorAll('.menu .class2');
console.log(items);

for (var i of items) {
  console.log(i);
}

// Ngược lại sẽ không có giá trị
console.log(document.querySelectorAll('.class2 .menu')); // NodeList []
```

![querySelectorAll](./images/css-004.png 'querySelectorAll')
