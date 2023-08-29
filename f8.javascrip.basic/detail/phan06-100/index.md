# Let & Const

---

**Tóm tắt:**

1. **Var** vs **Let,Const**
   - Scope : Phạm vi truy cập vào biến
   - Hosting : Đưa lên trên đầu (Cẩu lên)
2. **Const** vs **Let, Var**
   - Assignment : Gán lại giá trị

---

## 1. Var / Let, Const

### 1.1 Scope : Phạm vi truy cập

- Scope: Phạm vi hiệu lực truy cập của Biến có sự khác nhau khi khởi tạo bằng Var và khởi tạo bằng Let hoặc Const
- Scope phạm vi truy cập liên quan đến khối code (code block)
  - Code Block: trong khối lệnh if/else, các vòng lặp (loop), hay đơn giản trong khối code trong cặp ngoặc `{}`,...
  -
- Ví dụ với var:

```js
if(true){
  var a = 'Javascript';
}
console.log(a);
// Javascript

//-- Hoặc viết lại---

{
  var a = 'Javascript';
}

console.log(a);
// Javascript
```

- Ví dụ với let, const:

```js
{
  let a = 'Javascript';
}

console.log(a);
// app.js:6 Uncaught ReferenceError: a is not defined
```

- Với const

```js
{
  const a = 'Javascript';
}

console.log(a);
// app.js:6 Uncaught ReferenceError: a is not defined
```

- Đều thông báo là biến a chưa được định nghĩa.
- Như vậy, let/const sẽ không hiểu được khai báo khởi tạo nằm ở trong khối Code Block.
- Tính thừa hưởng khai báo vào trong

```js
{
  var a = 'Javascript';
  let b = 'CSS';
  const c = 'html';

  {
    {
      console.log(a);
      console.log(b);
      console.log(c);
    }
  }
}

//Javascript
//CSS
//html
```
- Lưu ý trường hợp đặc biệt của khai báo lại

```js
{
    var a = "Javascript";
    const a = "CSS";
    {
        {
            console.log(a);
        }
    }
}
// Uncaught SyntaxError: Identifier 'a' has already been declared

{
    var a = "Javascript";
    {
        const a = "CSS";
        {
            console.log(a);
        }
    }
}
//CSS

{
    var a = "Javascript";
    {
        const a = "CSS";
        {
            const a = "html";
            console.log(a);
        }
    }
}
//html
```

- Như vậy, khai báo biến và giá trị sẽ ưu tiên ở trong khối code cùng cấp sau đó là khối code cấp gần nhất chứa nó.

### 1.2 Hosting : Đưa lên trên đầu
- Đưa lên trên đầu : Viết lại code định nghĩa lên đầu đối với 1 số trường hợp cho phép Hosting
- Ví dụ với Var 

```js
a = "Javascript";
console.log(a);
var a;

//Javascript
```
- Nếu dùng Let và Const

```js
a = "Javascript";
console.log(a);
let a;
//Uncaught ReferenceError: Cannot access 'a' before initialization

a = "Javascript";
console.log(a);
const a;
//Uncaught SyntaxError: Missing initializer in const declaration
```
- Sẽ bị báo lỗi, nguyên nhân là var có hỗ trợ Hosting và trình duyệt sẽ viết lại khai báo đưa lên đầu.

```js
//Code 
var a =  1;

// ES6 viết lại
var a;
a = 1;
```

- ở ví dụ trên Hosting khai báo ở dưới được đưa lên trên.

```js
//Code 
a = "Javascript";
console.log(a);
var a;

// ES6 viết lại
var a;
a = "Javascript";
console.log(a);
//Javascript
```

![Hosting](./images/003.png 'Hosting')
- Như vậy với khai báo `var` hỗ trợ **Hosting**, còn khai báo `let` và `const` không hỗ trợ **Hosting**
Xem thêm:
- https://niithanoi.edu.vn/hoisting-trong-javascript.html
- https://viblo.asia/p/hoisting-javascript-WAyK8RmmlxX
- https://anonystick.com/blog-developer/hoisting-javascript-la-gi-hoisting-tot-hay-xau-chi-can-1-phut-de-hieu-2020051681168206

## 2. Const / Let, Var
- **Assignment** : Gán giá trị, với khai báo `Const`(_CONSTANT_) - `Hằng số` thì không gán lại được giá trị cho biến thuộc loại - Kiểu tham trị. Xem thêm ở


### 2.1 Assignment Primitive Types
- Gán lại giá trị cho biến tham trị.
- Xét ví dụ sau: 

```js
let a = 'PHP';
console.log("Biến a:", a); // Biến a: PHP

// --- Gán lại ---
a = 'Javascript'
console.log("Biến a:", a); // Biến a: Javascript
```

- Với const sẽ bị báo lỗi

```js
const a = 'PHP';
console.log("Biến a:", a); // Biến a: PHP

// --- Gán lại ---
a = 'Javascript'
//Uncaught TypeError: Assignment to constant variable.
```

- Như vậy với kiểu `Primitive Types` sẽ không gán lại giá trị được khi sử dụng khai báo `const`


### 2.2 Assignment Reference Types Types
- Gán lại giá trị cho biến tham chiếu.
- Xét ví dụ khi gán lại giá trị cho cả đối tượng kiểu tham chiếu, sẽ xuất hiện lỗi gán giá trị như kiểu biến tham trị. 

```js
const cat = {
    name: "Tom",
    age: 5
};
console.log("Mèo Tom:", cat); 
// Mèo Tom: {name: 'Tom', age: 5}

// --- Gán lại ---
cat = {
    name: "Tom",
    age: 2
};
// Assignment to constant variable.
```

- Nếu gán lại giá trị cho thành phần của đối tượng thì vẫn cho phép.

```js
const cat = {
    name: "Tom",
    age: 5
};
console.log("Mèo Tom:", cat); 
// Mèo Tom: {name: 'Tom', age: 5}

// --- Gán lại ---
cat.age = 3; 
console.log("Mèo Tom:", cat); 
// Mèo Tom: {name: 'Tom', age: 3}
```

- Hay như mảng Array, cho phép thay đổi giá trị index như sau:

```js
const cars = ['Mazda','Toyota','Hyundai'];
console.log('Item index 0: ',cars[0]);
// Item index 0:  Mazda

console.log('----------');
cars[0] = 'Ford'
console.log('Item index 0: ',cars[0]);
// Item index 0:  Ford
```

## 3. Tổng kết

![Const](./images/004.png 'Const')

---