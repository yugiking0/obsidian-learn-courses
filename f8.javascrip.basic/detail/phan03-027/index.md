# LÀM VIỆC VỚI CHUỖI

---

```js
var myString = 'Hoc JS tai F8!';
```

> Keyword: Javascript string methods

    1. Length

```js
console.log(myString.length); // 14
```

    2. Find index

```js
console.log(myString.indexOf('JS'));
console.log(myString.indexOf('JS'), 2); //thêm Index để lấy "JS" thứ 2

console.log(myString.search('JS')); // Không có thêm tham số index
```

    3. Cut string

```js
console.log(myString.slice(2, 3));
```

    4. Replace

```js
console.log(myString.replace('JS', 'Javascript')); // 'Hoc Javascript tai F8'
```

    5. Convert to upper case

```js
console.log(myString.toUpperCase()); // 'HOC JS TAI F8'
```

    6. Convert to lower case

```js
console.log(myString.toLowerCase()); // 'hoc js tai f8'
```

    7. Trim

```js
console.log('  Hoc JS tai F8  '.trim()); // 'Hoc JS tai F8!'
console.log('  Hoc JS tai F8  '.length); // 17
console.log('  Hoc JS tai F8  '.trim().length); // 13
```

    8. Split

```js
var languages = 'Javascript, PHP, Ruby';
console.log(languages.split(', ')); // ['Javascript', 'PHP', 'Ruby']
```

    9. Get a character by index

```js
console.log(myString.charAt(0)); // "H"
console.log(myString.charAt(2)); // "c"

console.log(myString.charAt(15)); // undefine
console.log(typeof myString.charAt(15)); // undefine
```

---

## 1. Length

- Trả về độ dài của chuỗi.

```js
var myString = 'Hoc JS tai F8!';
console.log(myString.length); // 14
```

---

## 2. FindIndex

- Trả về độ dài của chuỗi.

### indexOf

```js
var myString = 'Hoc JS, ở đây JS là Javascript, JS tai F8!';

// Vị trí JS đầu tiên trong chuỗi
console.log(myString.indexOf('JS')); // 4

// Vị trí CSS đầu tiên trong chuỗi
console.log(myString.indexOf('CSS')); // -1 -> Không có

// Vị trí JS thứ 2 trong chuỗi
/**
 * console.log(myString.indexOf('JS', loc));
 * loc: vị trí bắt đầu tìm của chuỗi, 8 - vị trí sau JS đầu tiên
 * Vậy muốn tìm vị trí JS thứ n??
 * thì cần tìm từ vị trí JS (n-1) cộng thêm độ dài 2 ? Cách khác???
 */
console.log(myString.indexOf('JS', 6)); // 14
// hoặc viết:
console.log(myString.indexOf('JS', myString.indexOf('JS') + 2)); // 14

// Vị trí JS cuối cùng của chuỗi : lastIndexOf()
console.log(myString.lastIndexOf('JS')); // 32
```

Có thể tìm hiểu thêm [ở đây](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)

### search

```js
var myString = 'Hoc JS tai F8!';
console.log(myString.search('JS')); // 4
console.log(myString.search('JS', 8)); // 4 : Không hiểu loc index như indexOf
```

- `String.prototype.search()` chức năng gần như `String.prototype.indexOf()`, nhưng không truyền thêm được vị trí bắt đầu tìm.
- `String.prototype.search()` hỗ trợ xử lý tìm theo `regular expression` mà `String.prototype.indexOf()` không hỗ trợ.

Có thể tìm hiểu thêm [ở đây](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/search)

---

## 3. Cut string

- Cắt chuỗi.

```js
var myString = 'Hoc JS tai F8!';

// Cắt chuỗi JS ra
console.log(myString.slice(4, 6)); // JS
```

SYNTAX : .slice(start, end)

- Truyền vào 2 tham số: vị trí đầu tiên và vị trí cuối.

```js
var myString = 'Hoc JS tai F8!';

// Cắt chuỗi "JS tai F8!"
console.log(myString.slice(4)); // "JS tai F8!" : không truyền endLocation (tham số thứ 2)

// Cắt cả chuỗi
console.log(myString.slice()); //  'Hoc JS tai F8!'
console.log(myString.slice(0)); //  'Hoc JS tai F8!'
console.log(myString.slice('')); //  'Hoc JS tai F8!'

// Cắt ngược từ sau ra trước, cắt "F8"
console.log(myString.slice(-3, -1)); // F8 : Dùng số âm
```

Có thể tìm hiểu thêm [ở đây](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

---

## 4. Replace

- Thay thế cụm từ trong chuỗi

```js
var myString = 'Hoc JS tai F8!';
var myString2 = 'Hoc JS JS tai F8!';

// Thay cụm từ JS bằng Javascript
console.log(myString.replace('JS', 'Javascript')); // 'Hoc Javascript tai F8!'

// Nhưng chỉ thay thế được JS đầu tiên
console.log(myString2.replace('JS', 'Javascript')); // 'Hoc Javascript JS tai F8!'

// Muốn thay thế tất cả phải dùng `regular expression`(Tìm hiểu sau)
console.log(myString2.replace(/JS/g, 'Javascript')); // 'Hoc Javascript Javascript tai F8!'
```

- Tìm hiểu thêm về `regular expression` - Biểu thức chính qui

Có thể tìm hiểu thêm [ở đây](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

---

## 5. Convert to upper case

```js
var myString = 'Hoc JS tai F8!';
console.log(myString.toUpperCase()); // 'HOC JS TAI F8!'
```

---

## 6. Convert to lower case

```js
var myString = 'Hoc JS tai F8!';
console.log(myString.toLowerCase()); // 'hoc js tai f8!'
```

---

## 7. Trim

- Xử lý dữ liệu người dùng, bỏ khoảng trắng thừa đầu hay cuối chuỗi.

```js
var myString = '   Hoc JS tai F8!   ';

console.log(myString.trim()); // 'Hoc JS tai F8!'
console.log(myString.length); // 20
console.log(myString.trim().length); // 14
```

---

## 8. Split

- Cắt 1 chuỗi thành Array
- Cần truyền vào ký tự, hay cụm từ để ngăn cách tách ra.

```js
var languages = 'Javascript, PHP, Ruby';
console.log(languages.split(', ')); // ['Javascript', 'PHP', 'Ruby']
console.log(languages.split(',')); // ["Javascript", " PHP", " Ruby"]
console.log(languages.split('a')); // ["J", "v", "script, PHP, Ruby"]

// Tách chuỗi thành mảng bao gồm các ký tự
var language = 'Javascript';
console.log(language.split('')); // ["J", "a", "v", "a", "s", "c", "r", "i", "p", "t"]
```

---

## 9. Split

### charAt

- Lấy ký tự trong chuỗi từ vị trí cho trước

```js
var myString = 'Hoc JS tai F8!';
console.log(myString.length); // 14

console.log(myString.charAt(0)); // "H"
console.log(myString.charAt(2)); // "c"

console.log(myString.charAt(15)); // '' chuỗi rỗng
console.log(typeof myString.charAt(15)); // string
```

### [index]

```js
var myString = 'Hoc JS tai F8!';
console.log(myString.length); // 14

console.log(myString[0]); // "H"
console.log(myString[2]); // "c"

console.log(myString[15]); // undefined
console.log(typeof myString[15]); // undefined
```

---

## Bài tập
