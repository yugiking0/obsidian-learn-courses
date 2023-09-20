# PEAN Stack Day 2 - Hoisting, Strict mode, Primitive Types & Reference Types, Deep Clone vs Shallow Clone

## **1. Hoisting**

### **1.1. Là gì vậy?**

Hoisting là một cơ chế trong Javascript khi biến và function declaration sẽ được "kéo lên" trước mọi thứ. Nghĩa là, dù bạn khai báo biến ở cuối file, Javascript "nghĩ" rằng bạn đã khai báo nó ở đầu file.

### **1.2. Ví dụ**

**Ví dụ 1:**

```javascript
console.log(x); // undefined chứ không phải lỗi
var x = 5;
console.log(x); // 5
```

Ở ví dụ trên, dù `x` được khai báo sau khi console.log nhưng vẫn không bị lỗi. Đó là nhờ hoisting đã "kéo" biến `x` lên trước!

**Ví dụ 2:** Dùng hàm trước khi khai báo

```javascript
sayHello(); // "Chào các bạn!"
function sayHello() {
    console.log("Chào các bạn!");
}
```

_Giải thích:_ Tại sao lại gọi hàm được trước khi nó được khai báo? Đơn giản, hoisting đã "kéo" function declaration `sayHello` lên trên cùng!

**Ví dụ 3:** Biến với `let` và `const` không hoisting như `var`

```javascript
console.log(name); // lỗi: cannot access 'name' before initialization
let name = "Mình";
```

_Giải thích:_ `let` và `const` cũng có hoisting nhưng không khởi tạo giá trị, vì thế chúng ta không thể truy cập trước khi khai báo.

**Ví dụ 4:** Hoisting trong function

```javascript
function showAge() {
    console.log(age); // undefined
    var age = 20;
}
showAge();
```

_Giải thích:_ Biến `age` được hoisted lên đầu hàm nhưng chỉ sau khi được khởi tạo mới có giá trị.

## **2. Strict mode**

Thế "Strict mode" là cái gì? Đơn giản, đó là cách để JavaScript trở nên nghiêm ngặt hơn, bắt lỗi chặt chẽ hơn.

### **2.1. Kích hoạt thế nào?**

Để kích hoạt "strict mode", chúng ta chỉ cần thêm câu lệnh `'use strict';` ở đầu file hoặc đầu function.

### **2.2. Tại sao cần "Strict mode"?**

Khi chúng ta code, đôi khi có những lỗi mà JavaScript bình thường sẽ bỏ qua. Nhưng với "strict mode", nó sẽ không để chúng ta làm điều đó.

### **2.3. Ví dụ**

**Ví dụ 1:** Không cho phép sử dụng biến mà không khai báo

```javascript
'use strict';
x = 10; // lỗi: x is not defined
```

_Giải thích:_ Strict mode không cho phép ta khởi tạo biến mà không dùng `var`, `let` hoặc `const`.

**Ví dụ 2:** Không cho phép xóa biến, hàm

```javascript
'use strict';
var y = 20;
delete y; // lỗi
```

_Giải thích:_ Trong strict mode, việc xóa biến, đối tượng hay hàm không được phép.

**Ví dụ 3:** Không cho phép trùng lặp tên tham số

```javascript
'use strict';
function sum(x, x) { // lỗi
    return x + x;
}
```

_Giải thích:_ Trong strict mode, việc khai báo hàm với tên tham số trùng lặp sẽ bị từ chối.

## **3. Primitive Types & Reference Types**

Đây chính là phần mình thích nhất, vì nó giải thích tại sao khi làm việc với object và array trong JavaScript, chúng ta thường gặp phải những lỗi khá lạ.

### **3.1. Primitive Types**

Là những kiểu dữ liệu cơ bản như: `Number`, `String`, `Boolean`, `null`, `undefined`, và `symbol`.

Khi bạn gán một giá trị primitive cho một biến khác, bạn đang "copy" giá trị đó. Ví dụ:

```javascript
let a = 5;
let b = a;
a = 10;

console.log(b); // 5, chứ không phải 10
```

### **3.2. Reference Types**

Gồm `Object` và `Array`. Khác với Primitive, khi bạn gán một object hoặc một array cho một biến khác, bạn đang "chỉ đến" cùng một tham chiếu.

```javascript
let obj1 = { name: "Mình" };
let obj2 = obj1;
obj1.name = "Các bạn";

console.log(obj2.name); // "Các bạn", chứ không phải "Mình"
```

### **3.3. Ví dụ**

**Ví dụ 1:** Gán giá trị cho một string

```javascript
let name = "Mình";
let newName = name;
newName = "Các bạn";

console.log(name); // "Mình"
```

_Giải thích:_ Strings là primitive types, nên khi gán, chúng ta copy giá trị thực.

**Ví dụ 2:** Sửa giá trị trong mảng

```javascript
let colors = ["đỏ", "xanh"];
let myColors = colors;
myColors.push("vàng");

console.log(colors); // ["đỏ", "xanh", "vàng"]
```

_Giải thích:_ Mảng là reference types, nên chúng ta chỉ đến cùng một tham chiếu.

**Ví dụ 3:** Clone một đối tượng

```javascript
let car1 = { brand: "Toyota" };
let car2 = {...car1};
car2.brand = "Mercedes";

console.log(car1.brand); // "Toyota"
```

_Giải thích:_ Sử dụng spread operator để "clone" giá trị, không phải tham chiếu.

## **4. Deep Clone vs Shallow Clone**

Trước hết, hãy hiểu rõ về hai khái niệm này:

- **Shallow Clone (Clone nông)**: Là việc sao chép một đối tượng tại cấp độ ngoài cùng. Nhưng các đối tượng con bên trong (nếu có) vẫn chỉ đến cùng một tham chiếu.
    
- **Deep Clone (Clone sâu)**: Là việc sao chép toàn bộ đối tượng, bao gồm cả các đối tượng con bên trong, tạo ra một bản sao hoàn toàn độc lập.
    

### **4.1. Shallow Clone**

**Ví dụ 1:** Sử dụng `Object.assign`

```javascript
let obj1 = { a: 10, b: { x: 20 } };
let obj2 = Object.assign({}, obj1);
obj2.b.x = 30;

console.log(obj1.b.x); // 30
```

_Giải thích:_ Mặc dù obj2 là một bản sao mới của obj1 nhưng obj2.b vẫn trỏ đến cùng một tham chiếu với obj1.b.

**Ví dụ 2:** Sử dụng spread operator

```javascript
let obj1 = { a: 10, b: { x: 20 } };
let obj2 = { ...obj1 };
obj2.b.x = 40;

console.log(obj1.b.x); // 40
```

_Giải thích:_ Tương tự như ví dụ 1, spread operator chỉ clone nông.

**Ví dụ 3:** Sử dụng mảng

```javascript
let arr1 = [1, [2, 3]];
let arr2 = [...arr1];
arr2[1][0] = 4;

console.log(arr1[1][0]); // 4
```

_Giải thích:_ Cùng một cơ chế, mảng con vẫn chỉ đến cùng một tham chiếu.

### **4.2. Deep Clone**

**Ví dụ 1:** Sử dụng `JSON`

```javascript
let obj1 = { a: 10, b: { x: 20 } };
let obj2 = JSON.parse(JSON.stringify(obj1));
obj2.b.x = 50;

console.log(obj1.b.x); // 20
```

_Giải thích:_ Kỹ thuật này sao chép toàn bộ đối tượng, nhưng không hoạt động với các giá trị đặc biệt như `undefined`, `function`, `Symbol`.

**Ví dụ 2:** Sử dụng thư viện như lodash

Nếu bạn sử dụng thư viện lodash:

```javascript
let _ = require('lodash');
let obj1 = { a: 10, b: { x: 20 } };
let obj2 = _.cloneDeep(obj1);
obj2.b.x = 60;

console.log(obj1.b.x); // 20
```

_Giải thích:_ lodash cung cấp hàm `cloneDeep` chuyên dụng để deep clone một đối tượng.

**Ví dụ 3:** Viết hàm deep clone

```javascript
function deepClone(obj) {
    if (obj === null) return null;
    let clone = Object.assign({}, obj);
    Object.keys(clone).forEach(
        key => (clone[key] = typeof obj[key] === 'object' ? deepClone(obj[key]) : obj[key])
    );
    return Array.isArray(obj) && obj.length ? (clone.length = obj.length) && Array.from(clone) : Array.isArray(obj) ? Array.from(obj) : clone;
}

let obj1 = { a: 10, b: { x: 20 } };
let obj2 = deepClone(obj1);
obj2.b.x = 70;

console.log(obj1.b.x); // 20
```

_Giải thích:_ Hàm này sẽ đệ quy sao chép tất cả các cấp độ của đối tượng.

