# Tất tần tật về Javascript OOP ES6

# Giới thiệu về javascript oop

Trong lập trình hướng đối tượng (OOP) có 4 tính chất là:
- **Tính đóng gói** (*Encapsulation*) [[#Tính đóng gói (Encapsulation)]]
- **Tính kế thừa** (*Inheritance*) [[#Kế thừa lớp (Inheritance)]]
- **Tính đa hình** (*Polymorphism*) 
- **Tính trừu tượng** (*Abstraction*)

Ở các phiên bản trước ES6 thì việc thể hiện các tính chất này khá là rắc rối và khó đọc (gần như là chỉ mô phỏng), thì trong es6 với 1 loạt các cập nhật mới đã khiến cho việc cài đặt oop trở nên dễ dàng hơn

# Pre ES6

Trước ES6 người ta hay dùng Object để định nghĩa đối tượng, mình sẽ lấy một ví dụ là ta có 2 lớp Person và Worker, lớp worker sẽ kế thừa lớp Person đồng thời sẽ sử dụng lại hàm print từ lớp person, cú pháp của nó như sau

```node
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.print = function() {
    return this.name + ' ' + this.age;
}
```

Giả sử ta có Workers kế thừa Person

```node
function Workers(name, age, total_hours) {
    // gọi lại constructor của lớp cha
    Person.call(this, name, age);
    this.total_hours = total_hours;
}
```

Trong trường hơp ta muốn ghi đè hàm **toUser** đồng thời sử dụng lại những cài đặt từ lớp cha thì phải làm như sau

```node
Workers.prototype.print = function() {
    // call lại hàm toUser
    let parent = Person.prototype.toUser.call(this);
    return parent + ' ' + this.total_hours
}

//kiểm tra kết quả
let dev = new Workers("Hai",23,5);
console.log(dev.print())
//Output: Hai 23 5
```

Vậy là chúng ta đã có thể mô phỏng phần nào tính kế thừa và tính đa hình trong oop, tuy nhiên các đặc điểm khác như static,... cũng chưa được thể hiện rõ ràng và cách viết này quá phức tạp, lộn xộn và thiếu tính trực quan, những người mới làm quen sẽ khó có thể tiếp cận được với js vì vậy từ phiên bản es6 đã thêm các cải tiến liên quan đến class

# ES6+ Classes

### Định nghĩa class cơ bản

Từ es6 trở đi, chúng ta đã có thể định nghĩa các đối tượng rõ ràng hơn thông qua từ khóa `Class` vd:

```node
class Course {
    constructor(name, price) {
      this.name = name;  
      this.price = price;
    }
    getName() {
     return this.name;
    }
}

let course_ta = new Course('Tieng anh', 1000)
console.log(course_ta.getName())
```

Ta có thể thấy việc định nghĩa 1 lớp đã trở nên dễ tiếp cận hơn thông qua các từ khóa class và constructor

### Kế thừa lớp (Inheritance)

Trong es6, việc kế thừa lớp trở nên rõ ràng và đơn giản hơn, nếu bạn đã từng làm việc qua với java thì việc học về kế thừa ở javascript sẽ vô cùng đơn giản, trở lại ví dụ lúc nãy ta sẽ thể hiện nó như sau:

```node
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    print() {
        return this.name + ' ' + this.age;
    }
}

class Workers extends Person {
    constructor(name, age, total_hours) {
        super(name, age);
        this.total_hours = total_hours;
    }

    print() {
        let parent = super.print();
        return parent + ' ' + this.total_hours;
    }
}

//thực hiện chạy thử
const worker = new Workers('Hai',23,8);
console.log(worker.print())
//output: Hai 23 8
```

Quan sát ví dụ trên ta có thể thấy việc thể hiện kế thừa thông qua từ khóa extends

```node
    class Workers extends Person
```

Ngoài ra ta còn được cung cấp thêm từ khóa `super` để gọi lại phương thức lớp cha 1 cách dễ dàng mà không cần phải bind object

### Tính đóng gói (Encapsulation)

#### Private class members

Các private class members như biến, method có thể khai báo dưới dạng private bằng cách thêm trước nó **dấu #** vd:

```node
class Worker {
    #info; //biến private
    constructor(info) {
        this.#info = info;
    }
    // hàm private
    #privateMethod() {
    }   
}

//chạy thử
const worker = new Worker('private_info');
worker.#privateMethod() //syntax error
```

***lưu ý ** : khi ta cố gắng truy cập vào các hàm hay biến này sẽ bị syntax error*

#### getter / setter

Để có thể truy cập vào các private field ta cần sử dụng hàm **getter setter**, vd cụ thể như sau:

```node
class Worker {
    #info; //biến private
    constructor(info) {
        this.#info = info;
    }
     get info() {
        return this.#info;
    }
    set info(info) {
        this.#info = info;
    }
}
//chay thu
const worker = new Workers('private_info');
console.log(worker.info) // private_info
worker.info = 'public_info'
console.log(worker.info) // public_info
```

### Static

Từ khóa static thường là đại diện cho lớp chứ không thuộc về một đối tượng, ta truy cập nó thông qua tên lớp chứ không tạo ra 1 đối tượng

#### static block

Nó được dùng để khởi tạo biến static ( **hỗ trợ từ nodejs 16.11 và chrome 94 - es2022** )

```node
class Student {
 static {
 }
}
```

#### static field

```node
class Student {
    static type = 'Hoc Sinh'
}

console.log(Student.type) // Hoc Sinh
```

# Kết bài

Tuy tính chất trừu tượng chưa được thể hiện nhưng classes cũng đã đem đến cho chúng ta nhiều cách viết mới, nó khiến cấu trúc code trở nên dễ đọc, dễ hiểu hơn, tuy vậy các bạn phải chú ý đến các phiên bản browser hỗ trợ để tránh gây lỗi không mong muốn, kiểm tra các phiên bản tại đây: [ phiên-bản ] ([https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#browser_compatibility](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#browser_compatibility))