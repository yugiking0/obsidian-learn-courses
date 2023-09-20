# BREAK & CONTINUE TRONG VÒNG LẶP

## 1. Break

- Thoát khỏi vòng lặp

```js
for (var i = 1; i <= 100; i++) {
  if (i > 10) {
    console.log('Không in số hơn 10.');
    break;
  }
  console.log(i);
}
```

- Khi gặp Break sẽ thoát khỏi vòng lặp hiện tại.

### 2. Continue

- Bỏ qua khối lệnh phía sau Continue và bắt đầu chạy lần lặp mới.

```js
for (var i = 1; i <= 10; i++) {
  if (i % 2 !== 0) {
    continue;
  }
  console.log(i);
}
```

![Continue](Javascript/f8.javascrip.basic/detail/phan03-053/images/001.png 'Continue')
