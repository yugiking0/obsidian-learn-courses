# TOÁN TỬ SỐ HỌC

## Lý thuyết

Javascript cung cấp tập hợp các toán tử phong phú giúp chúng ta thao tác với các giá trị và biến. Gồm các nhóm sau:

1. Toán tử số học (Arithmetic)
2. Toán tử gán (Assignment)
3. Toán tử so sánh (Comparison)
4. Toán tử logic (Logical)

Các toán tử số học được sử dụng trong các biểu thức toán học giống như cách chúng được sử dụng trong đại số.

Toán tử số học được sử dụng để thực hiện các phép toán số học trên các toán hạng. Các toán tử sau được gọi là toán tử số học trong JavaScript.

| Toán tử | Chức năng        | Ví dụ                 |
| ------- | ---------------- | --------------------- |
| +       | Phép cộng        | 2 + 2 = 4             |
| -       | Phép trừ         | 10 - 4 = 6            |
| \_      | Phép nhân        | 5 \* 2 = 10           |
| /       | Phép chia        | 8 / 2 = 4             |
| \*\*    | Phép lũy         | thừa 3 \*\* 2 = 9     |
| %       | Phép chia lấy dư | 10 % 3 = 1            |
| ++      | Tăng lên 1       | var a = 2; a++; a = 3 |
| –       | Giảm xuống 1     | var a = 2; a–; a = 1  |

## Ví dụ

```js
var a = 2;
var b = 6;
var c = a * b;
console.log(c); // output: 12

var d = 3;
c = a * b + d;
console.log(c); // output: 15

c = (a * b) % 5;
console.log(c); // output: 2
```
