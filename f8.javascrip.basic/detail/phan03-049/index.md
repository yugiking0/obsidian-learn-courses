# VÒNG LẶP FOR/IN

## 1. Dùng cho Object

```js
// For/in
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

![Object](./images/001.png 'Object')

## 2. Dùng cho Array

- Giống với cách đã dùng trước đây với for()

```js
var arr = ['Javascript', 'CSS', 'Html', 'Java', 'Python'];
var arrLength = arr.length; // Tạo biến ngoài để tối ưu hơn
for (var i = 0; i < arrLength; i++) {
  console.log(arr[i]);
}
```

- Vì Array cũng là 1 Object nên có thể áp dụng cho Array như sau:

```js
// Loop for/in => Array
var arr = ['Javascript', 'CSS', 'Html', 'Java', 'Python'];

for (var key in arr) {
  console.log(arr[key]);
}

// Giống cách dùng for()
for (var i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

![Array](./images/002.png 'Array')

## 3. Dùng cho chuỗi String

```js
var myString = 'Javascript';

// myString[0]// J
for (var i in myString) {
  console.log(myString[i]);
}
```

![String](./images/003.png 'String')

---
