# String/Array includes() method

---

### 01. String includes() method

> String.includes(subString,index)
>
> - Index: vị trí ký tự bắt đầu tìm kiếm từ 0.

- Để kiểm tra trong chuỗi có chứa cụm từ cần tìm không.

```js
var myString = 'Cộng hòa xã hội chủ nghĩa Việt Nam';
console.log(myString.includes('xã hội')); // true
console.log(myString.includes('hưng')); // false
console.log(myString.includes('Cộng', 0)); // true
console.log(myString.includes('Cộng', 1)); // false
```

### 02. Array includes() method

- Để kiểm tra trong mảng có chứa phần tử cần tìm không.

```js
var myArr = ['Javascript', 'PHP', 'CSS'];

console.log(myArr.includes('PHP')); // true
console.log(myArr.includes('Javascript', 0)); // true
console.log(myArr.includes('Javascript', 1)); // false
// -2 + 3 =  1 // array.length is 3
console.log(myArr.includes('PHP', -2)); // true
```

---

### 03. Câu hỏi

- [x] includes trả về boolean khi hàm được thực thi!
- [ ] includes trả về 0 hoặc 1 tùy vào đối số có tồn tại trong chuỗi/mảng gốc hay không.
- [ ] includes là thuộc tính của string và array!
- [ ] includes có thể sử dụng cho cả number!
- [x] includes là hàm, là phương thức của string và array!
