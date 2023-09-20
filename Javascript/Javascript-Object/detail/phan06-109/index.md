# Modules

---

## 1. Lý thuyết

- `Modules` là việc bóc tách một chức năng thành phần ra thành một nơi riêng dễ quản lý.
- Thường sẽ tách thành file, hoặc tập hợp các file.
- Một phần mềm MVC sẽ tách ra các thành phần(Model-View-Controller) và từng phần có thể tách nhỏ thành các chức năng nhỏ hơn.
- Để sử dụng Modules trong Javascript thì sẽ cần:
  - Export
  - Import
  - Khai báo dạng type ='Module'

## 2. Các thao tác

### 2.1 Khởi tạo ban đầu

- Tạo 2 file như sau:

```js
demo-modules
├─ index.html
└─ app.js
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Modules</title>
    <style>
      body {
        height: 100vh;
        align-items: center;
        background: linear-gradient(to top left, #28b487, #7dd56f);
      }
    </style>
  </head>
  <body></body>
  <script src="./app.js"></script>
</html>
```

- và app.js

```js
console.log('Hello World!');
console.warn('Alert!!!');
console.error('Bugzzz!');
```

![Console](Javascript/Javascript-Object/detail/phan06-109/images/001.png 'Console')

### 2.2 Ta viết lại thành hàm logger

- Thay đổi ta sẽ viết lại hàm logger trong app.js xử lý như sau:

```js
function logger(message, type = 'log') {
  return console[type](message);
}

logger('Hello World!');
logger('Alert!!!', 'warn');
logger('Bugzzz!', 'error');
```

### 2.3 Tách hàm logger riêng ra 1 file logger.js

```js
demo-modules
├─ index.html
├─ app.js
└─ logger.js
```

- Khi này hàm ở file app.js cần import hàm logger từ file logger.js vào:

- Khi này file app.js sẽ có kiểu:

```js
logger('Hello World!');
logger('Alert!!!', 'warn');
logger('Bugzzz!', 'error');

// app.js:3 Uncaught ReferenceError: logger is not defined
```

- Sẽ bị báo lỗi do chưa nhận biết khai báo hàm logger, xử lý tình trạng này ta thêm Import vào. `import logger from './logger.js';`

```js
import logger from './logger.js';

logger('Hello World!');
logger('Alert!!!', 'warn');
logger('Bugzzz!', 'error');

// Uncaught SyntaxError: Cannot use import statement outside a module
```

- Phần mềm vẫn báo lỗi do chưa xác định kiểu file app.js là module, nên chỗ này cần xử lý thêm ở file index.html tại `type="module"`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Modules</title>
  </head>
  <body></body>
  <script type="module" src="./app.js"></script>
</html>
```

- Khi này sẽ không báo lỗi nữa, nhưng không log được thông tin.

### 2.4 Khai báo Export ở file logger.js

```js
function logger(message, type = 'log') {
  return console[type](message);
}

export default logger;
```

- Để ý thấy có `export default logger` cần Export ra ngoài đối tượng mặc định là logger.
- Trong 1 file khi Export ra sẽ có 1 đối tượng/ hàm là default mặc định, còn lại có thể export theo kiểu thường là đối tượng.
- Ta xử lý các trạng thái type là: log, warn, error

```js
export const TYPE_LOG = 'log';
export const TYPE_WARN = 'warn';
export const TYPE_ERROR = 'error';

function logger(message, type = TYPE_LOG) {
  return console[type](message);
}

export default logger;
```

- Thì bên app.js sẽ import vào sẽ như sau:

```js
import logger, {TYPE_LOG, TYPE_WARN, TYPE_ERROR} from './logger.js';

logger('Hello World!');
logger('Alert!!!', TYPE_WARN);
logger('Bugzzz!', TYPE_ERROR);
```

### 2.5 Tách tiếp các khai báo Constant ra riêng file constant.js

- File constants.js sẽ là

```js
export const TYPE_LOG = 'log';
export const TYPE_WARN = 'warn';
export const TYPE_ERROR = 'error';
```

- File logger.js chỉ cần import TYPE_LOG để dùng khai báo mặc định như sau:

```js
import {TYPE_LOG} from './constant.js';

function logger(message, type = TYPE_LOG) {
  return console[type](message);
}

export default logger;
```

- File app.js sẽ khai báo thành:

```js
import logger from './logger.js';
import {TYPE_LOG, TYPE_WARN, TYPE_ERROR} from './constant.js';

logger('Hello World!');
logger('Alert!!!', TYPE_WARN);
logger('Bugzzz!', TYPE_ERROR);
```

## 3. Đảm bảo tính bảo mật code

```js
demo-modules
├─ log
│   ├─ index.js
│   ├─ constant.js
│   └─ logger.js
├─ index.html
└─ main.js
```

![modules](Javascript/Javascript-Object/detail/phan06-109/images/002.png 'modules')

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Modules</title>
  </head>
  <body>
    <h1>Modules</h1>
    <div id="app-id"></div>
    <button id="btn">Submit</button>
  </body>
  <script type="module" src="./main.js"></script>
</html>
```

- main.js

```js
// main.js
import logger from './log/index.js';
import {TYPE_LOG, TYPE_WARN, TYPE_ERROR} from './log/constant.js';

function init() {
  const btn = (document.querySelector('#btn').onclick = () => {
    // console.log('Hello World', Math.random());
    logger('Hello World');
    logger('Warning...', TYPE_WARN);
    logger('Error...', TYPE_ERROR);
  });
}

document.addEventListener('DOMContentLoaded', function () {
  init();
});
```
- log/constant.js

```js
// constant.js
const TYPE_LOG = 'log';
const TYPE_WARN = 'warn';
const TYPE_ERROR = 'error';

export {TYPE_LOG, TYPE_WARN, TYPE_ERROR};
```

- log/logger.js

```js
// logger.js
import {TYPE_LOG} from './constant.js';

function logger(message, type = TYPE_LOG) {
  console[type](message);
}

export default logger;
```

- log/index.js

```js
// index.js

export {default} from './logger.js';

```
