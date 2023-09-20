# Value Type and Reference Type in Javascript

## Mở bài

Xin chào các bạn. Hôm nay mình sẽ bàn về hai khái niệm trong javascript mà nó gây nhiều rắc rối khi code nếu không hiểu rỏ về nó, xin giới thiệu đó là Value vs. Reference. Mình xin đưa ra một bài test nhỏ:

```js
var personObj1 = {
  name: 'Alex',
  age: 30,
};

var person = personObj1;
person.age = 25;

person = {
  name: 'John',
  age: 50,
};

var personObj2 = person;

console.log(personObj1); //(1)
console.log(personObj2); //(2)
```

Nếu các bạn biết được kết quả của dòng lệnh (1), (2) và lý do vì sao thì xin chúc mừng bạn. Còn nếu bạn không biết được kết quả in ra như thế nào thì mình cũng xin chúc mừng bạn. Sau khi đọc xong chia sẽ này của mình bạn sẽ có được một hiểu biết mới cũng khá là hay ho đấy.

## Thân bài

Trong javascript có năm kiểu dữ liệu được gọi là **_`primitive types`_** đó là: `Boolean`, `null`, `undefined`, `String`, và `Number`. Trong javascript cũng có ba kiểu dữ liệu được gọi là reference types đó là: Array, Function, và Object. Vì sao có sự phân chia đó qua các vị dụ ở dưới các bạn sẽ hiểu.

### Primitives

Khi một giá trị là một kiểu dữ liệu thuộc dạng `primitive` được gán cho một biến tức là lúc này biến đó chứa giá trị đó. Ví dụ:

```js
var x = 10;
var y = 'abc';
var z = null;
```

Lúc này biến x chứa 10, biến y chứa string 'abc'. Ảnh bên dưới minh họa các biến và giá trị tương ứng khi lưu trong bộ nhớ. Khi ta gán những biến này cho những biến khác bằng dấu '=', tức là ta copy giá trị của biến đó cho biến mới. Ví dụ:

```js
var x = 10;
var y = 'abc';

var a = x;
var b = y;

console.log(x, y, a, b); // -> 10, 'abc', 10, 'abc'
```

Ảnh bên dưới minh họa các biến và giá trị tương ứng sau khi gán trong bộ nhớ.Khi ta thay đổi giá trị một biến sẽ không làm thay đổi biến khác. Tức là giữa hai biến không còn quan hệ vợi nhau nữa.

```js
var x = 10;
var y = 'abc';

var a = x;
var b = y;

a = 5;
b = 'def';

console.log(x, y, a, b); // -> 10, 'abc', 5, 'def'
```

### Reference

Khi một biến được gán một giá trị thuộc kiểu dữ liệu thuộc nhóm Reference thì biến đó chỉ lưu địa chỉ của giá trị đó trên bộ nhớ. Biến đó không lưu giá trị được gán. Ví dụ: Khi chúng ta gán và sự dụng một biến được gắn kiểu dữ liệu thuộc Reference chúng ta sẽ viết như sau:

```js
var arr = []; //(1)
arr.push(1); //(2)
```

Mô phỏng dòng lệnh 1 trên bộ nhớ như ảnh sau: các bạn thấy đó. Biến arr chỉ lưu điạ chỉ của array được gán vào thôi. không phải lưu giá trị. Có nghĩa là khi bạn sử dụng biến này thì biến javascript sẽ tới địa chỉ của biến đó lưu và lấy giá trị có ở địa chỉ đó trả về cho bạn. Ảnh sau mô phỏng dòng lệnh 2 trên bộ nhớ. Ở dòng lệnh thứ hai thì javascript tìm tới địa chỉ ô nhớ và thêm một phần tử vào ô nhớ đó. Đến đây các bạn đã thấy sự khác nhau giữa Reference và Primitives chưa?

### Gắn một biến dạng Reference vào một biến mới

Khi một biến dạng Reference được gán cho một biến mới, thì biến mới sẽ chứa địa chỉ chứa trong biến trước. Có nghĩa là biến mới cũng tham chiếu tới cùng một ô nhớ như biết trước đó. Ví dụ:

```js
var reference = [1];
var refCopy = reference;
```

Hai dòng code trên được minh họa như sau:Tiếp tục câu lệnh sau:

```js
reference.push(2);
console.log(reference, refCopy);
// -> [1, 2], [1, 2]
```

Bạn thấy điều gì đó khác lạ chưa, Hai biến reference và refCopy cùng một array. Hình ảnh sau giải thích điều này.

### Dạng object

Ví dụ trên mình nói về dạng array. Bây giờ nói tới object nhé. Xét đoạn code sau:

```js
var obj = { first: 'reference' };
```

Đoạn code sau được minh họa như sau:Vậy còn điều gì xảy ra với đoạn code dưới đây:

```js
var obj = { first: 'reference' };
obj = { second: 'ref2' };
```

đoạn code trên được minh họa bằng hình sau:Như thấy trong hình biến obj sẽ được chứa địa chỉ khác khi gán cho nó một địa object khác.

## Kết bài

Mình tin là khi các bạn đọc tới đây thì các bạn biết được kết quả của ví dụ trong phần mở bài rồi nhỉ. Reference còn cái function nữa mới các bạn tự tìm hiểu ở đây nhé.
