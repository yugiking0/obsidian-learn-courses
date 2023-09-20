# Event listener

---


  - [Khái niệm](#1-khái-niệm)
  - [Khi nào sử dụng](#2-khi-nào-sử-dụng)
  - [Cách dùng của DOM Event](#3-cách-dùng-của-dom-event)
  - [Cách dùng Event listener](#4-cách-dùng-event-listener)
    - [Xử lý nhiều sự kiện event](#41-xử-lý-nhiều-sự-kiện-event)
    - [Lắng nghe/ hủy bỏ lắng nghe](#42-lắng-nghe-hủy-bỏ-lắng-nghe)
  - [Sự khác nhau giữa DOM Event và addEventListener](#5-sự-khác-nhau-giữa-dom-event-và-addeventlistener)

---

## 1. Khái niệm

- Ngoài cách dùng để thêm sự kiện vào Element bằng DOM Event methods: onclick, ondblclick, onmouseout,... thì DOM còn cung cấp thêm một công cụ là Event listener để đa dạng cách gán sự kiện cho một tao tác nào đó khi tác động lên đối tượng Element

## 2. Khi nào sử dụng

- Xử lý nhiều sự kiện khi event xảy ra.
- Lắng nghe/ hủy bỏ lắng nghe các sự kiện xảy ra cùng lúc.

## 3. Cách dùng của DOM Event

- Xét ví dụ khi cần gán cho 1 button thực hiện nhiều công việc khi click

```html
<body>
  <button>Click me!!</button>
</body>
```

```js
var btn = document.querySelector('button');

btn.onclick = function (e) {
  // Việc 1
  console.log('Viec 1');

  // Việc 2
  console.warn('Viec 2');

  // Việc 3
  console.error('Viec 3');
};
```

![DOM Event](Javascript/f8.javascrip.basic/detail/phan04-086/images/001.png 'DOM Event')

- Xử lý nút `Click me!!` chỉ hiệu lực khi trang web load xong sau 3s.

```js
setTimeout(() => {
  btn.onclick = function (e) {
    // Việc 1
    console.log('Viec 1');

    // Việc 2
    console.warn('Viec 2');

    // Việc 3
    console.error('Viec 3');
  };
}, 3000);
```

- Chặn việc thực hiện nút `Click me!!` sau 3 giây

```js
var btn = document.querySelector('button');

btn.onclick = function (e) {
  // Việc 1
  console.log('Viec 1');

  // Việc 2
  console.warn('Viec 2');

  // Việc 3
  console.error('Viec 3');
};

setTimeout(() => {
  btn.onclick = function () {};
}, 3000);
```

- Bài toán là: ở trường hợp nào đó thì chỉ xử lý `Viec 1` và `Viec 3` mà không xử lý `Viec 2` khi click nút `Click me!!` thì sẽ thế nào? Cụ thể sau 3s khi bấm click chỉ thực hiện việc `Viec 1` và `Viec 3`, không xử lý `Viec 2`

- Với DOM Event thì phải gán lại nút `Click me!!` khi click như sau:

```js
var btn = document.querySelector('button');

btn.onclick = function (e) {
  // Việc 1
  console.log('Viec 1');

  // Việc 2
  console.warn('Viec 2');

  // Việc 3
  console.error('Viec 3');
};

setTimeout(() => {
  btn.onclick = function (e) {
    // Việc 1
    console.log('Viec 1');

    // Việc 3
    console.error('Viec 3');
  };
}, 3000);
```

- Việc xử lý với DOM Event rườm rà và gán đi gán lại phức tạp sẽ gây khó khăn cho việc bổ sung hay chỉnh sửa sau này, với những trường hợp có xử lý loại bỏ chặn sự kiện Event thì nên dùng phương thức `EventListener` sẽ phù hợp hơn.

## 4. Cách dùng Event listener

- Xử lý nhiều sự kiện khi event xảy ra.
- Lắng nghe/ hủy bỏ lắng nghe các sự kiện xảy ra cùng lúc.

### 4.1 Xử lý nhiều sự kiện event

- Với `Event listener` thêm một sự kiện vào `Element`

```js
var btn = document.querySelector('button');

btn.addEventListener('click', function (e) {
  // Việc 1
  console.log('Viec 1');

  // Việc 2
  console.warn('Viec 2');

  // Việc 3
  console.error('Viec 3');
});
```

- Hoặc tạo từng công việc tương ứng với mỗi lần `addEventListener`

```js
var btn = document.querySelector('button');

// Việc 1
btn.addEventListener('click', function (e) {
  console.log('Viec 1');
});

// Việc 2
btn.addEventListener('click', function (e) {
  console.warn('Viec 2');
});

// Việc 3

btn.addEventListener('click', function (e) {
  console.error('Viec 3');
});
```

- Hoặc tạo theo các Callback

```js
var btn = document.querySelector('button');

// Việc 1
function viec1() {
  console.log('Viec 1');
}

// Việc 2
function viec2() {
  console.warn('Viec 2');
}

// Việc 3
function viec3() {
  console.error('Viec 3');
}

btn.addEventListener('click', viec1);
btn.addEventListener('click', viec2);
btn.addEventListener('click', viec3);
```

### 4.2 Lắng nghe/ hủy bỏ lắng nghe

- Xử lý nút `Click me!!` chỉ hiệu lực khi trang web load xong sau 3s.

```js
var btn = document.querySelector('button');

// Việc 1
function viec1() {
  console.log('Viec 1');
}

// Việc 2
function viec2() {
  console.warn('Viec 2');
}

// Việc 3
function viec3() {
  console.error('Viec 3');
}

setTimeout(function () {
  btn.addEventListener('click', viec1);
  btn.addEventListener('click', viec2);
  btn.addEventListener('click', viec3);
}, 3000);
```

- Chặn việc thực hiện nút `Click me!!` sau 3 giây, lúc này ta dùng Method `removeEventListener`

```js
var btn = document.querySelector('button');

// Việc 1
function viec1() {
  console.log('Viec 1');
}

// Việc 2
function viec2() {
  console.warn('Viec 2');
}

// Việc 3
function viec3() {
  console.error('Viec 3');
}

// addEventListener : Thêm event vào Button
btn.addEventListener('click', viec1);
btn.addEventListener('click', viec2);
btn.addEventListener('click', viec3);

// RemoveEventListener : Hủy event 
setTimeout(function () {
  btn.removeEventListener('click', viec1);
  btn.removeEventListener('click', viec2);
  btn.removeEventListener('click', viec3);
}, 3000);

```

- Bài toán là: ở trường hợp nào đó thì chỉ xử lý `Viec 1` và `Viec 3` mà không xử lý `Viec 2` khi click nút `Click me!!` thì sẽ thế nào? Cụ thể sau 3s khi bấm click chỉ thực hiện việc `Viec 1` và `Viec 3`, không xử lý `Viec 2`
```js
var btn = document.querySelector('button');

// Việc 1
function viec1() {
  console.log('Viec 1');
}

// Việc 2
function viec2() {
  console.warn('Viec 2');
}

// Việc 3
function viec3() {
  console.error('Viec 3');
}

// addEventListener : Thêm event vào Button
btn.addEventListener('click', viec1);
btn.addEventListener('click', viec2);
btn.addEventListener('click', viec3);

// RemoveEventListener : Hủy event 
setTimeout(function () {
  btn.removeEventListener('click', viec2);
}, 3000);
```
![addEventListener](Javascript/f8.javascrip.basic/detail/phan04-086/images/002.png 'addEventListener')

## 5. Sự khác nhau giữa DOM Event và addEventListener
