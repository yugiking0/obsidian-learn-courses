# Template Literals
---
- Template literals
- Multi-line String

## 1. Nội Dung
- Template literals: Sử dụng biến nội suy
- Multi-line String: Viết nhiều dòng.

## 2. Cách sử dụng
### 2.1 Template literals
- Xét ví dụ nối câu như sau:

```js
const carName = "Accent";
const brandName = "Hyundai";
const price = 500;

var description = carName 
  + " of " + brandName 
  + " has price is " + price;
console.log(description);
```

- Sử dụng Template literals nội suy sẽ dùng dấu như sau:

```js
const carName = "Accent";
const brandName = "Hyundai";
const price = 500;

description = `${carName} of ${brandName}`
  + ` has price is ${price}`;
console.log(description);
```
### 2.2 Multi-line String

- Để viết nhiều dòng có thể dùng ký tự `\n` để xuống dòng như sau:

```js
const lines = 'Line 1\n'
  + 'Line 2\n'
  + 'Line 3\n'

console.log(lines);
// Line 1
// Line 2
// Line 3
```

- Hoặc dùng Template literals với nội suy, sẽ giữa được cấu trúc.

```js
const lines = `Line 1
Line 2
Line 3`;

console.log(lines);
// Line 1
// Line 2
// Line 3
```