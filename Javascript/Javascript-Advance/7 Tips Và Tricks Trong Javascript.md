# 7 Tips Và Tricks Trong Javascript Giúp Bạn Chuyên Nghiệp Hơn

**Những mẹo dưới đây có thể giúp bạn tối ưu code Javascript của mình, giúp cho những dòng code của bạn trở nên chuyên nghiệp hơn, gọn gàng hơn**

### 1. Lọc ra những giá trị xuất hiện một lần trong mảng.

Kiểu đối tượng `Set` trong Javascript và toán tử `spread` ra mắt ở phiên bản ES6. Chúng ta có thể kết hợp 2 điều này để tạo ra một mảng mới từ mảng đã cho và các phần tử trong mảng chỉ xuất hiện một lần.

```javascript
const array = [1, 1, 2, 5, 3, 4, 4, 5]
const uniqueArray = [...new Set(array)]

console.log(uniqueArray)
// Results: [1, 2, 5, 3, 4]
```

### 2. Every and some.

`Every` function trả về giá trị boolean. Nếu tất cả phần tử trong mảng thỏa mãn điều kiện thì sẽ trả về **`true`**. Bên cạnh đó, `some` function chỉ kiểm trả nếu tồn tại ít nhất một phần tử trong mảng thỏa điều kiện thì trả về **true**.

```javascript
const firstArray = [12, 2, 3, 5, 6]
const secondArray = [20, -5, 3, 1, 6]

const isPositive = (number) => {
  return number > 0;
}

console.log(firstArray.every(isPositive));
// true (vì tất cả phần tử trong mảng này đều thỏa điều kiện)
console.log(secondArray.every(isPositive));
// false (vì có một phần tử -5 không thỏa điều kiện)

console.log(firstArray.some(isPositive));
// true
console.log(secondArray.some(isPositive))
// true (tồn tại phần tử thỏa điều kiện)
```

### 3. Chuyển từ số sang kiểu Boolean.

Khai báo một biến có giá trị **boolean**, ngoài cách khai báo thông thường (cho giá trị của biến là **true** hoặc **false**) thì có thể làm theo cách dưới đây.

```javascript
const isTrue = !0;
const isFalse = !1;
const alsoFalse = !!0;

console.log(isTrue);
// true
console.log(isFalse);
// false
console.log(alsoFalse);
// false
```

### 4. Chuyển sang kiểu String.

Với những ngôn ngữ, ta có thể chuyển số sang string bằng hàm `toString()`. Javascript cũng vậy, tuy nhiên còn có cách khác nhanh gọn hơn để làm điều đó như ví dụ dưới đây.

```javascript
const value = 1 + "";

console.log(value);
// "1"
```

### 5. Chuyển sang kiểu Number.

Việc chuyển từ String sang Number có thể sử dụng `parseInt()` trong Javascript. Nhưng có cách khác ngắn hơn để làm điều này đó chính ra sử dụng toán tử +.

```javascript
var value = "15"
value = +value;

console.log(value);
// 15
console.log(typeof value);
// "number"
```

### 6. Chuyển từ số thập phân sang số nguyên.

Nếu muốn chuyển từ một số thập phân sang số nguyên, bạn có thể sử dụng các function của Object Math như `Math.floor()`, `Math.ceil()` hoặc `Math.round()`. Nhưng cách nhanh nhất để làm điều này là sử dụng toán tử bitwise OR ( | ).

```javascript
console.log(5.9 | 0); // 5
console.log(5.1 | 0); // 5
```

### 7. Format code JSON.

Kiểu JSON nếu hiển thị trên một đường thẳng sẽ rất khó đọc, để dễ dàng đọc kiểu JSON hơn thì chúng ta có thể sử dụng method `stringify()` như ví dụ dưới đây.

```javascript
let obj = {name: 'Code learn', age: '3'}

console.log(obj)
console.log(JSON.stringify(obj, null, '\t'))
```

Kết quả:

![[Pasted image 20230906112055.png]]


Giữa dòng đầu và dòng thứ hai thì tất nhiên dòng đầu sẽ dễ đọc hơn đúng không nào ?

### Tạm kết.

Trên đây là 7 mẹo và thủ thuật khi code Javascript khiến cho đoạn code của bạn sẽ **dễ đọc hơn** và **không cần** dùng những function, method dài dòng. Hy vọng chia sẻ của mình sẽ có ích cho những bạn đang học Javascript. Nếu có thắc mắc hay đóng góp các bạn có thể bình luận bên dưới. Cảm ơn các bạn rất nhiều, chúc các bạn học tốt.