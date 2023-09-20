# Math Object

---

`Math` không phải là `Object Constructor` nên không thể khởi tạo cho đổi tượng.

```js
var number = new Math(); // Math is not a constructor
```

Những thuộc tính của `Math` thường được dùng bao gồm:

- Math.PI : Lấy số PI
- Math.round() : Làm tròn
- Math.abs() : Lấy trị tuyệt đối
- Math.ceil() : Lấy giá trị làm tròn trên
- Math.floor() : Lấy giá trị làm tròn trên
- Math.random() : Tạo 1 số ngẫu nhiên từ 0 -> 1
- Math.max() : Lấy giá trị lớn nhất
- Math.min() : Lấy giá trị nhỏ nhất
- ... Xem thêm [Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)

---

### 1. Math.PI

```js
var number = Math.PI;
console.log(number); // 3.141592653589793
```

---

### 2. Math.round()

```js
console.log(Math.round(9.75)); // 10
console.log(Math.round(6.25)); // 6
console.log(Math.round(4.55)); // 5
console.log(Math.round(5.49)); // 5
```

---

### 3. Math.abs()

```js
console.log(Math.abs(-9)); // 9
console.log(Math.abs(-6.1001)); // 6.1001
console.log(Math.abs(4)); // 4
console.log(Math.abs(-5.21)); // 5.21
```

---

### 4. Math.ceil()

```js
console.log(Math.ceil(9.1)); // 10
console.log(Math.ceil(6.901)); // 7
console.log(Math.ceil(4.001)); // 5
console.log(Math.ceil(5.21)); // 6
```

---

### 5. Math.floor()

```js
console.log(Math.floor(9.1)); // 9
console.log(Math.floor(6.901)); // 6
console.log(Math.floor(4.001)); // 4
console.log(Math.floor(5.21)); // 5
```

---

### 6. Math.random()

```js
console.log(Math.random()); // 0.05194999912333054
console.log(Math.random()); // 0.8058867537718295
console.log(Math.random()); // 0.2673795031042312
```

- Áp dụng:
  - Thảy đồng tiền ngửa - xắp, 0-1, Đúng-Sai,...
  - Đổ xúc sắc 1-> 6 nút
  - Ngẫu nhiên 1 số từ 1 -> n cho trước.

```js
// Thảy đồng tiền ngửa - xắp, 0-1, Đúng - Sai,...
var number = Math.round(Math.random());
console.log(number);

// Đổ xúc sắc 1-> 6 nút
for (var i = 0; i <= 1000; i++) {
  console.log(Math.round(Math.random() * 5 + 1));
}
// Ngẫu nhiên 1 số từ 1 -> 100 cho trước.
console.log(Math.round(Math.random() * 99 + 1));
```

---

### 7. Math.min() & Math.max()

```js
console.log(Math.min(92, -4, 3, 78, -21, 39)); // -21
console.log(Math.max(92, -4, 3, 78, -21, 39)); // 92
```

---
