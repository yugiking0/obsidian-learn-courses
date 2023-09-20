# Sử dụng Postman làm việc với REST API

---

---

## 1. Chức năng

- Công cụ để thao tác với database thông qua URL API
- Thao tác test các chức năng REST xử lý dữ liệu trên database

## 2. Cài đặt

- Cài đặt tại link : [postman](https://www.postman.com/downloads)
  ![postman](Javascript/f8.javascrip.basic/detail/phan05-096/images/001.png 'postman')

- Xem thên thông tin tại [postman](https://www.postman.com/downloads)

## 3. Sử dụng

- Tuân theo REST nên có thể xử lý CRUD trên dữ liệu
  - C - CREATE : Tạo mới
  - R - READ : Đọc dữ liệu
  - U - UPDATE : Cập nhật dữ liệu
  - D - DELETE : Xóa dữ liệu
- Với sử dụng Postman có thể xử lý tương ứng với các chức năng
  - GET : Lấy dữ liệu (READ)
  - POST: Tạo dữ liệu (CREATE)
  - PUT/PATCH : Cập nhật dữ liệu (UPDATE)
  - DELETE : Xóa dữ liệu (DELETE)
- Ngoài ra có thêm những chức năng khác:
  ![postman](Javascript/f8.javascrip.basic/detail/phan05-096/images/002.png 'postman')

- Xem thên thông tin tại [postman](https://www.postman.com/downloads)

Xóa module npm
`npm uninstall json-server`

Xóa npm init - Xóa thư mục node_modules
`rm node_modules`

![Remove node_modules](Javascript/f8.javascrip.basic/detail/phan05-096/images/005.png 'Remove node_modules')

**Lưu ý:**

- Tách thư mục API Json Server riêng ra
- Tách thư mục Project Demo Fetch ra riêng
- Nguyên nhân nếu để chung vào chạy Live Server của Project mỗi khi db.json được thay đổi sẽ load lại website làm cho Render lại hiển thị.

  ![QLKH](Javascript/f8.javascrip.basic/detail/phan05-096/images/004.png 'Danh sách khóa học')
