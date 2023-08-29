# JSON SERVER

---

- [1. Chức năng](#1-chức-năng)
- [2. Cài đặt](#2-cài-đặt)
- [3. Sử dụng](#3-sử-dụng)

---

## 1. Chức năng

- Dựng nên một Fake API , Mock API để test chức năng khi Back-end chưa dựng xong API để Demo.
- Chạy dịch vụ tạo Fake API theo chuẩn REST có thể áp dụng các giao thức xử lý CRUD (Create - Read - Update - Delete).

## 2. Cài đặt

- Để cài được JSON Server thì cần cài đặt trước:
  - NodeJS
  - npm: Node Package Manager
    (Kiểu tra bằng cách chạy Terminal: node -v và npm -v)

![Check](./images/001.png 'Console')

- Khởi tạo NodeJS quản lý cho dự án:
  `npm init`
  Xem file **_package.json_**
  ![Init JSON](./images/002.png 'init')

- Để cài đặt JSON Server có kiểu:
  - Cài vào thư mục chương trình đang chạy(Chỉ có dự án này sử dụng, dự án khác muốn chạy thì phải cài đặt)
  - Cài vào Global của máy tính PC(cài vào thư mục NodeJS dùng cho các dự án trên máy)
- Câu lệnh cài:
  - Cài Global:
    `npm install -g json-server` hoặc `npm i -g json-server`
  - Cài riêng cho dự án:
    `npm install json-server` hoặc `npm i json-server`
- Tương ứng với mỗi cách cài sẽ có cách thiết lập để chạy khác nhau.
- Tham khảo ở link : [json-server](https://github.com/typicode/json-server)

## 3. Sử dụng

- Khai báo chạy JSON Server chạy riêng cho dự án.
- Tạo file **_db.json_**

```json
{
  "courses": [
    {
      "id": 1,
      "name": "HTML, CSS từ Zero đến Hero",
      "description": "Trong khóa này chúng ta sẽ cùng nhau xây dựng giao diện 2 trang web là The Band & Shopee."
    }
  ],
  "users": [
    {
      "id": 1,
      "name": "Sơn Đặng"
    },
    {
      "id": 2,
      "name": "Kiên Nguyễn"
    }
  ]
}
```

- Khai báo để JSON Server chạy kiểu riêng từng dự án, ta sửa file **_package.json_** ở mục **_scripts_**

```js
  "scripts": {
    "start": "json-server --watch db.json",
    "test": "echo \"Error: no test specified\" && exit 1"
  },

```

![package.json](./images/003.png 'scripts')

- Để chạy JSON Server ta dùng Terminal theo cú pháp
  `npm start`
  ![JSON Server](./images/004.png 'Run Start')
- Kiểm tra: Ta chạy link URL trên trình duyệt

```js
  Resources
  http://localhost:3000/courses
  http://localhost:3000/users
```

![Check URL](./images/005.png 'Kiểm tra')

- Hoặc viết xử lý lại sử dụng `fetch`

```js
var url = 'http://localhost:3000/courses';

fetch(url)
  .then(response => response.json())
  .then(courses => {
    document.body.innerHTML = courses
      .map(course => {
        return `
        <h1> ${course.name}</h1>
        <p> ${course.description}</p>
        `;
      })
      .join('');
  })
  .catch(() => {
    console.error(new Error('Có lỗi!'));
  });
```

![Check URL](./images/006.png 'Kiểm tra')
