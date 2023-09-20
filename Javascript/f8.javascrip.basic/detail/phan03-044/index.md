# Toán tử 3 ngôi (Ternary operator)

## Lý thuyết

Toán tử 3 ngôi hay còn được gọi là (Ternary operator) là toán tử duy nhất trong JavaScript cần tới ba toán hạng.

## Cú pháp:

> [Điều kiện] ? [Biểu thức nếu đúng] : [Biểu thức nếu sai]

Ví dụ 1:

```js
var age = 16;

console.log(age >= 18 ? 'Người lớn' : 'Trẻ con');
// Kết quả: Trẻ con

console.log(age > 12 && age < 20 ? 'Tuổi teen' : 'Tuổi không teen');
// Kết quả: Tuổi teen
```

Ví dụ 2:

```js
var input = 'f8';
var result = input === 'f8' ? 'Fullstack.edu.vn' : 'Unknown';
console.log(result);
// Kết quả: Fullstack.edu.vn
```
