# Khóa JavaScript Basic:

---

https://github.com/yugiking0/f8.javascrip.basic/tree/develope

- Xem [F8 phần nội dung Promise](https://yugiking0.github.io/f8.javascrip.basic/f8)

---

## Phần 01 : Giới thiệu

### Bài 001: Lời khuyên trước khóa học

- Xem [Lời khuyên trước khóa học](./detail/phan01-001/index.md)

### Bài 002: Cài đặt môi trường

- Cài trình duyệt Browser Chrome
- Code Editor `VS Code` + Extension `Liver Server`

---

## Phần 02 : Giới thiệu

### Bài 003: Sử dụng Javascript với HTML

- Xem [Sử dụng Javascript với HTML](./detail/phan02-003/index.md)

### Bài 004: Sử dụng Javascript với HTML

- Xem [Sử dụng Javascript với HTML](./detail/phan02-004/index.md)

### Bài 005: Biến và khai báo biến

- Xem [Biến và khai báo biến](./detail/phan02-005/index.md)

### Bài 006: Gán giá trị cho biến

- Xem [Gán giá trị cho biến](./detail/phan02-006/index.md)

### Bài 007: Học về biến qua video

- Xem [Học về biến qua video](./detail/phan02-007/index.md)

### Bài 008: Test tính cẩn thận, chỉn chu của bạn

- Xem [Test tính cẩn thận, chỉn chu của bạn](./detail/phan02-008/index.md)

### Bài 009: Cú pháp comments

- Xem [Cú pháp comments](./detail/phan02-009/index.md)

### Bài 010: Học comments qua video

- Xem [Học comments qua video](./detail/phan02-010/index.md)

### Bài 011: Một số hàm built-in

- Xem [Một số hàm built-in](./detail/phan02-011/index.md)

  - alert
  - console
  - confirm
  - prompt
  - setTimeOut
  - setInterval

<!-- prettier-ignore -->
### Bài 012: Làm quen với toán tử

- Xem [Làm quen với toán tử](./detail/phan02-012/index.md)

### Bài 013: Lưu ý khi làm bài tập

- Xem [Lưu ý khi làm bài tập](./detail/phan02-013/index.md)

### Bài 014: Toán tử số học

- Xem [Toán tử số học](./detail/phan02-014/index.md)

### Bài 015: Toán tử ++ -- với tiền tố & hậu tố

- Xem [Toán tử ++ -- với tiền tố & hậu tố](./detail/phan02-015/index.md)

### Bài 024: Truthy và Falsy

- Xem [Truthy và Falsy](./detail/phan02-024/index.md)

## Phần 03 : Kiến thức cốt lỗi (Phần 1)

### Bài 027: Làm việc với chuỗi

- Xem [Làm việc với chuỗi](./detail/phan03-027/index.md)

### Bài 031: Làm việc với mảng

- Xem [Làm việc với mảng](./detail/phan03-031/index.md)

### Bài 038: Object - Đối tượng.

- Xem [Object](./detail/phan03-038/index.md)

### Bài 039: Object Construction - Thiết kế đối tượng.

- Xem [Object](./detail/phan03-039/index.md)

### Bài 040: Object Prototype - Thuộc tính nguyên mẫu.

- Xem [Object Prototype](./detail/phan03-040/index.md)

### Bài 042: Lệnh rẽ nhánh If else

- Xem [Lệnh rẽ nhánh If else](./detail/phan03-042/index.md)

### Bài 043: Lệnh rẽ nhánh Switch

- Xem [Lệnh rẽ nhánh Switch](./detail/phan03-043/index.md)

<!-- prettier-ignore -->
```js
var date = 9;

switch (date) {
  case 2:
  case 3:
  case 4:
  case 5:
  case 6:
    console.log('Weekday');
    break;
  case 7:
  case 8:
    console.log('Weekend');
    break;
  default:
    console.log('Undefined day');
}
```

### Bài 044: Toán tử 3 ngôi (Ternary operator)

- Xem [Toán tử 3 ngôi (Ternary operator)](./detail/phan03-044/index.md)
  > [Điều kiện] ? [Biểu thức nếu đúng] : [Biểu thức nếu sai]

### Bài 045: Giới thiệu vòng lặp - Loop

- Xem [Giới thiệu vòng lặp - Loop](./detail/phan03-045/index.md)

  **Vòng lặp - Loop**

  - for : Vòng lặp với điều kiện đúng
  - for/in : Vòng lặp qua key của đối tượng (LOI-Loop Object In)
  - for/of : Vòng lặp qua value của đối tượng
  - while : Lặp khi điều kiện đúng.
  - do/while : Thực hiện 1 lần, sau đó lặp khi điều kiện đúng.

### Bài 046: Vòng lặp for()

- Xem [Vòng lặp for](./detail/phan03-046/index.md)

```js
// Print Log 100 line
for(var i = 1; i<= 100; i++>){
  console.log(`Line ${i}`);
}
```

```js
// prettier-ignore
var arr =[
  "Javascript",
  "CSS",
  "Html",
  "Java",
  "Python"
]
var arrLength = arr.length; // Tạo biến ngoài để tối ưu hơn
for (var i = 0; i < arrLength; i++) {
  console.log(arr[i]);
}
```

### Bài 049: Vòng lặp for/in

- Xem [Vòng lặp for/in](./detail/phan03-049/index.md)
  - for/in dùng cho _Object_
  - for/in dùng cho _Array_
  - for/in dùng cho _String_

```js
// Loop for/in => Object
var myInfo = {
  firstName: 'Dinh',
  lastName: 'Quang Duy',
  birthYear: 1985,
  address: 'Đà Nẵng',
  country: 'Việt Nam',
};

for (var key in myInfo) {
  console.log(key, myInfo[key]);
}
```

```js
// Loop for/in => Array
var arr = ['Javascript', 'CSS', 'Html', 'Java', 'Python'];

for (var key in arr) {
  console.log(arr[key]);
}
```

```js
// Loop for/in => String
var myString = 'Javascript';

// myString[0]// J
for (var i in myString) {
  console.log(myString[i]);
}
```

### Bài 050: Vòng lặp for/of

- Xem [Vòng lặp for/of](./detail/phan03-050/index.md)

### Bài 050: Vòng lặp for/of

- Xem [Vòng lặp for/of](./detail/phan03-050/index.md)

```js
// prettier-ignore
var languages = [
    'Javascript', 
    'CSS',
    'Html', 
    'Java'];

// 1.for/of
console.log('---1. for/of----');
for (var course of languages) {
  console.log(course);
}
// 2.for/in
console.log('---2. for/of----');
for (var index in languages) {
  console.log(index, languages[index]);
}
```

```js
var myString = 'Javascript';
for (var char of myString) {
  console.log(char);
} // J a v a s c r i p t
```

```js
var myInfo = {
  firstName: 'Dinh',
  lastName: 'Quang Duy',
  birthYear: 1985,
  address: 'Đà Nẵng',
  country: 'Việt Nam',
};
console.log(Object.keys(myInfo));
console.log(Object.values(myInfo));

for (var item of Object.keys(myInfo)) {
  console.log(item);
}

for (var item of Object.values(myInfo)) {
  console.log(item);
}
```

### Bài 051: Vòng lặp while

- Xem [Vòng lặp while](./detail/phan03-051/index.md)

```js
var i = 1;
while (i <= 100) {
  console.log('Line :', i);
  i++;
}
```

```js
var languages = ['Javascript', 'CSS', 'Html', 'Java'];
while (i < languages.length) {
  console.log(languages[i]);
  i++;
}
```

### Bài 052: Vòng lặp do/while

- Xem [Vòng lặp do/while](./detail/phan03-052/index.md)

Kiểm tra ví dụ:
Xem [Kiểm tra](./demo-index.html)

### Bài 053: Break & Continue trong vòng lặp

- Xem [Break & Continue trong vòng lặp](./detail/phan03-053/index.md)

<!-- ![Console](./images/001.png "Console") -->
<!-- <img src="./images/001.png" alt="JAVASCRIPT VỚI HTML" width="400px"/> -->

### Bài 054: Vòng lặp lồng nhau (Nested Loop)

- Xem [Vòng lặp lồng nhau - Nested Loop](./detail/phan03-054/index.md)

### Bài 055: Các bài toán về vòng lặp

- Xem [Các bài toán về vòng lặp](./detail/phan03-055/index.md)

### Bài 056: Làm việc với mảng dùng Methods (Phần 2)

- Xem [Làm việc với mảng dùng Methods](./detail/phan03-056/index.md)
- Array Methods:
  - forEach()
  - every()
  - some()
  - find()
  - filter()
  - map()
  - reduce()

### Bài 057: 15 Method Array

- Xem [15 Method Array](./detail/phan03-057/index.md)

### Bài 058: Array reduce() method

- Xem [Array reduce() method](./detail/phan03-058/index.md)

### Bài 059: Bài tập reduce method của Array.

- Xem [Bài tập reduce method của Array](./detail/phan03-059/index.md)

### Bài 060: Phương thức reduce có logic như thế nào?

- Xem [Phương thức reduce có logic như thế nào?](./detail/phan03-060/index.md)

### Bài 061: String/Array includes() method

- Xem [String/Array includes() method](./detail/phan03-061/index.md)

### Bài 062: Math Object

- Xem [Math Object](./detail/phan03-062/index.md)

### Bài 063: Callback

- Xem [Callback](./detail/phan03-063/index.md)

### Bài 064: Callback - Phần 2

- Xem [Callback - Phần 2](./detail/phan03-064/index.md)

### Bài 065: Empty elements of array

- Xem [Empty elements of array](./detail/phan03-065/index.md)

### Bài 066: My filter() method

- Xem [My filter() method](./detail/phan03-066/index.md)
- Tham khảo [Value Type và Reference Type](./detail/phan03-066/value-reference.md)
  <!-- ![Console](./images/001.png "Console") -->
  <!-- <img src="./images/001.png" alt="JAVASCRIPT VỚI HTML" width="400px"/> -->

### Bài 059: My some() method và My every()

- Xem [My some() method](./detail/phan03-067/index.md)

---

## Phần 04 : HTML DOM

### Bài 070: HTML DOM là gì?

- Xem [HTML DOM là gì?](./detail/phan04-070/index.md)

### Bài 071: HTML DOM vs DOM API

- Xem [HTML DOM vs DOM API](./detail/phan04-071/index.md)

### Bài 072: Document object

- Xem [Document object](./detail/phan04-072/index.md)

### Bài 073: Get element method - Phần 1

- Xem [Get element method - Phần 1](./detail/phan04-073/index.md)
- Xem lại [CSS-Selector](./detail/phan04-073/css-selector.md)
- [Bài tập](./detail/phan04-073/baitap.md)

### Bài 074: Get element method - Phần 2

- Xem [Get element method - Phần 2](./detail/phan04-074/index.md)

### Bài 075: Get element method - Phần 3

- Xem [Get element method - Phần 3](./detail/phan04-075/index.md)
- Nghiên cứu thêm về [Query Selector Element DOM](./detail/phan04-075/query-selector.md)

### Bài 076: Attribute node & Text node

- Xem [Attribute node & Text node](./detail/phan04-076/index.md)

### Bài 077: DOM attribute

- Xem [DOM attribute](./detail/phan04-077/index.md)

### Bài 078: InnerText vs textContent Property

- Xem [InnerText vs textContent Property](./detail/phan04-078/index.md)

### Bài 079: InnerHTML vs OuterHTML Property

- Xem [InnerHTML vs OuterHTML Property](./detail/phan04-079/index.md)

### Bài 080: Node Property

- Xem [Node Property](./detail/phan04-080/index.md)

### Bài 081: DOM CSS

- Xem [DOM CSS](./detail/phan04-081/index.md)

### Bài 082: ClassList Property

- Xem [ClassList Property](./detail/phan04-082/index.md)

### Bài 083: DOM events

- Xem [DOM events](./detail/phan04-083/index.md)

### Bài 084: DOM events example

- Xem [DOM events](./detail/phan04-084/index.md)

### Bài 085: PreventDefault and StopPropagation

- Xem [PreventDefault and StopPropagation](./detail/phan04-085/index.md)

### Bài 086: Event listener

- Xem [Event listener](./detail/phan04-086/index.md)

<!-- ![Console](./images/001.png "Console") -->
<!-- <img src="./images/001.png" alt="JAVASCRIPT VỚI HTML" width="400px"/> -->

---

## Phần 05 : Asynchronous Promise

### Bài 087: JSON là gì?

- Xem [JSON](./detail/phan05-087/index.md)

### Bài 088: Synchronous - Asynchronous (Đồng bộ và Bất đồng bộ)

- Xem mục [Đồng bộ - Bất đồng bộ](./detail/phan05-088/index1.md)
- Xem mục [Synchronous - Asynchronous](./detail/phan05-088/index.md)
- Xem mục [Phần 1](./detail/phan05-088/phan1.md)
- Xem mục [Phần 2](./detail/phan05-088/phan2.md)

### Bài 089: Sự ra đời của Pain Promise (Niềm đau - Nguyên nhân cần thiết)

- Xem mục [Niềm đau và sự cần thiết của Promise](./detail/phan05-089/index.md)
- Xem [Callback hell](./detail/phan05-089/index2.md)
- Xem [Callback hell 2](./detail/phan05-089/resolve-callback-hell.md)

### Bài 090: Cấu trúc và cách sử dụng Promise

- Xem mục [Promise là gì](./detail/phan05-090/index.md)

### Bài 091: Tính chất chuỗi trong Promise(Promise Chain)

- Xem mục [Promise Chain](./detail/phan05-091/index.md)

### Bài 092: Promise methods (resolve, reject, all)

- Xem mục [Promise methods](./detail/phan05-092/index.md)

### Bài 093: Promise example - Ví dụ sử dụng Promise

- Xem mục [Promise example](./detail/phan05-093/index.md)

### Bài 093+: Nổi đau của Promise - Promise Pain

- Xem mục [Promise Pain](./detail/phan05-093/index.md)

### Bài 094: Fetch dữ liệu

- Xem mục [Fetch dữ liệu](./detail/phan05-094/index.md)

<!-- ![Console](./images/001.png "Console") -->
<!-- <img src="./images/001.png" alt="JAVASCRIPT VỚI HTML" width="400px"/> -->

### Bài 097.1: Promise Pain

- Xem mục [Asyn/Await](./detail/phan05-098/index.md)
- Xem mục [Promise và Asyn/Await](./detail/phan05-098/index2.md)

### Bài 097.2: Xử lý Asyn/Await

- Xem mục [Asyn/Await](./detail/phan05-099/index.md)

### Bài 097.3: Xử lý Axios

- Xem mục [Xử lý Axios](./detail/phan05-100/index.md)

### Bài 093: Promise example - Ví dụ sử dụng Promise

- Xem mục [Promise example](./detail/phan05-093/index.md)

### Bài 094: Fetch dữ liệu

- Xem mục [Fetch dữ liệu](./detail/phan05-094/index.md)

### Bài 095: JSON Server

- Xem mục [JSON Server](./detail/phan05-095/index.md)

### Bài 096: Sử dụng Postman làm việc với REST API

- Xem mục [Sử dụng Postman](./detail/phan05-096/index.md)

### Bài 097: Thêm/sửa/xóa khóa học với Fetch và REST API

- Xem mục [Thêm/sửa/xóa khóa học với Fetch và REST API](./detail/phan05-097/index.md)

---

## Phần 06 : ECMAScript 6+

### Bài 099: ECMAScript 6+ là gì?

- Xem mục [ECMAScript 6+](./detail/phan06-099/index.md)

### Bài 100: Let & Const

- Xem mục [Let & Const](./detail/phan06-100/index.md)


### Bài 101: Template literals

- Xem mục [Template literals](./detail/phan06-101/index.md)


### Bài 102: Arrow function

- Xem mục [Arrow function](./detail/phan06-102/index.md)


### Bài 103: Classes

- Xem mục [Classes](./detail/phan06-103/index.md)

### Bài 104: Default parameter values

- Xem mục [Default parameter values](./detail/phan06-104/index.md)

### Bài 105: Enhanced object literals

- Xem mục [Enhanced object literals](./detail/phan06-105/index.md)

### Bài 106: Destructuring, Rest

- Xem mục [Destructuring, Rest](./detail/phan06-106/index.md)

### Bài 107: Spread

- Xem mục [Spread](./detail/phan06-107/index.md)

### Bài 108: Tagged template literals

- Xem mục [Tagged template literals](./detail/phan06-108/index.md)

### Bài 109: Modules

- Xem mục [Modules](./detail/phan06-109/index.md)