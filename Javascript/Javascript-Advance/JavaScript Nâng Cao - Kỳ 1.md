# JavaScript Nâng Cao - Kỳ 1

#### Có một câu nói là: **Trên đời chỉ có thứ nhiều người chửi và thứ không ai thèm dùng.**

Javascript là một ví dụ điển hình, nó có một số điểm thú vị nhưng cũng khiến chúng ta phải đau đầu. Lý thuyết thì dễ hiểu, nhưng khi thực hành là cả một vấn đề. Vậy nên, mình sẽ cùng các bạn đi sâu vào từng ví dụ cụ thể và phân tích, mổ xẻ nó để hiểu hơn về Javascript nhé.

**Series** này có thể sẽ khá dài mình không biết sẽ có bao nhiêu **Kỳ** tuy nhiên để tiện cho các bạn nào không đọc các bài trước đó của mình về JS thì trong loạt bài này mình sẽ giải thích lại toàn bộ. Các lý thuyết trong loạt bài này mình cũng có thể sẽ giải thích lại nhiều lần (tùy hứng) để các bạn có thể năm rõ nó hơn nhé. Ok vào bài thôi nào... GÉT GÔ 🚀

> Nếu có bất kỳ câu hỏi nào đừng ngại hãy bình luận dưới phần `comment` nhé. Hoặc chỉ cần để lại một `comment chào mình` là đã giúp mình có thêm động lực hoàn thành series này. Cảm ơn các bạn rất nhiều. 🤗

## **1. Hoisting**

Với đoạn code này:

```js
function sayHi() {
  console.log(name);
  console.log(age);
  var name = "Lydia";
  let age = 21;
}
sayHi();
```

Kết quả xuất ra màn hình sẽ là: `undefined` và `ReferenceError`

Cùng mình đi tìm hiểu tại sao kết quả nó lại là như vậy nhé ❔

### 1.1. Biến trong JavaScript và việc "hoisted"

Khi bạn nhìn thấy đoạn mã trên, bạn có thể tự hỏi: "Tại sao lại xuất hiện `undefined` và `ReferenceError` trong khi ta đã khai báo biến `name` và `age` sau những dòng console.log?". Để giải đáp câu hỏi này, mình cần phải hiểu về một khái niệm quan trọng trong JavaScript: **hoisting**.

### 1.2. Hoisted là gì?

Trong JavaScript, khi chúng ta khai báo một biến bằng `var`, trình biên dịch sẽ tự động "di chuyển" phần khai báo biến đó lên đầu hàm hoặc lên đầu phạm vi toàn cục. Người ta gọi quá trình này là **hoisting**.

Ví dụ, khi ta có:

```js
function saySomething() {
  console.log(message);
  var message = "Hello, mình là Tuấn!";
}
```

Thực chất, trình biên dịch sẽ "thấy" mã như sau:

```js
function saySomething() {
  var message;
  console.log(message);
  message = "Hello, mình là Tuấn!";
}
```

### 1.3. Biến `name` và giá trị `undefined`

Quay trở lại với đoạn mã ban đầu, dù chúng ta khai báo biến `name` sau dòng `console.log(name)`, nhưng do **hoisting**, biến `name` đã được "chuyển lên đầu" và chỉ được khởi tạo chứ chưa được gán giá trị. Vì vậy, khi chúng ta truy xuất đến biến `name` tại thời điểm đó, giá trị của nó là `undefined`.

### 1.4. Biến `age`, `let` và "temporal dead zone"

Với biến `age`, ta sử dụng từ khóa `let` để khai báo. Mặc dù `let` và `const` cũng trải qua quá trình **hoisting** giống như `var`, nhưng chúng không được khởi tạo ngay lập tức. Thay vào đó, có một khoảng thời gian mà chúng không thể truy cập - và người ta gọi đó là **"temporal dead zone"**. Nếu chúng ta cố gắng truy cập đến một biến `let` hoặc `const` trong "dead zone" này, JavaScript sẽ báo lỗi `ReferenceError`.

Trong ví dụ trên, khi ta cố gắng log giá trị của `age` trước khi biến đó được khởi tạo, chúng ta chạm vào "temporal dead zone" và do đó, ta nhận được `ReferenceError`.

### 1.5. Mục đích của TDZ (Temporal Dead Zone)

Vậy tại sao lại cần tới TDZ?

Lý do chính đằng sau việc sử dụng TDZ là để giúp các lập trình viên tránh được các lỗi khó nhận biết và tạo ra một ngữ cảnh rõ ràng hơn khi sử dụng biến.

Ví dụ, xem xét đoạn mã sau:

```js
function updateUserProfile(id) {
    if (id) {
        let profile = getProfileById(id);
    }
    console.log(profile); // Throws ReferenceError: getProfileById is not defined
}
updateUserProfile(1)
```

như đã giải thích ở trước sau thì thực chất, trình biên dịch sẽ "thấy" mã như sau:

```js
function updateUserProfile(id) {
    let profile;
    if (id) {
        profile = getProfileById(id);
    }
    console.log(profile); // Throws ReferenceError: getProfileById is not defined
}
updateUserProfile(1)
```

Ở đây, TDZ giúp ta nhận biết rằng chúng ta đang cố gắng sử dụng một biến trước khi nó được khởi tạo. Điều này giúp tránh các lỗi tiềm ẩn, chẳng hạn như truy cập vào một thuộc tính của một đối tượng chưa được khởi tạo.

Temporal Dead Zone nghe có vẻ phức tạp, nhưng nó thực sự là một tính năng hữu ích để giúp các lập trình viên viết code một cách rõ ràng và tránh lỗi. Mặc dù việc không thể truy cập một biến trong TDZ có thể gây ra một số khó khăn khi lập trình, nhưng nó giúp chúng ta tránh được những lỗi khó nhận biết và tăng cường sự rõ ràng trong mã nguồn.

Có bạn sẽ nói: "Vớ vẩn làm gì có chuyện tôi chưa khai báo biến mà đã dùng cái này sv năm 1 cũng biết."

🤣Tấm chiếu mới, tin mình đi nếu bạn mà một Javascripter thật sự thì bạn sẽ gặp cái lỗi ReferenceError này nhiều lắm lắm luôn ấy...

### 1.6. Ví dụ minh họa

Để giải thích một cách dễ hiểu hơn, hãy tưởng tượng mình đang ở một tiệc BBQ. Khi mình đến, mình đã biết danh sách những người sẽ tham gia (danh sách biến được khai báo). Mặc dù bạn biết tên họ nhưng cho tới khi họ thực sự đến (biến được gán giá trị), bạn chẳng biết họ đang ở đâu (biến `var` sẽ là `undefined`). Và một số người khác, bạn chỉ biết họ sẽ đến sau một khoảng thời gian nhất định (biến `let` trong "temporal dead zone").

Việc trả về `undefined` có chút khác biệt so với cho nó vào "temporal dead zone", như ví dụ ở trên khi bạn đăng ký tham gia BBQ với `var` thì nếu bạn chưa tới kịp thì danh sách sẽ ghi là `undefined`. Và khi được ghi là `undefined` nó giống như bạn nhờ 1 thằng bạn có tên là `undefined` tới xí chỗ vậy đó nó sẽ tới đó trước và ngồi giữ chỗ cho bạn cho tới khi bạn tới. Còn mấy ông mua vé hạng `let` hoặc `const` thì được cho vào danh sách "temporal dead zone" có nghĩa là chưa có mặt và nếu như BBQ có tổ chức _**event Giftaway**_ quà trong lúc bạn chưa tới thì bạn sẽ MÓM 🤣.

## **2. Event Loop và Event Queue**

Trước khi đi sâu vào các ví dụ, thì mình muốn nói một chút về Event Loop và Event Queue.

### 2.1. Event Loop

Trong Javascript, có một khái niệm quan trọng là **Event Loop**. Nó là một vòng lặp vô hạn mà trong đó, engine của Javascript liên tục kiểm tra xem có công việc gì cần thực hiện hay không.

### 2.2. Event Queue

Khi một hàm bất đồng bộ như `setTimeout` được gọi, callback của nó không được thực thi ngay lập tức. Thay vào đó, nó sẽ được đặt vào một hàng đợi gọi là **Event Queue**. Chỉ khi mọi công việc trong **execution stack** (stack thực thi) đã xong, Event Loop mới bắt đầu lấy các công việc từ Event Queue ra và thực thi nó.

### 2.3. Ví dụ

#### 2.3.1. Vòng lặp sử dụng `var`

Khi sử dụng `var`:

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1);
}
```

Biến `i` được khai báo bằng `var` nên nó có phạm vi toàn cục vậy suy ra từ đầu đến cuối chỉ có một biết i duy nhất. Khi vòng lặp kết thúc, giá trị của `i` sẽ là 3. Nhớ lại về **Event Queue**, hàm `setTimeout` sẽ không thực thi ngay mà sẽ chờ đến khi tất cả các vòng lặp hoàn tất. Do đó, khi nó thực thi, giá trị của `i` là 3 và chúng ta sẽ thấy output là `3 3 3`.

#### 2.3.2. Vòng lặp sử dụng `let`

Khi sử dụng `let`:

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1);
}
```

Tại mỗi vòng lặp, `i` là một biến mới. Điều này có nghĩa là mỗi callback `setTimeout` sẽ "nhớ" giá trị của `i` tại thời điểm nó được tạo ra. Vì vậy, khi `setTimeout` được thực thi từ **Event Queue**, nó sẽ in ra giá trị `i` tại thời điểm callback đó được tạo: `0 1 2`.

Bạn đã thấy sự khác biệt khi sử dụng `var` và `let` trong một vòng lặp kết hợp với hàm bất đồng bộ `setTimeout` rồi đúng không. Điều này cho thấy sự quan trọng của việc hiểu rõ cách Javascript xử lý code và tầm quan trọng của việc chọn đúng từ khóa khi khai báo biến.🔥

Kinh nghiệm của mình là hãy luôn cần thận khi sử dụng `var` chỉ sử dụng khi hiểu rõ scrope của nó. Trong thực tế thì hiện tại đa phần mọi người chỉ sử dụng `let` và `const` để tránh những bug không đáng có.

## 3. **"Arrow Function" và `this`**

```js
const shape = {
  radius: 10,
  diameter() {
    return this.radius * 2;
  },
  perimeter: () => 2 * Math.PI * this.radius
};

console.log(shape.diameter());  // Gì sẽ xuất hiện?
console.log(shape.perimeter()); // Còn ở đây thì sao?
```

Tại sao khi thực thi kết quả lại là: `20` and `NaN` mà không phải là `20` and `62.83185307179586`

Thực ra điều đặc biệt ở đoạn code bên trên là do nó đang sử dụng hai kiểu function: **hàm thông thường (regular function)** và **arrow function**. Điểm khác biệt chính giữa chúng là cách chúng xử lý từ khóa `this`.

### 3.1. Định nghĩa đối tượng `shape`

```js
const shape = {
  radius: 10,
  diameter() {
    return this.radius * 2;
  },
  perimeter: () => 2 * Math.PI * this.radius
};
```

Ở đây, `shape` là một đối tượng có 3 thuộc tính: `radius`, `diameter`, và `perimeter`.

- `radius` là một thuộc tính có giá trị là `10`.
- `diameter` là một phương thức (method) thông thường.
- `perimeter` là một arrow function.

### 3.2. Hiểu rõ về `this` trong phương thức thông thường

Khi bạn gọi một phương thức thông thường, giá trị của `this` trong phương thức đó sẽ trỏ tới đối tượng gọi phương thức.

Ví dụ:

```js
shape.diameter();  // Kết quả là 20
// this chính là shape
```

Khi gọi `shape.diameter()`, `this` trong hàm `diameter` sẽ trỏ tới đối tượng `shape`, và trả về giá trị `radius * 2` tức là `10 * 2` -> Kết quả: 20.

### 3.3. Arrow Function và bí mật của `this`

Quay lại vấn đề chính của chúng ta

Khác với phương thức thông thường, arrow function không tạo ra một context `this` riêng. Thay vào đó, nó "bắt" `this` từ surrounding scope.

Trong trường hợp của `shape.perimeter`, arrow function đang ở trong context của đối tượng `shape`, nhưng giá trị `this` của nó sẽ không trỏ tới `shape`. Thay vào đó, nó sẽ trỏ tới surrounding scope (global scope, ví dụ trong trường hợp chạy trên browser là `window`).

```js
shape.perimeter();  // Kết quả là NaN
```

Do `window.radius` không tồn tại nên giá trị trả về sẽ là `2 * Math.PI * undefined` -> Kết quả: NaN.

### 3.4. Ví dụ minh họa

Để hiểu rõ hơn về sự khác biệt này, hãy xem xét ví dụ sau:

```js
const myObject = {
  value: "Hello, World!",
  normalFunction: function() {
    console.log(this.value);
  },
  arrowFunction: () => {
    console.log(this.value);
  }
};

myObject.normalFunction();  // Kết quả: "Hello, World!"
myObject.arrowFunction();  // Kết quả: undefined (hoặc có thể khác tùy context)
```

Với `normalFunction`, `this` trỏ tới `myObject` nên trả về giá trị "Hello, World!". Tuy nhiên, với `arrowFunction`, `this` không trỏ tới `myObject` mà trỏ tới surrounding scope.

### 3.5. Giải thích thêm về Surrounding Scope và Lexical Scope

Để hiểu rõ hơn về khái niệm surrounding scope, mình cần phải nắm vững ý tưởng về "lexical scope". "Lexical" ở đây có nghĩa là "liên quan đến từ vựng hoặc cú pháp". Trong JavaScript, khi chúng ta nói đến "lexical", chúng ta đang nói về vị trí cụ thể của block code đó trong source code. (vị trí block code được viết ra.)

Vậy, "lexical scope" có nghĩa là phạm vi mà một biến có thể được truy cập dựa trên vị trí block code của nó trong chương trình, chứ không phải là cách chúng ta gọi hàm hay block code đó. Và Surrounding Scope là phạm vi mà block code hiện tại được bao quanh bởi Lexical Scope.

Ôi lý thuyết,... nhức đầu quá men, cho một ví dụ để giễ hiểu coi! Ok, giả sử mình có một ví dụ cơ bản:

```js
let a = 'global';

function checkScope() {
    let a = 'local';
    
    function innerCheck() {
        console.log(a);
    }
    
    innerCheck();
}

checkScope(); // Kết quả?
```

Khi chúng ta gọi hàm `checkScope`, hàm `innerCheck` được gọi bên trong nó. Vậy `innerCheck` sẽ log giá trị nào của `a` ra? Chính xác, kết quả sẽ là 'local' bởi vì lexical scope của hàm `innerCheck` chứa giá trị `a` ở mức hàm `checkScope`.

Quay lại với arrow functions trong JavaScript, chúng không tạo ra một "lexical scope" mới cho `this`. Thay vào đó, `this` trong arrow function được quyết định dựa trên lexical scope xung quanh. Điều này là nguyên nhân khi chúng ta sử dụng arrow function cho `perimeter` trong ví dụ trên, `this` không trỏ đến object `shape`, mà lại trỏ đến surrounding scope, thường là `window` (hoặc `global` nếu bạn đang ở môi trường Node.js).

Vậy, nếu mình thử thực hiện:

```js
console.log(this.radius);
```

Ở global scope, kết quả sẽ là `undefined`. Vì thế, khi arrow function `perimeter` được thực thi, nó cũng trả về `NaN` do phép tính trên giá trị `undefined`.

Ồ vẫn hơi khó hiểu nhỉ... thử vào một ví dụ thử xem sao.

Ví dụ: Arrow Function bên trong một hàm khác

```js
function outerFunction() {
    this.value = 30;
    return {
        value: 40,
        arrowFunc: () => {
            console.log(this.value);
        },
        normalFnc: function () {
            console.log(this.value);
        }
    };
}

const object = outerFunction();
object.arrowFunc();   // 30
object.normalFnc();   // 40
```

Ở ví dụ này, `outerFunction` khai báo một biến `value` với `this` và trả về một object có Arrow Function `arrowFunc`. Khi chúng ta gọi `object.arrowFunc()`, `this` trong Arrow Function sẽ trỏ tới `this` của `outerFunction` chứ không phải object mà nó trả về. Do đó, kết quả in ra là 30 chứ không phải 40. Tuy nhiên `normalFnc` thì `this` chính là đang trỏ tới `object`.

Từ hai ví dụ trên, các bạn có thể thấy rằng Arrow Function không quan tâm nó được gọi từ đâu mà chỉ quan tâm nó được khai báo ở đâu. `this` trong Arrow Function luôn trỏ về "surrounding scope - vị trí nó được code ra" mà nó được định nghĩa.

Vậy nên, khi viết code, mình cần cẩn thận khi sử dụng Arrow Function trong những ngữ cảnh mà `this` chơi một vai trò quan trọng.

Nhớ điều này khi sử dụng arrow functions! Trong một số trường hợp, chúng rất tiện lợi, nhưng khi làm việc với object methods và bạn muốn truy cập các thuộc tính của object đó thông qua `this`, hàm thông thường có lẽ sẽ là lựa chọn tốt hơn.

Bonus:

```js
// Surrounding Scope cho cả function outerFunction
function outerFunction() {
    this.value = 30; // Ông này chính là Lexical Scope của outerFunction

    return {
        value: 40, // Bà này chính là Lexical Scope của đối tượng trả về khi gọi hàm outerFunction

        // Vì đây là arrow function, nó không tạo ra lexical scope riêng cho `this`, thay vào đó, nó "nhớ" `this` từ Surrounding Scope (ở đây là outerFunction).
        arrowFunc: () => {
            console.log(this.value); // `this` ở đây tham chiếu đến outerFunction
        },

        // Function này tạo ra một Lexical Scope riêng cho `this`, tham chiếu đến đối tượng trả về
        normalFnc: function () {
            console.log(this.value); // `this` ở đây tham chiếu đến đối tượng trả về
        }
    };
}

const object = outerFunction();
object.arrowFunc();   // 30
object.normalFnc();   // 40
```

### 3.6. Tóm lại

Khi sử dụng `this` trong JavaScript, các bạn cần phải rất chú ý đến ngữ cảnh và loại function mình đang sử dụng. Arrow functions có nhiều ưu điểm, nhưng chúng cũng mang theo những sự khác biệt quan trọng, đặc biệt là cách thức hoạt động của `this`.

Vậy nên, nếu bạn cần tham chiếu đến thuộc tính của object thông qua `this`, hãy sử dụng **hàm thông thường** thay vì arrow function nhé! Mình hy vọng các bạn đã hiểu rõ hơn về `this` và arrow functions trong JavaScript.

## **4. Phép toán cộng `+` trong JavaScript**

Ta có đoạn code sau:

```js
+true;
!"Lydia";
```

Kết quả sau khi thực thi sẽ là: `1` and `false`

1. Đối với `+true`: Kết quả là `1`
2. Đối với `!"Lydia"`: Kết quả là `false`

Ồ... tại sao ko phải là `false and NaN` hay `false and false` mà lại là `1 and false`.

Đầu tiên, mình cùng xem lại đoạn code:

```js
+true;
```

Ở đây, chúng ta đang dùng phép toán cộng một cách không trực tiếp. Trong JavaScript, khi bạn đặt dấu `+` trước một biến hoặc giá trị, đó chính là việc bạn muốn chuyển giá trị đó thành số.

Mình có một ví dụ khác cho các bạn:

```js
let x = "5";
console.log(+x);  // Kết quả: 5 (dưới dạng số)
```

Quay lại với `+true`, khi chúng ta convert giá trị boolean `true` thành số, kết quả sẽ là `1`. Đúng rồi, đó chính là số `1` mà bạn thấy.

### 4.1. Bổ sung một chút về giá trị boolean

Cái mình muốn nói ở đây là:

- `true` khi chuyển thành số sẽ là `1`.
- `false` khi chuyển thành số sẽ là `0`.

Mình đã kiểm tra lại bằng cách làm như thế này:

```js
console.log(+true);   // Kết quả: 1
console.log(+false);  // Kết quả: 0
```

### 4.2. Xem xét chuỗi và giá trị truthy/falsy

Chúng ta lại xem đoạn code:

```js
!"Lydia";
```

Ở đây, dấu `!` trước chuỗi nghĩa là chúng ta đang phủ định (negate) giá trị của chuỗi đó. Đối với JavaScript, một chuỗi không rỗng sẽ luôn có giá trị là truthy.

Chắc các bạn còn nhớ, `truthy` là gì chứ? Đó là những giá trị mà khi chúng ta chuyển thành boolean, chúng sẽ trở thành `true`. Gồm các giá trị sau:

1. Số nguyên dương và số thập phân khác không (nghĩa là khác 0).
2. Chuỗi ký tự không rỗng.
3. Đối tượng không rỗng.
4. Mảng không rỗng.
5. Giá trị boolean `true`.
6. Giá trị đại diện cho một hàm hoặc biểu thức hợp lệ.
7. Đối tượng hoặc mảng không rỗng được coi là "truthy" ngay cả khi chứa các giá trị rỗng bên trong.

Các giá trị còn lại thường được đánh giá là "falsy" và chúng sẽ được xem như giá trị sai trong ngữ cảnh của điều kiện. Một số ví dụ về giá trị "falsy" bao gồm:

1. Số nguyên 0 và số thập phân 0.0.
2. Chuỗi ký tự rỗng.
3. Giá trị boolean false.
4. Giá trị null hoặc undefined.
5. Đối tượng hoặc mảng rỗng.

Vậy nên, `!"Lydia"` sẽ là gì? Chính xác, đó sẽ là `false`. Vì "Lydia" là `truthy` và `!truthy` là `falsy`.

Mình minh họa lại nè:

```js
console.log(!"Lydia");   // Kết quả: false
console.log(!"");        // Kết quả: true
```

Chú ý rằng, chuỗi rỗng `""` lại là một giá trị falsy. Vì vậy, `!""` sẽ trả về `true`.

## **5. Object và truy xuất thuộc tính**

Trước hết, để hiểu rõ vấn đề này, mình cần phải hiểu object trong JavaScript là gì? Object là một kiểu dữ liệu phức tạp cho phép bạn lưu trữ nhiều dữ liệu dưới dạng cặp key-value.

Mình có thể truy cập giá trị của thuộc tính (value) trong một object qua tên thuộc tính (key) bằng cách sử dụng cú pháp dấu chấm (.) hoặc cặp dấu ngoặc vuông ([]).

Trong JavaScript thì tất cả `keys` của các `object` đều là `string` (ngoại trừ khi nó là một `Symbol`). Dù chúng ta không viết chúng như một `string`, về cơ bản chúng sẽ luôn được chuyển sang dạng `string`.

JavaScript thông dịch (hay `unboxes`) từng câu lệnh. Khi chúng ta sử dụng cặp dấu ngoặc [], nó sẽ tìm kiếm dấu mở ngoặc đầu tiên [, và sẽ tiếp tục tìm kiếm cho tới khi gặp dấu đóng ngoặc ]. Chỉ khi đó thì câu lệnh mới được thực thi.

### 5.1 Phân tích cụ thể qua ví dụ

Ta có đoạn code sau:

```js
const bird = {
  size: "small"
};

const mouse = {
  name: "Mickey",
  small: true
};
```

#### 5.1.1 Lỗi điển hình: **mouse.bird.size**

Ở đây, chúng ta đang cố gắng truy cập vào thuộc tính `bird` của object `mouse`, nhưng rõ ràng object `mouse` không có thuộc tính này. Vì vậy, `mouse.bird` sẽ trả về `undefined`. Lúc này, việc truy cập vào `size` từ `undefined` sẽ gây ra lỗi.

=> Đây là lỗi rất điển hình mà các bạn mới hay gặp phải.

#### 5.1.2 mouse[bird.size] và mouse[bird["size"]]

Hai biểu thức này giống nhau, và cả hai đều truy cập vào thuộc tính `size` của object `bird`, giá trị trả về là string "small". Vậy nên, `mouse[bird.size]` và `mouse[bird["size"]]` sẽ tương đương với việc truy cập `mouse["small"]`.

Và, rõ ràng trong object `mouse`, mình có thuộc tính `small` với giá trị là `true`.

=> Cả hai đều hợp lệ.

#### 5.1.3 Lưu ý khi truy xuất thuộc tính của object

- Khi sử dụng cú pháp dấu chấm (.), tên thuộc tính không được chứa dấu cách và phải tuân theo các quy tắc đặt tên biến.
- Trong khi đó, khi sử dụng cặp dấu ngoặc vuông ([]), tên thuộc tính có thể là bất kỳ giá trị nào, và chúng sẽ được tự động chuyển đổi thành string (ngoại trừ `Symbol`).

### 5.2. Tóm lại

Trong JavaScript, việc truy cập thuộc tính của object là một tính năng mạnh mẽ và linh hoạt. Nhưng cũng cần phải cẩn trọng để không truy cập vào thuộc tính không tồn tại, gây ra lỗi. Chúng ta đã thấy điều này qua ví dụ `mouse.bird.size`.

Tốt nhất là khi code, hãy luôn kiểm tra sự tồn tại của thuộc tính trước khi truy cập để tránh các lỗi không mong muốn!