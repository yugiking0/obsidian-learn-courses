# DOM events example

---

- Ta có file html như sau:

```html
 <body>
    <button type="submit" id="load-id">Load</button>

    <input type="text"></input>
    <input type="checkbox"></input>
    <select>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
    </select>

  </body>
```

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log(inputElements[0].value); // Giá trị input text
  console.log(inputElements[1].checked); // Trạng thái check/ không check true/false
  console.log(selectOption.value); // Giá trị option được select
}

var inputElements = document.querySelectorAll('input');
var selectOption = document.querySelector('select');
```

![Get Value](Javascript/f8.javascrip.basic/detail/phan04-084/images/001.png 'Get Value')

## 1. Lấy Event từ Input/Select

- Lấy đối tượng Elements để xử lý

- Xem lại mục:

```js
document.querySelector('input[type=text]');
document.querySelector('input[type="text"]');
document.querySelector('input[type=checkbox]');
document.querySelector('select');
```

### 1.1 Lấy Value Input text

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log('Input value 1: ', inputElement.value);
  console.log('Input value 2: ', inputValue);
}

// Lấy Element của Input với type ="text"
var inputElement = document.querySelector('input[type=text]');
var inputValue;
// Event Blur = LostFocuse
inputElement.onchange = function (e) {
  console.log(e.target);
  console.log('Input value: ', e.target.value);
};

// Event onChange when change input character - Thay đổi mỗi khi thay đổi ký tự
inputElement.oninput = function (e) {
  //   console.log('Onchange Value: ', e.target.value);
  inputValue = e.target.value;
};
```

![Get onchange Value](Javascript/f8.javascrip.basic/detail/phan04-084/images/002.png 'Get onchange Value')

- Có thể gán giá trị mỗi khi onInput cho biến inputValue, để xử lý như tra cứu tên theo danh mục.

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log('onInput value: ', inputValue);
}

var inputElement = document.querySelector('input[type="text"]');
var inputValue;

inputElement.onchange = function (e) {
  console.log('Input value: ', e.target.value);
};

inputElement.oninput = function (e) {
  inputValue = e.target.value;
};
```

![Get onchange Value](Javascript/f8.javascrip.basic/detail/phan04-084/images/003.png 'Get onchange Value')

### 1.2 Lấy Value Input checkbox

- Để lấy giá trị nút checkbox, đầu tiên cần lấy được Element Checkbox
- Mỗi lần xử lý check hoặc bỏ check, sẽ làm thay đổi giá trị của ô này.
- Để lấy được Element Checkbox ta dùng câu lệnh

```js
var checkboxElement = document.querySelector('input[type=checkbox]');

checkboxElement.onchange = function (e) {
  console.log(e);
};
```

![Element Checkbox](Javascript/f8.javascrip.basic/detail/phan04-084/images/004.png 'Element Checkbox')

- Ở sự kiện mỗi lần thay đổi checkbox, xác định có target: input
- Kiểm tra e.target

```js
var checkboxElement = document.querySelector('input[type=checkbox]');

checkboxElement.onchange = function (e) {
  console.log(e.target);
};
```

![Element Checkbox](Javascript/f8.javascrip.basic/detail/phan04-084/images/005.png 'Element Checkbox')

- Để lấy giá trị nút checkbox

```js
var checkboxElement = document.querySelector('input[type=checkbox]');

checkboxElement.onchange = function (e) {
  console.log(e.target.value);
};
```

![Element Checkbox](Javascript/f8.javascrip.basic/detail/phan04-084/images/006.png 'Element Checkbox')

- Có thể xử lý tạo 1 biến, lấy giá trị mỗi khi onchange checkbox gán cho biến này như sau:

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log('Checkbox Value: ', checkboxValue);
}

var checkboxElement = document.querySelector('input[type=checkbox]');
var checkboxValue = false;

checkboxElement.onchange = function (e) {
  checkboxValue = e.target.checked;
};
```

![Element Checkbox](Javascript/f8.javascrip.basic/detail/phan04-084/images/007.png 'Element Checkbox')

### 1.3 Lấy Value Select Options

- Cách xử lý để lấy `Element Select Value` cũng sẽ thực hiện theo từng bước như sau:

  - lấy `Element Select` :
    `var selectElement = document.querySelector('select');`
  - Mỗi lần thay đổi chọn option, nên sự kiện sẽ là `onChange`
  - Lấy e.target, và kiểm tra giá trị khi `console.log(e.target)`
  - Xác định giá trị sẽ là `e.target.value`
  - Như vậy giá trị của Select cũng sẽ tương tự là: `selectElement.value;`

- Kiểm tra onchange event

```js
var selectElement = document.querySelector('select');

selectElement.onchange = function (e) {
  console.log(e);
};
```

![Element Select](Javascript/f8.javascrip.basic/detail/phan04-084/images/008.png 'Element Select')

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log('Select Value: ', selectElement.value);
}

var selectElement = document.querySelector('select');

selectElement.onchange = function (e) {
  console.log(e.target);
  console.log([e.target]);
};
```

![Element Select](Javascript/f8.javascrip.basic/detail/phan04-084/images/009.png 'Element Select')

- Để lấy được giá trị sẽ dùng `e.target.value`, có thể gán giá trị này cho biến `Global` `selectValue` để xử lý:

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log('Select Value: ', selectValue);
}

var selectElement = document.querySelector('select');
var selectValue = 1;

selectElement.onchange = function (e) {
  selectValue = e.target.value;
  console.log(selectValue);
};
```

![Element Select](Javascript/f8.javascrip.basic/detail/phan04-084/images/010.png 'Element Select')

> **Lưu ý:** _Với **Select Option**, thì giá trị hiển thị Option và Value Option đôi khi sẽ có sự khác nhau._

- Ví dụ: Các Option thể hiện là `1,2,3` nhưng Value khi chọn lại là `value-01,value-02, value-03`

```html
  <body>
    <button type="submit" id="load-id">Load</button>
    <input type="text"></input>
    <input type="checkbox"></input>
    <select>
      <option value="value-01">1</option>
      <option value="value-02">2</option>
      <option value="value-03">3</option>
    </select>
  </body>
```

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log('Select Value 1: ', selectElement.value);
  console.log('Select Value 2: ', selectValue);
}

var selectElement = document.querySelector('select');
var selectValue;

selectElement.onchange = function (e) {
  selectValue = e.target.value;

  // Lựa chọn hiển thị 1, nhưng Value lại là value-01
  console.log(selectValue);
};
```

![Element Select](Javascript/f8.javascrip.basic/detail/phan04-084/images/011.png 'Element Select')

- Hoặc khi hiển thị cho người dùng User thể hiện mô tả rõ ràng, nhưng giá trị lựa chọn chỉ là id, sau đó xử lý ở Database Back-end sẽ xử lý id này với giá trị phù hợp khi được truyền đi.

- Các Option thể hiện là `Javascript , CSS, HTML` nhưng Value khi chọn lại là `1,2,3`

```html
  <body>
    <button type="submit" id="load-id">Load</button>
    <input type="text"></input>
    <input type="checkbox"></input>
    <select>
      <option value="1">Javascript</option>
      <option value="2">CSS</option>
      <option value="3">HTML</option>
    </select>
  </body>
```

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {
  console.log('Select Value 1: ', selectElement.value);
  console.log('Select Value 2: ', selectValue);
}

var selectElement = document.querySelector('select');
var selectValue;

selectElement.onchange = function (e) {
  selectValue = e.target.value;
  console.log(selectValue);
};
```

![Element Select](Javascript/f8.javascrip.basic/detail/phan04-084/images/012.png 'Element Select')

## 2. Key up/ Key down

- key Down: Khi nhấn phím xuống;
- key Up: Sau khi nhấn phím xuống, sự kiện xuất khi khi thả phím ra(Phím đi lên)
- key Press: Sự kiện khi nhấn phím.

```html
  <body>
    <button type="submit" id="load-id">Load</button>

    <input type="text"></input>

  </body>
```

```js
var btLoad = document.querySelector('#load-id');
btLoad.addEventListener('click', iniLoad);

function iniLoad() {}

var selectElement = document.querySelector('input[type=text]');

selectElement.onkeydown = function (e) {
  console.log(e);
};
```

![key Down](Javascript/f8.javascrip.basic/detail/phan04-084/images/013.png 'key Down')

- Sự kiện khi nhấn phím trên bàn phím keyboard xuống, với mỗi phím sẽ có giá trị mã số tương ứng bằng thuộc tính `which`
  - event.key: Giá trị của phím hiển thị màn hình. (a,b,c,Enter,Esc,Altr,@,#,...)
  - event.keyCode/event.which: Giá trị ACSII (a-65,b-66,c-67,Enter-13,Esc-27,Alt-18,@-50,#-51,...) Xem [Keycode](https://keycode.info/)
  - event.code: Vị trí của phím:
    - 1 - Digit1
    - 1 - Numpad1
    - ` - Backquote
    - Tab - Tab
    - F1 - F1
    - Xem [Keycode](https://keycode.info/)

```js
var selectElement = document.querySelector('input[type=text]');

selectElement.onkeypress = function (e) {
  console.log(e.key, e.keyCode);
  console.log(e.key, e.which);
};
```

![key Press](Javascript/f8.javascrip.basic/detail/phan04-084/images/014.png 'key Press')

- Một số mã phím quan trọng hay sử dụng khi bắt sự kiện như: Enter, Esc,...

- Mô tả xử lý event Key Mozilla [KeyboardEvent.keyCode](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/keyCode)

- Xem các giá trị phím tại [Keycode](https://keycode.info/)

- Bắt sự kiện bấm phím, có thể lấy cho cả màn hình trình duyệt khi xử lý như:

  - Esc thoát khỏi Popup, hoặc Text Input
  - Enter: Xác nhận, hoặc gửi nội dung chat ở Box-Chat
  - Gán phím nóng cho màn hình nhập liệu

- Với phím Esc cần xử lý lại, do đã bị chặn

```js
document.onkeydown = function (evt) {
  evt = evt || window.event;
  var isEscape = false;
  console.log([evt]);
  if ('key' in evt) {
    isEscape = evt.key === 'Escape' || evt.key === 'Esc';
  } else {
    isEscape = evt.keyCode === 27;
  }
  if (isEscape) {
    console.log('Exit!');
  }
};
```
