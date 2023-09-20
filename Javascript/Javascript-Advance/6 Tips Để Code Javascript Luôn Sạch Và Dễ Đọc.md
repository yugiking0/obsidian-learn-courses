# # 6 Tips Để Code Javascript Luôn Sạch Và Dễ Đọc
**Trong một dự án dù lớn hay nhỏ thì code của chúng ta cần phải dễ đọc và dễ bảo trì. Việc để code luôn "sạch" và dễ đọc là một nghệ thuật trong lập trình, để nắm được những nghệ thuật đó thì chúng ta cùng nhau tìm hiểu qua bài viết này nhé.**

### 1. Dấu ngoặc nhọn

Hầu hết trong các dự án Javascript, dấu ngoặc nhọn được viết theo kiểu "Egyptian" (ai cập) - với dấu mở ngoặc nằm cùng một hàng với từ khóa tương ứng - không phải là một hàng khác. Thêm nữa là có một khoảng trắng trước dấu mở ngoặc: 

```javascript
if (condition) {
  // do something
}
```

Ngoài ra còn có một số cách viết khác.

1. Những bạn mới học thường viết như thế này. Dấu ngoặc nhọn lúc này **không cần thiết**
    
    ```javascript
    if (n < 0) {alert('This number is negative');}​
    ```
    
2. **Không** sử dụng dấu ngoặc nhọn và viết ở dòng mới. Làm như thế này sẽ dễ gây ra lỗi khi ta thêm những đoạn code mới.
    
    ```javascript
    if (n <0)
      alert('This number is negative')​;
    ```
    
3. Viết tất cả trên một dòng và không sử dụng dấu ngoặc nhọn - **Được** nếu đoạn code ngắn.
    
    ```javascript
    if (n < 0) alert('This number is negative');​
    ```
    
4. Đây là cách mình khuyên mọi người nên dùng:
    
    ```javascript
    if (n < 0) {
      alert('This number is negative');
    }​
    ```
    

### 2. Độ dài của một dòng.

Mình chắc rằng sẽ **không một ai** thích đọc một dòng code dài ngoằn ngoèo. Đôi lúc mọi người khi code cũng sẽ gặp vấn đề đó. Và cách giải quyết vấn đề này là chia nó ra sang những dòng khác.

```javascript
// Sử dụng dấu `` để chia một string ra thành nhiều dòng.

let str = `
  The quick brown fox jumps
  over the lazy dog
`;
```

Với câu lệnh if

```javascript
if (
  id === 123 &&
  firstName === 'Matt' &&
  lastName === 'Nguyen'
) {
  letSayHello();
}
```

### 3. Thụt lề.

Có 2 loại thụt lề:

#### Thụt ngang: 2 hoặc 4 phím space.

Thụt lề ngang được thực hiện bằng cách sử dụng 2 hoặc 4 phím space hoặc dùng phím Tab. Cách nào cũng được nhưng sử dụng phím Space ngày nay phổ biến hơn.

Ưu điểm của phím space là linh hoạt thụt lề hơn phím Tab.

#### Thụt dọc: những dòng trống để chia đoạn code ra thành từng khối một cách logic.

Trong một function cũng có thể được chia ra thành các phần thực hiện công việc riêng biệt. Trong ví dụ dưới đây, việc khởi tạo biến, dùng vòng lặp được chia theo chiều dọc.

```javascript
function pow(x, n) {
  let result = 1;
  //              <--
  for (let i = 0; i < n; i++) {
    result *= x;
  }
  //              <--
  return result;
}
```

Việc chừa ra một dòng giúp cho code dễ đọc hơn.

### 4. Dấu chấm phẩy.

Dấu chấm phẩy nên được đặt sau mỗi lệnh, thậm chí việc bỏ qua nó vẫn không ảnh hưởng đến chương trình.

Có những ngôn ngữ lập trình khi mà dấu chấm phẩy là tùy chọn và hiếm khi được sử dụng. Trong Javascript, mặc dù có những trường hợp ngắt một dòng không được hiểu là dấu chấm phẩy ( ví dụ khi xử lý một Promise), khiến đoạn code dễ gây ra lỗi. 

### 5. Nesting Levels.

Cố gắng tránh để những đoạn code lồng nhau quá nhiều tầng.

Ví dụ, khi sử dụng vòng lặp, sử dụng `continue`; là một cách để tránh việc thêm một nesting level.

Thay vì viết như thế này:

```javascript
for (let i = 0; i < 10; i++) {
  if (cond) {
    ... // <- thêm một nesting level
  }
}
```

Ta có thể viết:

```javascript
for (let i = 0; i < 10; i++) {
  if (!cond) continue;
  ...  // <- tránh việc thêm nesting level
}
```

Chúng ta có thể làm điều tương tự với `if` `else` và `return`

Thay vì:

```javascript
function pow(x, n) {
  if (n < 0) {
    alert("Negative 'n' not supported");
  } else {
    let result = 1;

    for (let i = 0; i < n; i++) {
      result *= x;
    }

    return result;
  }
}
```

Ta có thể viết

```javascript
function pow(x, n) {
  if (n < 0) {
    alert("Negative 'n' not supported");
    return;
  }

  let result = 1;

  for (let i = 0; i < n; i++) {
    result *= x;
  }

  return result;
}
```

Mình chắc rằng khá nhiều bạn thường viết theo cách 1.

Cách 2 dễ đọc hơn vì trường hợp đặc biệt n < 0 đã được xử lý sớm. Khi mà kiểm tra xong chúng ta sẽ vào thẳng đoạn code chính mà không cần thêm một nested level.

### 6. Đặt function

Nếu bạn viết một vài "helper" function và sử dụng chúng, có 3 cách để tổ chức những function này.

1. Khai báo functions rồi sau đó sử dụng nó.
    
    ```javascript
    // khai báo function
    function createElement() {
      ...
    }
    
    function setHandler(elem) {
      ...
    }
    
    function walkAround() {
      ...
    }
    
    // code sử dụng những function này
    let elem = createElement();
    setHandler(elem);
    walkAround();​
    ```
    
2. Code trước sau đó đến functions
    
    ```javascript
    // code sử dụng functions
    let elem = createElement();
    setHandler(elem);
    walkAround();
    
    // --- helper functions ---
    function createElement() {
      ...
    }
    
    function setHandler(elem) {
      ...
    }
    
    function walkAround() {
      ...
    }​
    ```
    
3. Kết hợp: function được khai báo tại nơi nó được sử dụng đầu tiên

Hầu hết cách số 2 thường được sử dụng hơn bời vì điều trước tiên chúng ta muốn biết là đoạn code làm gì (nhìn tên function là biết ngay).

Ngoài ra còn có một số coding style phổ biến khác như **Google Javascript Style**, **Airbnb Javascript Style**, **StandardJs.** Bên cạnh đó cũng có tool tự động format code của bạn theo một chuẩn có sẵn như **JSLint**, **JSHint**, **ESLint.**

### Tạm kết

Trên đây là một số coding styles trong javascript mình thường sử dụng. Điều này giúp mình mỗi khi đọc lại code mình mất ít thời gian hơn để hiểu đoạn code đó, mục đích của nó là gì. Hy vọng sẽ giúp các bạn mới học lập trình Javascript. Nếu có ý kiến hoặc đóng góp các bạn comment xây dựng bên dưới nhé. Chúc các bạn học tốt.