# LÀM VIỆC VỚI MẢNG

Các thuộc tính:

1. To string

- Chuyển các phần tử sang chuỗi nối với nhau bởi dấu phẩy (",")
- Không làm thay đổi mảng đã cho.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'C#', 'Ruby'];

console.log(arr.toString()); //Javascript,PHP,CSS,C#,Ruby
console.log(arr.toString(';')); //Javascript,PHP,CSS,C#,Ruby
console.log(typeof arr.toString()); // string
```

2. Join

- Gần giống với toString() là nối các phần tử trong mảng thành 1 chuỗi, nhưng có hỗ trợ chia cách các phần tử bởi ký tự truyền vào.
- Không làm thay đổi mảng đã cho.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'C#', 'Ruby'];

console.log(arr.join()); // Javascript,PHP,CSS,C#,Ruby
console.log(arr.join('')); // JavascriptPHPCSSC#Ruby
console.log(arr.join(' ')); // Javascript PHP CSS C# Ruby
console.log(arr.join(',')); // Javascript,PHP,CSS,C#,Ruby
console.log(arr.join('; ')); // Javascript; PHP; CSS; C#; Ruby
```

3. Pop

- Loại bỏ phần tử cuối cùng của mảng
- Làm thay đổi mảng đã cho.
- Giá trị lấy ra là Element cuối cùng của mảng bị pop()

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.pop();

console.log(arr); // ["Javascript", "PHP", "CSS"]
console.log(arr.length); // 3 : element of Array
console.log(valueEl); // Ruby
```

4. Push

- Thêm vào phần tử ở vị trí cuối cùng của mảng
- Làm thay đổi mảng đã cho.
- Giá trị của .push() là độ dài của mảng sau khi đã .push() thêm vào.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.push('Python');

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby", "Python"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // 5: element of Array
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.push('Python', 'Dart');

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby", "Python", "Dart"]
console.log(arr.length); // 6 : element of Array
console.log(valueEl); // 6: element of Array
```

5. Shift

- Loại bỏ phần tử đầu tiên của mảng
- Làm thay đổi mảng đã cho.
- Giá trị của .shift() là giá trị đầu tiên của mảng bị loại bỏ.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.shift();

console.log(arr); // ["PHP", "CSS", "Ruby"]
console.log(arr.length); // 3 : element of Array
console.log(valueEl); // Javascript
```

6. Unshift

- Thêm phần tử vào vị trí đầu tiên của mảng
- Làm thay đổi mảng đã cho.
- Giá trị của .unshift() là độ dài của mảng sau khi thêm phần tử vào.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.unshift('Python');

console.log(arr); // ["Python", "Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // 5 : element of Array
```

7. Splicing

- Cắt mảng từ vị trí bắt đầu với số lượng bao nhiêu phần tử cần tách ra.
  > Syntax : .splice(startLocation, numberSlice)
- Nếu bỏ trống số lượng cần lấy sẽ lấy từ vị trí chỉ định tất cả phần tử còn lại của mảng.
- Làm thay đổi mảng đã cho.
- Giá trị của .splice() mảng bị tách ra.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1, 2);

console.log(arr); // ["Javascript", "Ruby"]
console.log(arr.length); // 2 : element of Array
console.log(valueEl); // ["PHP", "CSS"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1);

console.log(arr); // ["Javascript"]
console.log(arr.length); // 1 : element of Array
console.log(valueEl); // ["PHP", "CSS", "Ruby"]
```

8. Concat

- Chức năng bổ sung thêm phần tử vào mảng ở vị trí cuối cùng.
- Không làm thay đổi mảng đã cho.
- Giá trị của .concat() là một mảng mới từ mảng đã có bổ sung thêm phần tử.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.concat('Python');

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["Javascript", "PHP", "CSS", "Ruby", "Python"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.concat(['Python', 'SQL']);

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["Javascript", "PHP", "CSS", "Ruby", "Python", "SQL"]
```

9. Slicing

---

Có thể tìm hiểu thêm các Method khác của Array [ở đây](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#)

---

## Chi tiết

### 7. Splicing

- `Splice` : Chức năng **xóa** và **chèn**.

Xem các mục xử lý sau:

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1, 2);

console.log(arr); // ["Javascript", "Ruby"]
console.log(arr.length); // 2 : element of Array
console.log(valueEl); // ["PHP", "CSS"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1, 2, 'Java');

console.log(arr); // ["Javascript", "Java", "Ruby"]
console.log(arr.length); // 3 : element of Array
console.log(valueEl); // ["PHP", "CSS"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1);

console.log(arr); // ["Javascript"]
console.log(arr.length); // 1 : element of Array
console.log(valueEl); // ["PHP", "CSS", "Ruby"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1, 0, 'Java');

console.log(arr); // ["Javascript", "Java", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // []
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(-1, 2, 'Java');

console.log(arr); // ["Javascript", "PHP", "CSS", "Java"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["Ruby"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(-1, -2, 'Java');

console.log(arr); // ["Javascript", "PHP", "CSS", "Java", "Ruby"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // []
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(-1, -1, 'Java');

console.log(arr); // ["Javascript", "PHP", "CSS", "Java", "Ruby"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // []
```

#### 7.1 Xóa

> Syntax: .splice(start)

- `start`: Vị trí con trỏ cần chỉ định đến
- Xóa mảng từ vị trí `start` đến hết mảng

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1);

console.log(arr); // ["Javascript"]
console.log(arr.length); // 1
console.log(valueEl); // ["PHP", "CSS", "Ruby"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
// Xóa từ vị trí CSS về sau
var valueEl = arr.splice(-2);

console.log(arr); // ["Javascript", "PHP"]
console.log(arr.length); // 2
console.log(valueEl); // ["CSS", "Ruby"]
```

> Syntax: .splice(start, numberDelete)

- `start`: Vị trí con trỏ cần chỉ định đến
- `numberDelete` : Số lượng phần tử cần xóa bắt đầu từ vị trí con trỏ đó.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1, 2);

console.log(arr); // ["Javascript", "Ruby"]
console.log(arr.length); // 2
console.log(valueEl); // ["PHP", "CSS"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(1, 0); // Sẽ không xóa do <= 0
valueEl = arr.splice(1, -1); // Sẽ không xóa do <= 0

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4
console.log(valueEl); // []
```

- Nếu `start`< 0 thì sẽ đếm vị trí từ phía sau

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(-2, 1);

console.log(arr); // ["Javascript", "PHP", "Ruby"]
console.log(arr.length); // 3 : element of Array
console.log(valueEl); // ["CSS"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
// Đếm ngược từ sau đến vị trí index -2 là CSS và xóa 2 phần tử
var valueEl = arr.splice(-2, 2);

console.log(arr); //  ["Javascript", "PHP"]
console.log(arr.length); // 2 : element of Array
console.log(valueEl); // ["CSS", "Ruby"]
```

#### 7.2 Chèn

> Syntax: .splice(start, numberDelete, elementInsert)

- Khi `numberDelete` bằng 0, sẽ không xóa phần tử; mà sẽ tiến hành chèn vào vị trí `start`

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(2, 0);

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // []
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(2, 0, 'Java');

console.log(arr); // ["Javascript", "PHP", "Java", "CSS", "Ruby"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // []
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(-1, 0, 'Java');

console.log(arr); // ["Javascript", "PHP", "CSS", "Java", "Ruby"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // []
```

#### 7.3 Xóa và chèn.

> Syntax: .splice(start, numberDelete, elementInsert)

- Kết hợp 2 mục trên khi `numberDelete` > 0 và thêm `elementInsert` tại vị trí `start`.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];

var valueEl = arr.splice(1, 2, 'Java'); // Con trỏ ở vị trí PHP, xóa 2 phần từ và chèn 'Java' ở đây

console.log(arr); // ["Javascript", "Java", "Ruby"]
console.log(arr.length); // 3 : element of Array
console.log(valueEl); // ["PHP", "CSS"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(-1, 2, 'Java');
// Con trỏ đến vị trí index = -1 là 'Ruby', sau đó xóa 2 phần tử từ Ruby đếm ra sau, rồi chèn vào 'Java' tại vị trí này.

console.log(arr); // ["Javascript", "PHP", "CSS", "Java"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["Ruby"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.splice(-1, -2, 'Java');
// Con trỏ đến vị trí index = -1 là 'Ruby', vì -2 <= 0 nên không xóa, và chèn vào vị trí này 'Java'

console.log(arr); // ["Javascript", "PHP", "CSS", "Java", "Ruby"]
console.log(arr.length); // 5 : element of Array
console.log(valueEl); // []
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];

var valueEl = arr.splice(1, 'Java');
// Con trỏ ở vị trí PHP, không có số lượng phần tử cần xóa, nên không chèn vào

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // []
```

---

### 8. Concat

> Syntax: A.concat(B)

- Nối 2 Array với nhau, trả về mảng mới với mảng thêm vào ở phía sau, không làm thay đổi mảng cũ.

- Chức năng bổ sung thêm phần tử vào mảng ở vị trí cuối cùng.
- Không làm thay đổi mảng đã cho.
- Giá trị của .concat() là một mảng mới từ mảng đã có bổ sung thêm phần tử.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.concat('Python');

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["Javascript", "PHP", "CSS", "Ruby", "Python"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];
var valueEl = arr.concat(['Python', 'SQL']);

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["Javascript", "PHP", "CSS", "Ruby", "Python", "SQL"]
```

---

### 9. Slicing

### 9.1 : Cắt mảng

- slice : cắt lấy 1 vài phần tử của mảng đã có.

> Syntax: .slice(startLoc, endLoc)

- Từ vị trí index đầu đến vị trí index cần dừng
- Không làm thay đổi mảng đã có, trả về mảng mới.

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];

var valueEl = arr.slice(1, 2);
// lấy mảng các phần tử từ con trỏ ở vị trí PHP, đến index thứ 2 CSS

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["PHP"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];

var valueEl = arr.slice(1, 3);
// lấy mảng các phần tử từ con trỏ ở vị trí PHP, đến index thứ 3 Ruby

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["PHP", "CSS"]
```

### 9.1 : Copy mảng

- Copy mảng

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];

var valueEl = arr.slice(1);
// lấy mảng các phần tử từ con trỏ ở vị trí PHP, đến cuối

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["PHP", "CSS", "Ruby"]
```

```js
var arr = ['Javascript', 'PHP', 'CSS', 'Ruby'];

var valueEl = arr.slice(0);
// Copy cả mảng

console.log(arr); // ["Javascript", "PHP", "CSS", "Ruby"]
console.log(arr.length); // 4 : element of Array
console.log(valueEl); // ["Javascript", "PHP", "CSS", "Ruby"]
```

---

## Bài tập

---

```js
// Làm bài tập tại đây
function sum2(a, b) {
  var result = a + b;
  console.log(typeof result);
  if (typeof result != 'number') {
    result = false;
  }
  return result;
}

function sum(a, b) {
  if (!isNaN(a + b)) return a + b;
  return false;
}

var c = null;
var d = undefined;
console.log(sum2(c, d));
```
