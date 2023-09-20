# Phương thức reduce có logic như thế nào?

Viết lại phương thức Reduce cho Array.

- Muốn viết lại Method cho Array thì dùng Phương Thức Nguyên Mẫu

  > Array.prototype.newMethod = function(argument1,argument2, ...) { console.log(argument)//Xem các đối số truyền vào}

- `Input`: Reduce sẽ bao gồm 2 đối số truyền vào là: `FunctionCallback` và `InitialValue`, với `InitialValue` đôi khi sẽ không được truyền vào.
- `Process`: Cần xử lý duyệt qua các phần tử của mảng để xử lý cho `FunctionCallback` với các đối số là `itemValue`, `index`, `originalArray` và cần trả về 1 giá trị Output.
- `Output`: Trả về 1 giá trị sau khi xử lý `FunctionCallback` với các đối số truyền vào: `InitialValue`, `itemValue`, `index`, `originalArray`
- Ta xem ví dụ mẫu sau:

```js
// Calc total of array
const arr = [1, 2, 3, 4, 5];

// Origin Array Reduce
var total = arr.reduce((acc, cur) => acc + cur); // 15
var total = arr.reduce((acc, cur) => acc + cur, 10); // 25

// New Array Reduce2
var total = arr.reduce2((acc, cur) => acc + cur); // 15
var total = arr.reduce2((acc, cur) => acc + cur, 10); // 25
```

- Viết lại cần lưu ý đến không truyền `InitialValue` và có truyền `InitialValue`

```js
// Tạo prototype Array
Array.prototype.reduce2 = function (functionCallback, initialValue) {
  var i = 0;
  if (argument < 2) {
    i = 1;
    initialValue = this[0];
  }
  for (; i < this.length; i++) {
    initialValue = functionCallback(initialValue, this[i], i, this); // Accumulator, currentValue, indexCurrent, originalArray
  }
  return initialValue; // Dùng initialValue như result để return.
};
```
