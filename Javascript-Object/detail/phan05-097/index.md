# Xử lý REST CRUD với Fetch và REST API

---

## 1. Mô tả

- Dùng JSON Server để dựng Mock API/ Fake API
- Thông qua Fetch để xử lý dữ liệu thông qua API như CRUD

Xóa module npm
`npm uninstall json-server`

Xóa npm init - Xóa thư mục node_modules
`rm node_modules`
![Remove node_modules](./images/003.png 'Remove node_modules')

**Lưu ý:**

- Tách thư mục API Json Server riêng ra
- Tách thư mục Project Demo Fetch ra riêng
- Nguyên nhân nếu để chung vào chạy Live Server của Project mỗi khi db.json được thay đổi sẽ load lại website làm cho Render lại hiển thị.
  ![QLKH](./images/002.png 'Danh sách khóa học')

## 2. Bài Toán

- Xây dựng trang web quản lý các khóa học
  - Render hiển thị
  - Thêm các khóa học
  - Cập nhật khóa Học
  - Xóa khóa học

![QLKH](./images/001.png 'Danh sách khóa học')

## 3. Thực Hiện

- Chạy dịch vụ Fake Api JSON Server
  `npm start`
  `http://localhost:3000/courses`
- Chạy live Server
  `live-server --port=5500`
