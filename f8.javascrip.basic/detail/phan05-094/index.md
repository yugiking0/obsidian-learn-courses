# Fetch dữ liệu

---

## 1. Font-end và Back-end

### 1.1 Font-end

- Xây dựng giao diện người dùng

### 1.2 Back-end

- Xây dựng logic xử lý trên cơ sở dữ liệu Database

### 1.3 API

- Từ Back-end sẽ đẩy dữ liệu cho Font-end để xây dựng giao diện thông qua API
- API - Application Programming Interface : Cổng giao tiếp dữ liệu
- Back-end sẽ đưa ra các API theo dạng URL giao tiếp theo giao thức REST để xử lý dữ liệu
- Các ví dụ URL API theo REST như sau:
  https://jsonplaceholder.typicode.com/posts
  https://jsonplaceholder.typicode.com/comments

![URL API](./images/001.png 'posts')
![URL API](./images/002.png 'comments')

- Lúc này Font-end từ các link URL API sẽ lấy dữ liệu về và render nên các giao sử dụng.

## 2. Fetch

- Fetch là một công cụ hỗ trợ get dữ liệu từ URL API về.
- Dữ liệu trả về của fetch:
  - Là một Promise
  - Kiểu dữ liệu JSON
  - Cần xử lý chuyển lại kiểu dữ liệu JavaScript (**`response.json()`**) để sử dụng render

```js
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(json => console.log(json))

{
	"userId": 1,
	"id": 1,
	"title": "delectus aut autem",
	"completed": false
}
```

- Với fetch đã hỗ trợ công cụ .json() để chuyển dữ liệu qua kiểu JavaScript mà không cần sử dụng các JSON Parse như đã học ở bài trước.

```js
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(json => console.log(json));

// Thay vì
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => JSON.parse(response)) // Dùng JSON Parse
  .then(json => console.log(json));
```

## 3. JSON

## 4. Ví dụ

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Example Fetch API</title>
  </head>
  <body></body>
  <script src="app.js"></script>
</html>
```

```js
var url = 'https://jsonplaceholder.typicode.com/posts';

fetch(url)
  .then(response => response.json())
  .then(json => {
    document.body.innerHTML = json
      .map(post => {
        return `
        <h1> ${post.title}</h1>
        <p> ${post.body}</p>
        `;
      })
      .join('');
  })
  .catch(() => {
    console.error(new Error('Có lỗi!'));
  });
```

![URL API](./images/003.png 'posts')

![URL API](./images/004.png 'posts')

---
