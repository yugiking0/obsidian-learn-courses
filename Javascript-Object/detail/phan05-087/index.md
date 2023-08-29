# JSON là gì?

---


  - [JSON là gì?](#1-json-là-gì)
  - [Các kiểu dữ liệu của JSON](#2-các-kiểu-dữ-liệu-của-json)
    - [Kiểu Số - Number](#21-kiểu-số-number)
    - [Kiểu Chuỗi - String](#22-kiểu-chuỗi-string)
    - [Kiểu Boolean](#23-kiểu-boolean)
    - [Kiểu null](#24-kiểu-null)
    - [Kiểu NaN](#25-kiểu-nan)
    - [Kiểu Mảng - Array](#26-kiểu-mảng-array)
    - [Kiểu Đối tượng - Object](#27-kiểu-đối-tượng-object)
  - [Chuyển đổi Javascript sang JSON và ngược lại](#3-chuyển-đổi-javascript-sang-json-và-ngược-lại)
    - [JSON.parse](#31-jsonparse-chuyển-từ-kiểu-json-về-javascript-types)
    - [JSON.stringify](#32-jsonstringify-chuyển-từ-kiểu-javascript-types-về-json)
  - [DevTool Website load JSON](#4-kiểm-tra-website-load-json)


---

## 1. JSON là gì?

- JSON là một kiểu định dạng dữ liệu kiểu chuỗi (JavaScript Object Notation) theo chuẩn truyền tải dữ liệu được phát kiến từ ngôn ngữ JavaScript, và được sử dụng trên nhiều ngôn ngữ dữ liệu theo tiêu chuẩn.

## 2. Các kiểu dữ liệu của JSON

- Từ các kiểu dữ liệu của ngôn ngữ khác có thể chuyển sang định dạng kiểu dữ liệu chuỗi JSON, và từ định dạng chuỗi JSON có thể chuyển sang các định dạng:
  - Kiểu Số - Number
  - Kiểu Chuỗi - String
  - Boolean
  - null
  - Kiểu Mảng - Array
  - Kiểu Đối tượng - Object
- Sử dụng 2 phương thức mã hóa từ kiểu dữ liệu sang chuỗi JSON, và giải mã kiểu dữ liệu chuỗi JSON sang kiểu dữ liệu của ngôn ngữ cần sử dụng. JSON hỗ trợ 2 phương pháp:
  - Stringify : Chuyển sang định dạng JSON
  - Parse : Chuyển từ định dạng JSON lại

### 2.1 Kiểu Số - Number

- Kiểu định dạng JavaScript

```js
// Kiểu Javascript
var jsVar = 1;
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu Javascript:  1 number
```

- Kiểu định dạng JSON

```js
// Kiểu JSON
var jsonVar = '1';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Kiểu JSON:  1 string
```

- Chuyển đổi từ định dạng JavaScript sang JSON

```js
// Kiểu Javascript
var jsVar = 1;
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);
```

- Chuyển đổi từ định dạng JSON sang javascript

```js
// Kiểu JSON
var jsonVar = '1';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);
```

- Xem đầy đủ:

```js
// Kiểu Javascript
var jsVar = 1;
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu JSON
var jsonVar = '1';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);
```

![Number](./images/001.png 'Number')

- Kiểu Số - Number
- Kiểu Chuỗi - String
- Boolean
- null
- Kiểu Mảng - Array
- Kiểu Đối tượng - Object

### 2.2 Kiểu Chuỗi - String

```js
// Kiểu Javascript
var jsVar = '1';
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu JSON
var jsonVar = '"1"';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);
```

![String](./images/002.png 'String')

> Lưu ý: Để ngăn cách các kiểu dữ liệu chuỗi trong JSON phải dùng dấu nháy kép `"`

### 2.3 Kiểu Boolean

```js
// Kiểu Javascript
var jsVar = true;
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu JSON
var jsonVar = 'true';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);
```

![Boolean](./images/003.png 'Boolean')

### 2.4 Kiểu null

```js
// Kiểu Javascript
var jsVar = null;
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu JSON
var jsonVar = 'null';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);
```

![null](./images/004.png 'null')

### 2.5 Kiểu NaN

```js
// Kiểu Javascript
var jsVar = NaN;
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu JSON
var jsonVar = '"NaN"';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);

// JSON.parse('NaN'); // SyntaxError
// VM717:1 Uncaught SyntaxError: Unexpected token N in JSON at position 0 at JSON.parse
```

![NaN](./images/006.png 'NaN')

### 2.6 Kiểu Mảng - Array

```js
// Kiểu Javascript
var jsVar = [1, 2, 3, 'Duy'];
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu JSON
var jsonVar = '[1,2,3,"Duy"]';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);
```

![Array](./images/005.png 'Array')

- Lưu ý: Để ngăn cách các kiểu dữ liệu chuỗi trong JSON phải dùng dấu nháy kép `"`

```js
// Kiểu JSON
var jsonVar = '["PHP","CSS","Javascript"]';
```

### 2.7 Kiểu Đối tượng - Object

```js
// Kiểu Javascript
var jsVar = {
  name: 'Quang Duy',
  city: 'Da Nang',
  age: 20,
};
console.log('Kiểu Javascript: ', jsVar, typeof jsVar);

// Kiểu JSON
var jsonVar = '{"name":"Quang Duy", "city":"Da Nang", "age":20}';
console.log('Kiểu JSON: ', jsonVar, typeof jsonVar);

// Chuyển từ kiểu Javascript sang kiểu JSON
var json = JSON.stringify(jsVar);
console.log('Chuyển sang JSON: ', json, typeof json);

// Chuyển từ kiểu JSON sang kiểu Javascript
var js = JSON.parse(jsonVar);
console.log('Chuyển lại Javascript: ', js, typeof js);
```

![Object](./images/007.png 'Object')

- Trong JSON khóa `Key` phải có dấu nháy kép

```js
var jsonVar = '{"name":"Quang Duy", "city":"Da Nang", "age":20}';
```

## 3. Chuyển đổi Javascript sang JSON và ngược lại

- Để chuyển đổi các kiểu dữ liệu từ JavaScript sang JSON hoặc từ kiểu dữ liệu dạng chuyển của JSON sang lại kiểu dữ liệu của JavaScript ta sử dụng 2 phương thức:
  - **Stringify** : `JSON.stringify` - Javascript Types -> JSON
  - **Parse** : `JSON.parse` - JSON string -> Javascript Types

### 3.1 JSON.parse chuyển từ kiểu JSON về Javascript Types

- Chuyển kiểu Số - Number

```js
var json = '1';
console.log(typeof JSON.parse(json));

// Number
```

- Chuyển kiểu Chuỗi - String

```js
var json = '"Quang Duy"';
console.log(typeof JSON.parse(json));

// string
```

- Chuyển kiểu Boolean

```js
var json = '{"name":"Quang Duy", "city":"Da Nang", "age":20}';
console.log(typeof JSON.parse(json));
```

- Chuyển kiểu null

```js
var json = 'null';
console.log(typeof JSON.parse(json));

// object
```

- Chuyển kiểu NaN

```js
var json = '"NaN"';
console.log(typeof JSON.parse(json));
// string

var json = 'NaN';
console.log(typeof JSON.parse(json));
// Uncaught SyntaxError: Unexpected token N in JSON at position 0 at JSON.parse (<anonymous>)
```

- Chuyển kiểu Mảng - Array

```js
var json = '["PHP","CSS","Javascript"]';
console.log(typeof JSON.parse(json));

// object
```

- Chuyển kiểu Đối tượng - Object

```js
var json = '{"name":"Quang Duy", "age": 20}';
console.log(typeof JSON.parse(json));

// object
```

### 3.2 JSON.stringify chuyển từ kiểu Javascript Types về JSON

- Chuyển kiểu Số - Number
- Chuyển kiểu Chuỗi - String
- Chuyển kiểu Boolean
- Chuyển kiểu null
- Chuyển kiểu NaN
- Chuyển kiểu Mảng - Array

```js
var js = [1, 2, 3, 'a', 'b', 'c', '1', '2', '3'];
console.log(JSON.stringify(js));
```

- Chuyển kiểu Đối tượng - Object

```js
var js = {
  name: 'Quang Duy',
  age: 20,
};
console.log(JSON.stringify(js));

// {"name":"Quang Duy","age":20}
```

- Lưu ý: Method của Object khi chuyển qua JSON sẽ bị mất

```js
var cat = {
  name: 'Tom',
  age: 3,
  sound: 'bark: "Gau Gau"',
  color: function () {
    return 'Orange';
  },
};
console.log('Color: ', cat.color());
console.log(JSON.stringify(cat));

// Color:  Orange
// {"name":"Tom","age":3,"sound":"bark: \"Gau Gau\""}
```

## 4. Kiểm tra Website load JSON

- Dùng DevTool
- Tab Network (1)
- Chọn tiếp Tab Detail XHR (2)
- Ở danh sách name (3) chọn một dòng API load dữ liệu
- Bên phải chọn Tab Response (4) để xem thể hiện dữ liệu string JSON lấy về từ API.

![DevTool](./images/008.png 'DevTool')

![DevTool](./images/009.png 'DevTool')
![DevTool](./images/010.png 'DevTool')

---
