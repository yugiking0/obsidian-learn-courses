- Cần phải có tài khoản Github

![[Pasted image 20230829165447.png]]

![[Pasted image 20230829165551.png]]

## Các loại đẩy lên Github
### 1. Có sẵn project ở github kéo về, sau đó đẩy từ local lên Github
1. Tạo 1 github repository(folder) - nơi chứa code
2. Clone project này: git clone [link_your_repo]
3. Viết code
4. Đẩy code lên github
- git status *(Kiểm tra trạng thái files)*
- git add . *(Thêm files)*
- git commit -m "Mô tả lần đẩy code lên" *(Tạo nội dung commit push)*
- git push origin main

```bash
git clone [link_your_repo]
git status
git add . 
git commit -m "Mô tả lần đẩy code lên"
git push origin main
```

### 2. Tạo project local và đẩy lên github
1. Tạo 1 github repository
2. git init *(Khởi tạo folder này dùng git)*
3. Viết code
4. Đẩy code lên github
- git status *(Kiểm tra trạng thái files)*
- git add . *(Thêm files)*
- git commit -m "Mô tả lần đẩy code lên" *(Tạo nội dung commit push)*
- git remote add origin [link_your_repo]
- git push origin master

```bash
git init
git status
git add . 
git commit -m "Mô tả lần đẩy code lên"
git remote add origin [link_your_repo]
git push origin master
```

![[Pasted image 20230829171357.png]]

