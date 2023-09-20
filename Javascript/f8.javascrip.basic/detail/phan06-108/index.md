# Tagged template literals

---

## 1. Xét ví dụ Highlight đoạn văn bản

- Ta xét ví dụ xử lý Hight những cụm từ theo biến được gán vào trong đoạn văn bản sau:

```js
const name = 'F8';
const course = 'Javascript';

console.log(`Học lập trình ${course} tại ${name}!`);
// Học lập trình Javascript tại F8!

/**
 * Muốn highlight "Javascript" và "F8" trong đoạn test trên.
 */
//===============~~=====================

function highlight(content) {
  console.log(content);
}

highlight(`Học lập trình ${course} tại ${name}!`);
// Học lập trình Javascript tại F8!
```

- Nếu như ta bỏ đi cặp ngoặc `()` sẽ thấy được như sau:

```js
const name = 'F8';
const course = 'Javascript';

function highlight(content) {
  console.log(content);
}

highlight`Học lập trình ${course} tại ${name}!`;
```

![Tagged template literals](Javascript/f8.javascrip.basic/detail/phan06-108/images/001.png 'Log')

- Nếu xử lý thêm `rest` thì sẽ được:

```js
const name = 'F8';
const course = 'Javascript';

function highlight(...rest) {
  console.log(rest);
}

highlight`Học lập trình ${course} tại ${name}!`;
```

![Tagged template literals](Javascript/f8.javascrip.basic/detail/phan06-108/images/002.png 'Tagged template literals')

- Ta thấy cụm từ được tách thành nhiều phần mảng khác nhau

![Tagged template literals](Javascript/f8.javascrip.basic/detail/phan06-108/images/003.png 'Tagged template literals')

- vậy: `Tagged template literals` là gì?

  - Là việc tách một đoạn `Template literals` biểu diễn thành mảng chứa các loại phần tử khác nhau.
  - Từ đây có thể phục vụ xử lý lại theo cách nào đó.

- Điều kiện để sử dụng `Tagged template literals`:
  - Đoạn văn bản được dùng theo kiểu `Template literals` sẽ bao gồm:
    - Biến
    - Sử dụng dấu `` (Dấu nháy bên cạnh phiếm số 1, phía trên bên trái bàn phím)
  - Khi gọi hàm thì bỏ đi cặp ngoặc () mà sử dụng luôn `Template literals` sau function
  - Sử dụng `rest` để tách đoạn văn bảng thành một mảng.

![Tagged template literals](Javascript/f8.javascrip.basic/detail/phan06-108/images/004.png 'Tagged template literals')

## 2. Ứng dụng Highlight đoạn văn bản

- Ý tưởng sẽ tạo thành 2 nhóm mảng:
  - Nhóm chứa đoạn văn bản thường
  - Nhóm chứa các biến `Template Literals`
- Sau đó nối lại xen kẽ, sau khi bổ sung highlight cho các biến `Template Literals`.

```js
const name = 'F8';
const course = 'Javascript';

function highlight([first, ...values], ...rest) {
  console.log('first::: ', first); // Học lập trình
  console.log('values::: ', values); // [' tại ', '!']
  console.log('rest::: ', rest); // ['Javascript', 'F8']
}
highlight`Học lập trình ${course} tại ${name}!`;
```

![Tagged template literals](Javascript/f8.javascrip.basic/detail/phan06-108/images/005.png 'Tagged template literals')

- Dùng `reduce` để tạo mới lại đoạn văn bản như sau:

```js
const name = 'F8';
const course = 'Javascript';

function highlight([first, ...values], ...rest) {
  console.log(first); // Học lập trình
  console.log(values); // [' tại ', '!']
  console.log(rest); // ['Javascript', 'F8']
  return rest
    .reduce((acc, cur) => {
        return [...acc, `<b>${cur}</b>`, values.shift()];
      },[first]
    ).join('');
}
const html = highlight`Học lập trình ${course} tại ${name}!`;
console.log(html);
// Học lập trình <b>Javascript</b> tại <b>F8</b>!
document.write(html);
```

![Tagged template literals](Javascript/f8.javascrip.basic/detail/phan06-108/images/006.png 'Tagged template literals')

---
