# Lưu ý khi làm bài tập

Anh em hãy đọc kỹ phần này để học hiệu quả hơn trong những bài học tiếp theo nhé!

Từ bài test này trở đi các bạn sẽ thường thấy cú pháp khai báo hàm dạng như function run(...). Đây là một hàm để hệ thống có thể đánh giá chất lượng bài làm của bạn, các bạn chưa cần quan tâm tới cú pháp “function” này vì chúng ta sẽ được học nó trong tương lai.

---

## Tập trung vào yêu cầu

Hãy tập trung vào việc giải quyết yêu cầu đưa ra trong đề bài và viết code của bạn tại vị trí dấu 3 chấm (…)

Ví dụ:

```js
function run(a, b) { // <-- Nội dung chưa cần quan tâm
    return c = ... // <-- Xoá dấu ... và viết code của bạn
}
```

Trường hợp trong đề bài mà có nói “Cho trước biến x, y, z…” thì đây là những biến đã cho trước (đã có sẵn, đã khai báo rồi). Các bạn vui lòng không khai báo lại các biến đã cho trước vì điều này sẽ làm bài tập của bạn không vượt qua được toàn bộ các test cases.

Ví dụ: Giả sử đề bài nói “Cho trước biến a, b là 2 số bất kỳ” thì code trong phần làm bài sẽ thường như sau:

Ví dụ:

<!-- prettier-ignore -->
```js
function run(a, b) { // <-- Đây là biến a & b đã cho trước
    return c = a + b // <-- Các bạn chỉ cần sử dụng biến a & b này
}
```

---

## Một số ví dụ làm sai

Dưới đây là một vài ví dụ khiến cho bài tập của bạn không vượt qua được các test cases của hệ thống F8.

#### Ví dụ 1: Khai báo lại biến đã cho trước

Điều này làm cho bài tập của bạn không vượt qua được toàn bộ các test cases.

<!-- prettier-ignore -->
```js
function run(a, b) { // <-- Biến a, b đã cho trước
    var a = 2 // <-- Biến a bị khai báo lại
    var b = 1 // <-- Biến b bị khai báo lại
    c = a + b

    return c;
}
```

#### Ví dụ 2: Sửa tên hàm cho trước

Ví dụ đây là code cho trước trong một bài tập:

<!-- prettier-ignore -->
```js
function run(a, b) {
    return c = ...
}
```

… nhưng bạn lại đổi tên hàm:

<!-- prettier-ignore -->
```js
function hihi(a, b) { // <-- tên hàm bị đổi từ "run" thành "hihi"
    return c = ...
}
```

… hoặc bạn lại đổi vị trí các tham số cho trước:

<!-- prettier-ignore -->
```js
function hihi(b, a) { // <-- a & b đã bị đổi chỗ
    return c = ...
}
```

… hoặc bạn chơi lớn xoá luôn hàm run của F8:

<!-- prettier-ignore -->
```js
// Chơi lớn, xoá luôn hàm của F8
var a = 2
var b = 1
c = a + b
```

Trên là một số điều các bạn cần chú ý khi làm bài tập nhé. Nếu là người mới học thì cứ bình tĩnh mà học thôi, đừng vội vàng quá mà tới những bài sau lại đi hỏi lại mình mấy vấn đề này nhé.

—End—
