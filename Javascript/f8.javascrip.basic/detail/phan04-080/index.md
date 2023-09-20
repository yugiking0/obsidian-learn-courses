# Node Property

---

- Nghiên cứu thêm về các Node Property

```html
<div class="box box1 box2" title="box-title" id="box-id">
  <h1 title="heading">New Heading</h1>
</div>
```

```js
var boxElement = document.querySelector('.box');
console.log(typeof boxElement); // object

console.log(boxElement);
```

![Console](Javascript/f8.javascrip.basic/detail/phan04-080/images/001.png 'Console')

- Chuyển qua mảng Array thành Node List để mở xem các Property của Node Element

```js
var boxElement = document.querySelector('.box');
console.log([boxElement]);
```

![Console](Javascript/f8.javascrip.basic/detail/phan04-080/images/002.png 'Console')

## 2. Các Property hay thao tác

### 2.1 Attribute (Name Node Map)

![Attribute](003.0.png 'Attribute')
![Attribute](003.1.png 'Attribute')
![Attribute](003.2.png 'Attribute')
![Attribute](003.3.png 'Attribute')

### 2.2 contentEditable

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Demo</title>
    <style>
      body {
        height: 100vh;
        background: linear-gradient(to top left, #a9aaff, hsl(219, 83%, 61%));
      }
    </style>
  </head>

  <body>
    <button type="submit" id="load-id">Load</button>

    <div class="box">
      <h1 class="heading">New Heading</h1>
    </div>

    <div id="output"></div>
  </body>
  <script src="../main.js"></script>
</html>
```

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

var boxElement = document.querySelector('.box');
console.log([boxElement]);

function iniLoad() {
  // boxElement.contentEditable = true;
  // boxElement.autosize = true;
  // boxElement.autofocus = true;
  // boxElement.draggable = true;
  boxElement.hidden = true;
}
```

### 2.3 outerText và outerHtml

