# Default parameter values

---

## 1. Nội dung

- Default parameter values: Định nghĩa giá trị mặc định cho tham số truyền vào Hàm Function

## 2. Cách dùng

- Ta có hàm in Logger ra như sau:

```js
function logger(message) {
  console.log('Log: ' + message);
}

logger('Message...');
// Log: Message...
logger();
// Log: undefined
```

- Sẽ sửa lại nếu như bỏ trống không đưa tham số vào thì sẽ in ra `Giá trị mặc định`.

```js
function logger(message) {
  if (message == undefined) {
    console.log('Giá trị mặc định');
  } else {
    console.log('Log: ' + message);
  }
}

logger('Message...');
logger();
```

- Với ES6 cung cấp cho tiện ích `Default parameter values` đễ xử lý hỗ trợ trường hợp này như sau:

```js
const logger = function (message = 'Gia tri mac dinh') {
  console.log('Log: ' + message);
};

logger('Message...');
logger();
```

- Thường sử dụng khi xử lý những tham số không bắt buộc phải nhập.
> `Xem ví dụ: Bình thường sẽ logger, còn nếu không truyền sẽ báo lỗi Error`

```js
function logger(message, type = 'log') {
  console[type](message);
}

logger('Message', 'error');
logger('Message');
```
