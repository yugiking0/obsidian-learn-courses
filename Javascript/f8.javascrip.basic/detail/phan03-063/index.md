# Callback

---

### 1. Callback là gì ?

> Là hàm (function) được truyền qua đối số khi được gọi bởi hàm khác.

- 1. Là hàm
- 2. Được truyền qua đối số

---

- [ ] Là một kiểu dữ liệu mới trong Javascript
- [ ] Là một khái niệm mới trong Javascript
- [ ] Là một giá trị mới trong javascript
- [x] **_Là một khái niệm nói lên cách hàm được sử dụng_**

### 2. Như thế nào được gọi là một callback ?

- [x] **_(1) Là một hàm. (2) Dùng làm đối số khi gọi hàm khác_**
- [ ] (1) Là một hàm. (2) Không đặt tên cho hàm
- [ ] Chỉ cần là một hàm
- [ ] (1) Là một giá trị khác function. (2) Được dùng làm đối số khi gọi hàm

---

### 3. Ví dụ:

```js
// 1. Ta có 1 hàm kiểm tra đối số truyền vào như sau:
function myFunction(param) {
  console.log('Kiểu dữ liệu: ', typeof param);
}

myFunction(123); // Kiểu dữ liệu:  number
myFunction('Javascript'); // Kiểu dữ liệu:  string

// 2. Tạo 1 hàm khác
function myCallback(myValue) {
  console.log('Giá trị:', myValue);
}

// 3. Truyền vào hàm trên
myFunction(myCallback); // Kiểu dữ liệu:  function

// 4. Gọi hàm
myCallback('Học lập trình Javascript');

// 5. Xử lý lại hàm myFunction
function myFunction(para) {
  para('Học lập trình Javascript');
}

// 6. Nhưng nếu vẫn xử lý là:
myFunction(123); // Uncaught TypeError: para is not a function
myFunction('Javascript'); // Uncaught TypeError: para is not a function

// 7. Khắc phục
function myFunction(para) {
  if (typeof para === 'function') {
    para('Học lập trình Javascript');
  }
}
```

---
