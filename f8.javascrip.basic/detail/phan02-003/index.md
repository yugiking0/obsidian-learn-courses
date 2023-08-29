# SỬ DỤNG JAVASCRIPT VỚI HTML

---

Trong thực tế chúng ta có 2 cách thông dụng để sử dụng Javascript trong HTML.

## Internal (sử dụng nội bộ)

- Đặt trực tiếp cặp thẻ script vào mã HTML và viết javascript giữa cặp thẻ này.

```html
<body>
  ...
  <script>
    alert("Xin chào các bạn!");
  </script>
  ...
</body>
```

---

## External (sử dụng file `.js` bên ngoài)

- Các bạn sẽ thường thấy cách này được sử dụng vì mã javascript được viết riêng biệt ra một file `.js` ở bên ngoài. Mã của chúng ta sẽ gọn gàng, dễ nhìn, dễ chỉnh sửa hơn vì không bị viết lẫn lộn vào HTML như cách `Internal`.

```html
<body>
  ...
  <script src="đường_dẫn_tới_file.js"></script>
</body>
```

- Trong trường hợp sử dụng file `.js` thì nội dung của file không được chứa thẻ `<script>`. Sau đây là ví dụ nội dung file `.js`.

---

### Đúng

```js
// Nội dung file .js
alert("Xin chào các bạn!");
```

### Sai

```js
// Nội dung file .js
<script>alert('Xin chào các bạn!')</script>
```

---

> Trong thực tế cách **`Internal`** cũng được sử dụng khá phổ biến trong các trường hợp mã `javascript` đó chỉ sử dụng tại duy nhất một màn hình và số lượng các dòng code không nhiều. Tuy nhiên cách này các bạn nên tránh việc lạm dụng vì sẽ dễ gây rác `source code` và lặp lại code không mong muốn
