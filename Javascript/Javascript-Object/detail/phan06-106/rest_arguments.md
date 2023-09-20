# Rest và Arguments

---

## 1. Parameter (Tham số)

- Đây là những gì chúng ta gọi khi định nghĩa một hàm.
- `Parameter` sẽ đại diện cho một giá trị mà hàm của bạn sẽ nhận được khi được gọi.
- Ví dụ sau khai báo hàm có 2 tham số là `x` và `y`:

```js
int Add(int x, int y)
{
    return (x+y);
}
```

## 2. Rest Parameters 
- Rest Parameters là tập hợp các tham số còn lại.
- Hàm có thể gọi với số lượng tham số tùy ý

>ví dụ như

```js
 function sum(a, b) {
  return a + b;
}

console.log( sum(1, 2, 3, 4, 5) ); // 3
=> 3
```

- Khi ta gọi `sum(1, 2, 3, 4, 5)` ta truyền vào 5 tham số tuy nhiên hàm sum định nghĩa với 2 tham số vẫn chẳng có bất cứ lỗi gì xảy ra. Bởi vì, Javascript cho phép bạn truyền nhiều hơn hoặc ít hơn số lượng tham số khai báo ở hàm. Và kết quả ta nhận được là 3, hàm sum chỉ tính tổng của 2 tham số đầu tiên.

- Sửa lại hàm sum để có thể tính toán đúng cho các trường hợp số lượng tham số khác nhau ta sử dụng rest parameters với phần định nghĩa tham số bắt đầu với 3 dấu chấm ... có nghĩa tập hợp các tham số còn lại vào một mảng.

> Cụ thể ta sẽ cài đặt như sau

```js
function sum(...args) {
  // args is the name for the array
  let sum = 0;

  args.forEach(arg => (sum += arg));

  return sum;
}

console.log(sum(1)); // 1
console.log(sum(1, 2)); // 3
console.log(sum(1, 2, 3)); // 6
```

- Hơn nữa chúng ta cũng có thể dùng các tham số khác cùng với `rest parameters`.
- Ví dụ ta có 2 tham số đầu tiên và tham số tiếp theo là một `rest parameters`

```js
function addList(list, ...args) {
  args.forEach(arg => list.push(arg));
  return list;
}

addList([1], 2, 3); // [1, 2, 3]
```

- Có một điều chú ý là rest parameters phải đặt ở cuối trong danh sách các parameters của hàm Ví dụ trường hợp sau sẽ báo lỗi

```js
function f(arg1, ...rest, arg2) { // arg2 after ...rest ?!
  // error
}
```

## 3. Argument variable (Đối số)

- Đây là đại diện cho giá trị truyền cho `parameter` khi chúng ta thực hiện lời gọi hàm.
- Mỗi `argument` sẽ tương ứng với một `parameter` khi khai báo.
- Ví dụ sau thực hiện lời gọi hàm Add bên trên và truyền vào hai đối số là `3` và `5`:

```js
int Sum = Add(3, 5);
```

## 4. So sánh Arguments và Rest Parameters

- Về cơ bản `arguments` cũng có thể nói là khá giống với `Rest parameters`.
- `Arguments` đơn giản là danh sách các tham số truyền vào khi gọi hàm.
- `Rest parameters` thì cao cấp hơn một chút nó chỉ rõ các tham số là tên là gì và cũng dễ đọc dễ hiểu hơn.

```js
function sum() {
  let total = 0;
  for (let argument of arguments) {
    total += argument;
  }
  return total;
}
sum(1, 2, 3); // 6
```

- `arguments` là một đối tượng kiểu `Arguments` không phải `Array` như `Rest parameters` nên bạn không thể dùng `forEach` được.

- `arguments` thường được sử dụng trước khi có `rest parameters` hiện tại `arguments` vẫn được support chúng ta vẫn có thể dùng bình thường tuy nhiên theo khuyến cáo thì nên chuyển sang `rest parameters` sẽ tốt hơn.

- Một điểm nữa là `arrow function` cũng sẽ ko dùng được `arguments` của chính nó

```js
let showArg = () => alert(arguments[0]);
showArg(1); ///wrong
```
---