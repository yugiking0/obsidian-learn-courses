# BIẾN VÀ KHAI BÁO BIẾN

## Biến là gì?

Trong quá trình xây dựng website hoặc các ứng dụng với Javascript chúng ta sẽ cần phải làm việc với các dạng thông tin dữ liệu khác nhau. Ví dụ:

- Phần mềm kế toán - Chúng ta sẽ làm việc với những con số
- Website bán hàng - Làm việc với dữ liệu thông tin sản phẩm, đơn hàng và giỏ hàng
- Ứng dụng Chat - Dữ liệu là những đoạn chat, tin nhắn, thông tin người chat

Biến được sử dụng để lưu trữ các thông tin trên trong quá trình ứng dụng Javascript hoạt động.

## Khai báo biến

Để khai báo biến ta sẽ bắt đầu bằng từ khóa `var` (`var` là viết tắt của từ **_variable_** - nghĩa là biến). Khai báo biến có cú pháp như sau:

```js
var [dấu cách] [tên biến];
```

Theo cú pháp trên, mình sẽ định nghĩa một biến có tên là fullName với dự định để lưu tên đầy đủ của mình vào đó.

```js
var fullName;
```

Tiếp theo, ta có thể lưu thông tin vào biến fullName này:

```js
var fullName; // khai báo biến

fullName = 'Sơn Đặng'; // gán giá trị
```

Các bạn chú ý có dấu nháy đơn '' bao ngoài chữ Sơn Đặng. Đó là cách để thể hiện dữ liệu dạng chuỗi (văn bản) trong Javascript.

> Khi đoạn mã trên được chạy (thực thi) Javascript sẽ tạo biến với tên **_fullName_** và gán giá trị 'Sơn Đặng' cho biến này. Một vùng nhớ trong RAM của máy tính sẽ được sử dụng để phục vụ việc lưu trữ những giá trị của biến khi chương trình được thực thi.

Chuỗi 'Sơn Đặng' đã được lưu vào vùng nhớ tương ứng với biến fullName. Ta có thể truy cập tới chuỗi này qua tên biến:

```js
var fullName;

fullName = 'Sơn Đặng';

alert(fullName); // hiển thị giá trị của biến
```

Để đơn giản và ngắn gọn, ta có thể kết hợp việc khai báo biến và gán giá trị cho biến thành một dòng:

```js
var fullName = 'Sơn Đặng'; // khai báo và gán giá trị

alert(fullName);
```

Ta cũng có thể khai báo nhiều biến trong cùng một dòng cách nhau bởi dấu , như sau:

<!-- prettier-ignore -->
```js
var fullName = "Sơn Đặng",  age = 18,  workAt = "F8";
```

rông có vẻ ngắn gọn, tuy nhiên mình khuyên các bạn không nên dùng cách này. Khi cần khai báo nhiều biến hơn thì cách này trở nên rất khó đọc.

Ta nên khai báo biến trên mỗi dòng khác nhau để dễ đọc hơn (nên dùng cách này):

```js
var fullName = 'Sơn Đặng';
var age = 18;
var workAt = 'F8';
```

Một số cách khai báo biến trên nhiều dòng khác như sau:

<!-- prettier-ignore -->
```js
var fullName = "Sơn Đặng",
  age = 18,
  workAt = "F8";
```

Thậm chí có cả phong cách sau:

<!-- prettier-ignore -->
```js
var fullName = "Sơn Đặng"
  , age = 18,
  , workAt = "F8";
```

Về mặt kỹ thuật thì tất cả các cách đều tương tự nhau. Vì vậy dùng cách nào là tùy theo sở thích của bạn.

> Khi gán giá trị dạng số cho biến chúng ta không sử dụng dấu nháy đơn '' bao bọc bên ngoài. Như ví dụ trên thì age = 18 ta sẽ viết luôn là số 18 và không sử dụng dấu nháy.

## Quy tắc đặt tên

1. Tên biến có thể bao gồm chữ cái, số, dấu gạch dưới ( \_ ) và kí tự đô la ( $ )
2. Tên biến không thể bắt đầu bằng số, phải bắt đầu bằng một chữ cái hoặc dấu gạch dưới hoặc dấu đô la
3. Tên biến phân biệt chữ hoa và chữ thường. Vì vậy tenbien và TenBien là 2 biến khác nhau
4. Tên biến không được (không thể) đặt trùng với các từ khóa của Javascript

> Từ khóa là những từ được Javascript sử dụng để tạo nên những quy chuẩn về mặt chức năng và cú pháp trong Javascript. Ví dụ: Để khai báo một biến ta sẽ sử dụng từ khóa var. Vì vậy ta không thể đặt tên biến là “var”

Ví dụ cho tên biến hợp lệ

<!-- prettier-ignore -->
```js
var address; // tên biến sử dụng chữ cái

var first_name; // kết hợp chữ cái và gạch dưới

var $last_name; // dấu đô la, gạch dưới và chữ cái

var f8; // chữ cái và số, số đứng sau chữ cái
```

Ví dụ cho tên biến không hợp lệ

```js
var java-script; // bao gồm dấu gạch ngang

var 8f; // bắt đầu với chữ số

var var = 'Biến'; // sử dụng trùng từ khóa `var`
```

Các chữ cái không phải tiếng Latin vẫn có thể được sử dụng làm tên biến (không sử dụng cách này):

<!-- prettier-ignore -->
```js
var ດ້ານວິຊາການ = "..."; // tiếng Thái Lan
var ਤਕਨੀਕੀ = "..."; // tiếng Lào
```

> Trong thực tế chúng ta sẽ sử dụng tiếng Anh để đặt tên biến vì đó là quy ước chung Quốc Tế.

Chúc bạn hoàn thành bài học đầu tiên với điểm số đối đa!
