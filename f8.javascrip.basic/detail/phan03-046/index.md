## VÒNG LẶP FOR

### Ví dụ:

Thực hiện in ra 100 dòng line.

```js
// Print Log 100 line
for (var i = 1; i <= 100; i++) {
  console.log(`Line ${i}`);
}
```

### Các cách chạy Loop for

#### 1. Cách 1:

```js
// Print Log 100 line
for (var i = 1; i <= 100; i++) {
  console.log(`Line ${i}`);
}
```

#### 2. Cách 2:

```js
// Print Log 100 line
var i = 1;
for (; i <= 100; i++) {
  console.log(`Line ${i}`);
}
```

#### 3. Cách 3:

```js
// Print Log 100 line
var i = 1;
for (; i <= 100; ) {
  console.log(`Line ${i}`);
  i++;
}
```

## Vòng lặp for dùng cho Array

- In các phần tử Element của một Array

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
