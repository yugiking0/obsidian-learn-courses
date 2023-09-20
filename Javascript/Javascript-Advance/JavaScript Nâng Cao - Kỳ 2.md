# JavaScript Nâng Cao - Kỳ 2

#### Có một câu nói là: **Trên đời chỉ có thứ nhiều người chửi và thứ không ai thèm dùng.**

Javascript là một ví dụ điển hình, nó có một số điểm thú vị nhưng cũng khiến chúng ta phải đau đầu. Lý thuyết thì dễ hiểu, nhưng khi thực hành là cả một vấn đề. Vậy nên, mình sẽ cùng các bạn đi sâu vào từng ví dụ cụ thể và phân tích, mổ xẻ nó để hiểu hơn về Javascript nhé.

**Series** này có thể sẽ khá dài mình không biết sẽ có bao nhiêu **Kỳ** tuy nhiên để tiện cho các bạn nào không đọc các bài trước đó của mình về JS thì trong loạt bài này mình sẽ giải thích lại toàn bộ. Các lý thuyết trong loạt bài này mình cũng có thể sẽ giải thích lại nhiều lần (tùy hứng) để các bạn có thể năm rõ nó hơn nhé. Ok vào bài thôi nào... GÉT GÔ 🚀

> Nếu có bất kỳ câu hỏi nào đừng ngại hãy bình luận dưới phần `comment` nhé. Hoặc chỉ cần để lại một `comment chào mình` là đã giúp mình có thêm động lực hoàn thành series này. Cảm ơn các bạn rất nhiều. 🤗

## **6. Khái niệm tham chiếu và tham trị**

Output của đoạn code bên dưới là gì:

```js
let c = { greeting: "Hey!" };
let d;

d = c;
c.greeting = "Hello";
console.log(d.greeting);
```

- A: `Hello`
- B: `Hey`
- C: `undefined`
- D: `ReferenceError`
- E: `TypeError`

```md
Đáp án của câu hỏi này là
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
Đáp án: A
```

Cùng mình đi tìm hiểu tại sao kết quả lại là như vậy nhé ❓️

### 6.1. Tham trị (pass-by-value)

Trong JavaScript, khi bạn gán một giá trị nguyên thủy (primitive value) như số, chuỗi, boolean, null, undefined, Symbol) từ một biến này sang một biến khác, giá trị thực sự được sao chép từ biến này sang biến kia.

Ví dụ:

```js
let a = 10;
let b = a;
a = 20;

console.log(a); // 20
console.log(b); // 10
```

Trong ví dụ trên, giá trị của `a` được sao chép vào `b`, nên khi thay đổi giá trị của `a`, giá trị của `b` không bị ảnh hưởng.

### 6.2 Tham chiếu (pass-by-reference)

Tuy nhiên, khi làm việc với các đối tượng (object, array, function), giá trị được tham chiếu, chứ không phải được sao chép.

Ví dụ:

```js
let obj1 = { value: 10 };
let obj2 = obj1;
obj1.value = 20;

console.log(obj1.value); // 20
console.log(obj2.value); // 20
```

Như bạn có thể thấy trong ví dụ trên, `obj2` không chỉ nhận giá trị ban đầu của `obj1`, mà còn tham chiếu tới cùng một đối tượng. Do đó, khi chúng ta thay đổi giá trị của `obj1`, giá trị của `obj2` cũng thay đổi theo.

### 6.3. Quay lại với câu hỏi ban đầu

```js
let c = { greeting: "Hey!" };
let d;

d = c;
c.greeting = "Hello";
console.log(d.greeting);
```

Tại thời điểm này, `c` là một đối tượng có một thuộc tính `greeting` có giá trị là "Hey!". Khi ta gán `d = c`, thì `d` tham chiếu tới cùng một đối tượng mà `c` tham chiếu. Do đó, khi thay đổi giá trị của `c.greeting` thành "Hello", giá trị của `d.greeting` cũng thay đổi theo, và `console.log(d.greeting)` in ra "Hello".

Hy vọng rằng, với ví dụ và giải thích của mình, các bạn đã hiểu rõ hơn về cách tham chiếu và tham trị hoạt động trong JavaScript, và tại sao đoạn code trên lại cho ra kết quả như vậy.

## **7. Khác Biệt Giữa "==" và "==="**

Output của đoạn code bên dưới là gì?

```js
let a = 3;
let b = new Number(3);
let c = 3;

console.log(a == b);
console.log(a === b);
console.log(b === c);
```

- A: `true` `false` `true`
- B: `false` `false` `true`
- C: `true` `false` `false`
- D: `false` `true` `true`

```md
Đáp án của câu hỏi này là
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
Đáp án: C
```

Chắc các bạn cũng thắc mắc tại sao kết quả lại ra như vậy, phải không nào? Để giải thích điều này, mình cần hiểu rõ về toán tử `==` và `===` trong Javascript.

### 7.1. Toán tử `==` (So sánh bằng)

Toán tử `==` so sánh hai giá trị với nhau và trả về `true` nếu chúng bằng nhau sau khi ép kiểu (type coercion) hoặc `false` nếu không.

Ví dụ:

```js
console.log(3 == '3'); // true
```

Trường hợp `a == b` trong ví dụ ban đầu, giá trị của `a` là 3 và giá trị của `b` là một đối tượng `Number` với giá trị là 3. Khi sử dụng toán tử `==`, Javascript sẽ tự động chuyển đổi kiểu của `b` thành `number`, nên kết quả của `a == b` sẽ là `true`.

### 7.2. Toán tử `===` (So sánh tuyệt đối)

Toán tử `===` so sánh cả giá trị và kiểu dữ liệu của hai biến. Nếu cả hai đều giống nhau, nó sẽ trả về `true`, ngược lại sẽ trả về `false`.

Ví dụ:

```js
console.log(3 === '3'); // false
```

Trường hợp `a === b` trong ví dụ ban đầu, mặc dù giá trị của `a` và `b` đều là 3, nhưng `a` là kiểu `number` và `b` là kiểu `object`, nên kết quả của `a === b` sẽ là `false`.

Tương tự, `b === c` cũng trả về `false` vì `b` là kiểu `object` và `c` là kiểu `number`.

Tóm lại, khi sử dụng toán tử `==`, Javascript sẽ tự động chuyển đổi kiểu dữ liệu của các biến để so sánh, trong khi `===` sẽ so sánh cả giá trị và kiểu dữ liệu mà không ép kiểu. Do đó, mình nên sử dụng `===` để tránh các lỗi không mong muốn do ép kiểu tự động. Vậy nên thường thì sẽ luôn sử dụng `===` nếu như không có mục đích hoặc lý do đặc biệt nào khác bắt buộc phải dùng `==`.

## **8. TypeError khi gọi phương thức static**

Output khi run đoạn code bên dưới là gì:

```js
class Chameleon {
  static colorChange(newColor) {
    this.newColor = newColor;
    return this.newColor;
  }

  constructor({ newColor = "green" } = {}) {
    this.newColor = newColor;
  }
}

const freddie = new Chameleon({ newColor: "purple" });
freddie.colorChange("orange");
```

- A: `orange`
- B: `purple`
- C: `green`
- D: `TypeError`

```md
Đáp án của câu hỏi này là
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
Đáp án: D 
```

Hàm `colorChange` là một hàm static (hàm tĩnh). Hàm static được thiết kế để chỉ để tồn tại ở mức class, và không thể truyền cho bất cứ instance con nào. Vì `freddie` là một instance con, hàm static này sẽ không được truyền xuống, và do đó không thể gọi được tại `freddie` instance: nó sẽ throw ra một `TypeError: freddie.colorChange is not a function`.

Nếu bạn thực thi đoạn code trên sẽ gặp lỗi `TypeError`

Để hiểu rõ hơn về vấn đề này, chúng ta cần tìm hiểu về các khái niệm sau:

### 8.1 Phương thức `static` trong JavaScript

Trong JavaScript, phương thức `static` là những phương thức được đính kèm với lớp, chứ không phải với một thể hiện (instance) của lớp đó. Nghĩa là, bạn không thể gọi một phương thức `static` từ một thể hiện của lớp.

### 8.2 `this` trong phương thức `static`

Khi sử dụng `this` trong một phương thức `static`, `this` đại diện cho lớp đó, chứ không phải một thể hiện của lớp. Điều này có nghĩa là bạn không thể truy cập vào các thuộc tính hoặc phương thức không `static` từ một phương thức `static`.

### 8.3. Giải thích kết quả của đoạn code ban đầu

Bây giờ chúng ta đã hiểu rõ hơn về phương thức `static` và `this` trong phương thức `static`, hãy phân tích đoạn mã được cung cấp.

Chúng ta có một lớp tên là `Chameleon` với một phương thức `static` tên là `colorChange` và một constructor. Constructor này khởi tạo `newColor` với giá trị mặc định là "green" nếu không có giá trị nào được cung cấp.

Sau đó, chúng ta tạo một thể hiện mới của `Chameleon` với giá trị `newColor` là "purple" và gán nó vào biến `freddie`.

Cuối cùng, chúng ta cố gắng gọi phương thức `colorChange` từ thể hiện `freddie` và thay đổi màu sắc thành "orange".

Tuy nhiên, do `colorChange` là một phương thức `static`, nó không thể được gọi từ một thể hiện của lớp. Vì vậy, khi chúng ta cố gắng gọi `freddie.colorChange("orange")`, JavaScript sẽ sinh ra lỗi `TypeError`.

### 8.4. Tóm lại

Như vậy, chúng ta đã hiểu rằng, không thể gọi một phương thức `static` từ một thể hiện của lớp. Điều này giúp ngăn chặn việc gọi nhầm các phương thức không cần thiết từ các thể hiện, giúp giữ cho mã của chúng ta gọn gàng và dễ quản lý hơn.

Nhớ rằng, nếu bạn muốn sử dụng một phương thức trong cả lớp và các thể hiện của lớp đó, đừng đặt nó là `static`.

## **9. Lỗi đánh máy và "use strict"**

### 9.1. Câu hỏi

Output của đoạn code bên dưới là gì?

```js
let greeting;
greetign = {}; // Lỗi đánh máy!
console.log(greetign);
```

- A: `{}`
- B: `ReferenceError: greetign is not defined`
- C: `undefined`

```md
Đáp án của câu hỏi này là
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
Đáp án: A 
```

Cùng mình đi tìm hiểu tại sao kết quả lại là như vậy nhé ❓️

### 9.2. Tìm hiểu lỗi

Trong JavaScript, khi ta thực hiện một phép gán cho một biến chưa được khai báo, thì JavaScript sẽ tự động tạo ra một biến toàn cục (global variable). Vì vậy, `greetign = {}` sẽ tạo ra một biến toàn cục `greetign` và gán cho nó giá trị `{}`.

Vậy, khi chạy `console.log(greetign)`, nó sẽ log ra `{}`.

Điều này có thể dẫn đến các vấn đề không mong muốn, bởi vì ta vô tình tạo ra một biến toàn cục mà không hề hay biết.

### 9.3. Sử dụng "use strict"

Để tránh việc tạo ra các biến toàn cục không mong muốn như thế này, chúng ta có thể sử dụng chế độ nghiêm ngặt (strict mode) trong JavaScript bằng cách thêm dòng `"use strict"` ở đầu tệp mã nguồn hoặc đầu khối mã.

Ví dụ, hãy xem xét đoạn mã sau:

```js
"use strict";
let greeting;
greetign = {}; // Lỗi đánh máy!
console.log(greetign);
```

Khi chạy đoạn mã này, JavaScript sẽ báo lỗi `ReferenceError: greetign is not defined`, vì chế độ nghiêm ngặt không cho phép gán giá trị cho các biến chưa được khai báo.

### 9.4. Tóm lại

Lỗi đánh máy thường gặp và có thể tạo ra các vấn đề không mong muốn trong mã nguồn của chúng ta. Để tránh điều này, hãy sử dụng chế độ nghiêm ngặt `"use strict"` để đảm bảo rằng chúng ta không gán giá trị cho các biến chưa được khai báo.

## **10. Thêm thuộc tính cho function**

Điều gì sẽ xảy ra khi chúng ta làm thế này?

```js
function bark() {
  console.log("Woof!");
}

bark.animal = "dog";
```

- A: Hoàn toàn không có vấn đề gì!
- B: `SyntaxError`. Bạn không thể thêm thuộc tính theo cách này.
- C: `undefined`
- D: `ReferenceError`

```md
Đáp án của câu hỏi này là
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
↓↓↓↓↓↓↓↓↓↓
Đáp án: A 
```

Trước tiên, mình cần hiểu rõ một điều quan trọng: trong JavaScript, hầu như mọi thứ đều là đối tượng (object), kể cả hàm (function). Điều này có nghĩa là chúng ta có thể thêm, chỉnh sửa hoặc xóa các thuộc tính và phương thức của đối tượng, kể cả khi đó là một hàm.

### 10.1 Kiểu dữ liệu trong JavaScript

Có 7 kiểu dữ liệu nguyên thủy trong JavaScript, bao gồm: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, và `bigint`. Trừ các kiểu nguyên thủy này, mọi thứ khác đều được coi là đối tượng (`object`). Điều này bao gồm mảng (`Array`), hàm (`Function`), và đương nhiên, đối tượng (`Object`).

### 10.2 Function là object

Khi mình nói rằng "function là object", điều đó có nghĩa là chúng ta có thể tương tác với hàm giống như với các đối tượng khác, ví dụ thêm các thuộc tính và phương thức vào chúng. Đoạn mã ở trên chính là một ví dụ. Chúng ta đã thêm thuộc tính `animal` cho hàm `bark` và gán giá trị `"dog"` cho nó.

### 10.3. Ví dụ minh họa

Ví dụ mình đã thấy ở trên là một ví dụ cơ bản. Giờ hãy thử một ví dụ khác một chút để hiểu rõ hơn:

```js
function greet() {
  console.log("Hello!");
}

// Thêm thuộc tính
greet.language = "English";

// Thêm phương thức
greet.sayGoodbye = function() {
  console.log("Goodbye!");
};

console.log(greet.language); // Output: English
greet.sayGoodbye(); // Output: Goodbye!
```

Ở ví dụ này, mình đã thêm một thuộc tính `language` và một phương thức `sayGoodbye` cho hàm `greet`. Điều này hoàn toàn hợp lệ và thực thi bình thường.

### 10.4. Tóm lại

Trong JavaScript, chúng ta có thể thêm thuộc tính và phương thức cho hàm vì hàm cũng là đối tượng. Chúng ta không chỉ có thể thêm thuộc tính và phương thức, mà còn có thể tham chiếu và sao chép chúng giống như các đối tượng khác. Điều này làm cho JavaScript trở thành một ngôn ngữ linh hoạt và mạnh mẽ, nhưng cũng yêu cầu chúng ta phải hết sức cẩn thận để tránh gây ra lỗi không mong muốn.