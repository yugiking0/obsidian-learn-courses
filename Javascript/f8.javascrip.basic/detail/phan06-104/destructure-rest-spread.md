# Destructuring, Rest & Spread 

---
## 1. Destructuring javascript là gì?

`Destructuring` là một cú pháp cho phép bạn gán các thuộc tính của một `Object` hoặc một `Array`. Điều này có thể làm giảm đáng kể các dòng mã cần thiết để thao tác dữ liệu trong các cấu trúc này. Có hai loại `Destructuring`: `Destructuring Objects` và `Destructuring Arrays `

### 1.1 Destructuring Objects 

**`Destructuring Objects`** cho phép bạn tạo ra một hay nhiều *new variables*  sử dụng những property của một `Objects`. Xem ví dụ dưới đây:

```js
const note = {
  	id: 1,
  	website: 'anonyStick.com',
  	date: '17/07/2014',
}
```

https://anonystick.com/blog-developer/giai-thich-ve-destructuring-rest-parameters-va-spread-syntax-trong-javascript-2020051980035339