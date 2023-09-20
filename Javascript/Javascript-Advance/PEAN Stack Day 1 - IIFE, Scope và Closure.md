# PEAN Stack Day 1 - IIFE, Scope và Closure
Mở đầu series mới về PEAN stack, mình sẽ cùng các bạn tìm hiểu 3 khái niệm hay ho trong Javascript: **IIFE**, **Scope**, và **Closure**. Đây là những khái niệm mà mình tin rằng mọi javascript developer cần nắm vững!

## 1. IIFE - Immediately Invoked Function Expressions

### 1.1. Khái niệm

Các bạn đã bao giờ tự hỏi, làm cách nào tạo một function và tự động thực thi nó ngay lập tức không? Đó chính là IIFE!

**IIFE** là cách mà chúng ta có thể tạo một function và chạy nó ngay lập tức mà không cần gọi tên function đó.

Ví dụ:

```javascript
(function() {
    console.log("Đây là IIFE!"); // Đây là IIFE!
})();
```

### 1.2. Ứng dụng

Một ứng dụng thực sự hữu ích của IIFE là giúp chúng ta tạo ra "private variables" trong Javascript. Với IIFE, biến bên trong function sẽ không bị ảnh hưởng bởi các biến bên ngoài.

Ví dụ:

```javascript
var name = "IT VN Chất";

(function() {
    var name = "Private World!";
    console.log(name); // Private World!
})();

console.log(name); // IT VN Chất
```

## 2. Scope

### 2.1. Khái niệm

Scope giúp chúng ta kiểm soát và quản lý phạm vi hoạt động của biến. Trong Javascript, chúng ta có 2 loại scope chính là: **Global Scope** và **Local Scope**.

### 2.2. Ứng dụng

- **Global Scope**: Khi một biến được khai báo bên ngoài function.
    
    ```javascript
    var globalVar = "Tôi là global!";
    
    function checkScope() {
        console.log(globalVar); // Tôi là global!
    }
    
    checkScope();
    ```
    
- **Local Scope**: Khi một biến được khai báo bên trong function.
    
    ```javascript
    function checkScope() {
        var localVar = "Tôi là local!";
        console.log(localVar); // Tôi là local!
    }
    
    checkScope();
    console.log(localVar); // Error: localVar is not defined
    ```
    

## 3. Closure

### 3.1. Khái niệm

**Closure** là một function được tạo ra bởi một function khác. Đặc điểm nổi bật là closure có thể truy cập vào các biến của function cha của nó.

### 3.2. Ứng dụng

Closure giúp chúng ta tạo ra các private methods hay variables trong Javascript.

Ví dụ:

```javascript
function makeCounter() {
    var count = 0;
    
    return function() {
        return count++;
    };
}

var counter = makeCounter();

console.log(counter()); // 0
console.log(counter()); // 1
```

Trong ví dụ trên, function bên trong truy cập và tăng biến `count` mặc dù nó được định nghĩa ngoài cùng. Điều này chỉ có thể xảy ra nhờ Closure.

## Một số ví dụ khác

### IIFE (Immediately Invoked Function Expressions)

#### Ví dụ 1: Sử dụng IIFE để khởi tạo một plugin

Giả sử bạn đang viết một plugin jQuery và muốn đảm bảo không ảnh hưởng tới các biến hoặc hàm ngoài.

```javascript
(function($) {
    // Bên trong đây, $ sẽ là jQuery
    $(document).ready(function() {
        // Mã của plugin
    });
})(jQuery);
```

Ở đây, chúng ta sử dụng IIFE để tránh xung đột giữa jQuery và các thư viện khác. `$` bên trong IIFE sẽ luôn ám chỉ jQuery.

#### Ví dụ 2: Khởi tạo một biến chỉ đọc

```javascript
var CONSTANTS = (function() {
    var secretKey = "12345";
    return {
        API_URL: "https://myapi.com",
        getSecretKey: function() {
            return secretKey;
        }
    };
})();

console.log(CONSTANTS.API_URL); // https://myapi.com
console.log(CONSTANTS.getSecretKey()); // 12345
```

Trong ví dụ này, IIFE giúp tạo ra một object `CONSTANTS` mà người dùng chỉ có thể truy cập thông qua các phương thức được cung cấp.

### Scope

#### Ví dụ 1: Sử dụng block scope để xử lý dữ liệu

```javascript
{
    let temporaryData = "data";
    // Xử lý temporaryData
    console.log(temporaryData); // "data"
}

//console.log(temporaryData); // Lỗi: temporaryData không tồn tại
```

Ở ví dụ này, `temporaryData` chỉ tồn tại trong block `{}`, giúp tránh làm ô nhiễm global scope.

#### Ví dụ 2: Sử dụng function scope để tạo biến riêng biệt

```javascript
function processData(data) {
    var processed = "Processed: " + data;
    return processed;
}

console.log(processData("myData")); // Processed: myData
//console.log(processed); // Lỗi: processed không tồn tại
```

Ở đây, biến `processed` chỉ tồn tại trong hàm `processData`, giúp tách biệt logic xử lý.

### Closure

#### Ví dụ 1: Tạo một hàm tăng giá trị

```javascript
function createIncrementer() {
    let count = 0;
    return function() {
        return count++;
    };
}

const increment = createIncrementer();

console.log(increment()); // 0
console.log(increment()); // 1
```

Hàm `createIncrementer` trả về một closure giữ lại trạng thái của `count` mỗi khi gọi hàm `increment`.

#### Ví dụ 2: Ẩn dữ liệu bên trong một module

```javascript
var Module = (function() {
    var privateData = "I am private";

    return {
        getPrivateData: function() {
            return privateData;
        }
    };
})();

console.log(Module.getPrivateData()); // "I am private"
//console.log(Module.privateData); // undefined
```

Sử dụng closure, chúng ta có thể tạo ra các module với dữ liệu và phương thức riêng tư. Trong ví dụ trên, `privateData` chỉ có thể truy cập thông qua hàm `getPrivateData`.
