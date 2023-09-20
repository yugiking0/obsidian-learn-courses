# PEAN Stack Day 3 - This, Bind, Call, Apply

# Day 3: `This`, `Bind`, `Call`, `Apply` trong Javascript

Hãy cùng mình tìm hiểu một chút về `this`, `bind`, `call`, và `apply` trong Javascript nhé! Đôi khi việc làm quen với những khái niệm này có thể hơi rối bời, nhưng sau khi đã hiểu rõ, các bạn sẽ thấy chúng thực sự hữu ích.

## 1. `This` trong Javascript

### 1.1. Khái niệm cơ bản

`this` không phải là một biến cố định, mà giá trị của nó thay đổi tùy theo cách gọi hàm.

### 1.2. Ví dụ

- **Ví dụ 1**: Trong method của object:
    
    ```javascript
    const person = {
      name: 'An',
      greet: function() {
        console.log(`Hello, my name is ${this.name}`);
      }
    };
    person.greet(); // Hello, my name is An
    ```
    
    **Giải thích**: Ở đây, `this` trong `greet` method chính là đối tượng `person` vì method được gọi từ object đó. Do đó, `this.name` sẽ trả về "An".
    
- **Ví dụ 2**: Khi gọi một hàm bình thường:
    
    ```javascript
    function introduce() {
      console.log(this);
    }
    introduce(); // Window {...}
    ```
    
    **Giải thích**: Khi một hàm bình thường được gọi (không thông qua một đối tượng hoặc không được bind), `this` mặc định sẽ trỏ đến `window` (trong trình duyệt).
    
- **Ví dụ 3**: Khi dùng `this` trong một hàm callback:
    
    ```javascript
    const myBtn = document.querySelector('.myBtn');
    myBtn.addEventListener('click', function() {
      console.log(this); // <button class="myBtn">Click me!</button>
    });
    ```
    
    **Giải thích**: Trong trường hợp này, `this` chính là element mà sự kiện được gắn lên, trong trường hợp này là nút `.myBtn`.
    

## 2. `Bind`

`Bind`, `Call` và `Apply`: Ba thằng này đơn giản giúp chúng ta kiểm soát cách sử dụng `this`.

### 2.1. Khái niệm

`bind` giúp chúng ta "ép buộc" một giá trị cụ thể cho `this` trong một function.

### 2.2. Ví dụ

- **Ví dụ 1**:
    
    ```javascript
    function greet() {
      console.log(`Hello, my name is ${this.name}`);
    }
    const person = {
      name: 'Bao'
    };
    const boundGreet = greet.bind(person);
    boundGreet(); // Hello, my name is Bao
    ```
    
    **Giải thích**: Dùng `bind`, ta có thể "ép" `this` trong hàm `greet` trỏ đến đối tượng `person`. Vì vậy, khi gọi `boundGreet()`, giá trị của `this.name` sẽ là "Bao".
    
- **Ví dụ 2**:
    
    ```javascript
    const timer = {
      seconds: 10,
      start: function() {
        setInterval(function() {
          if(this.seconds > 0) {
            console.log(this.seconds--);
          }
        }.bind(this), 1000);
      }
    };
    timer.start();
    ```
    
    **Giải thích**: Ở đây, nếu không có `bind(this)`, giá trị của `this` trong hàm callback của `setInterval` sẽ trở thành `window`, không phải là đối tượng `timer`. Nhưng nhờ `bind(this)`, `this` giữ nguyên là `timer` và code hoạt động như mong đợi.
    

## 3. `Call` và `Apply`

### 3.1. Khái niệm

Cả hai đều dùng để gọi hàm với một giá trị `this` và các tham số cụ thể. Khác biệt chính là cách truyền tham số: `call` truyền trực tiếp, còn `apply` truyền qua một mảng.

### 3.2. Ví dụ

- **Ví dụ với `call`**:
    
    ```javascript
    function introduce(hobby1, hobby2) {
      console.log(`Hello, I'm ${this.name}. I like ${hobby1} and ${hobby2}`);
    }
    const person = {
      name: 'Minh'
    };
    introduce.call(person, 'coding', 'reading'); 
    ```
    
    **Giải thích**: Ở đây, chúng ta dùng `call` để gọi hàm `introduce` với `this` là `person` và hai tham số là 'coding' và 'reading'.
    
- **Ví dụ với `apply`**:
    
    ```javascript
    function introduce(hobbies) {
      console.log(`Hello, I'm ${this.name}. I like ${hobbies.join(' and ')}`);
    }
    const person = {
      name: 'Hoa'
    };
    introduce.apply(person, [['singing', 'dancing']]);
    ```
    
    **Giải thích**: Khác với `call`, `apply` yêu cầu truyền tham số dưới dạng một mảng. Ở đây, chúng ta truyền một mảng gồm hai phần tử 'singing' và 'dancing'.
    

---

# **English Version**

Hey, friends! 🖐 Let's chat about a few cool things in Javascript: `this`, `bind`, `call`, and `apply`. They might seem a bit confusing at first, but trust me, once you get them, they're super handy!

## 1. The Magic of `This` in Javascript

### 1.1. What's it all about?

Imagine `this` as a magic word that doesn't always mean the same thing. It changes depending on how we're using it in our code.

### 1.2. Show me some examples!

- **Example 1**: Inside an object method:
    
    ```javascript
    const person = {
      name: 'An',
      greet: function() {
        console.log(`Hello, my name is ${this.name}`);
      }
    };
    person.greet(); // Outputs: Hello, my name is An
    ```
    
    **Plain Talk**: Here, `this` means the `person` object because the method is part of that object. So, `this.name` gives us "An".
    
- **Example 2**: Calling a regular function:
    
    ```javascript
    function introduce() {
      console.log(this);
    }
    introduce(); // Outputs: Window {...}
    ```
    
    **Plain Talk**: If you just call a normal function without tying it to anything, `this` just points to the whole browser window.
    
- **Example 3**: Using `this` in a callback:
    
    ```javascript
    const myBtn = document.querySelector('.myBtn');
    myBtn.addEventListener('click', function() {
      console.log(this); 
    });
    ```
    
    **Plain Talk**: Here, `this` is pointing to the button we clicked on, the one with `.myBtn` class.
    

## 2. The Power of `Bind`

The trio of `Bind`, `Call`, and `Apply` help us tell Javascript exactly what we want `this` to mean.

### 2.1. What's it about?

`bind` is like telling a function: "Hey, I want you to use `this` value every time you're called!"

### 2.2. Give me examples!

- **Example 1**:
    
    ```javascript
    function greet() {
      console.log(`Hello, my name is ${this.name}`);
    }
    const person = {
      name: 'Bao'
    };
    const boundGreet = greet.bind(person);
    boundGreet(); // Outputs: Hello, my name is Bao
    ```
    
    **Plain Talk**: With `bind`, we told the function to think of `this` as the `person` object. So, when we called it, `this.name` meant "Bao".
    
- **Example 2**:
    
    ```javascript
    const timer = {
      seconds: 10,
      start: function() {
        setInterval(function() {
          if(this.seconds > 0) {
            console.log(this.seconds--);
          }
        }.bind(this), 1000);
      }
    };
    timer.start();
    ```
    
    **Plain Talk**: If we didn't use `bind(this)`, the function would get confused and think `this` was the whole browser window. But thanks to `bind(this)`, it correctly thinks of `this` as the `timer` object.
    

## 3. Dive into `Call` & `Apply`

### 3.1. What are these?

Both `call` and `apply` let us call a function and tell it what `this` should be. They're like siblings but have a tiny difference in how they want their info.

### 3.2. Show and tell, please!

- **Example with `call`**:
    
    ```javascript
    function introduce(hobby1, hobby2) {
      console.log(`Hello, I'm ${this.name}. I like ${hobby1} and ${hobby2}`);
    }
    const person = {
      name: 'Minh'
    };
    introduce.call(person, 'coding', 'reading'); 
    ```
    
    **Plain Talk**: Here, we're telling the function to use `person` as `this`. And, we're giving it two hobbies directly.
    
- **Example with `apply`**:
    
    ```javascript
    function introduce(hobbies) {
      console.log(`Hello, I'm ${this.name}. I like ${hobbies.join(' and ')}`);
    }
    const person = {
      name: 'Hoa'
    };
    introduce.apply(person, [['singing', 'dancing']]);
    ```
    
    **Plain Talk**: The difference is, `apply` wants the hobbies in a list, like a shopping list. So we give it a list of hobbies.
    

Hope that clears things up! Remember, practice makes perfect. Keep coding and have fun! 🚀🤓🎉