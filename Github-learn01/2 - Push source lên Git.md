## Push source lên Git

![[git-002.png]]

### Gồm 3 cách:

- **Cách 1**: Từ thư mục ở Local Disk(PC) chạy lần lượt các lệnh

```git
echo "# aliconcon.io" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/yugiking0/aliconcon.io.git
git push -u origin main
```

- **Cách 2**: Đẩy thư mục đã có ở Local Disk lên Repository

![[git-003.png]]

```git
git remote add origin https://github.com/yugiking0/aliconcon.io.git
git branch -M main
git push -u origin main
```

- **Cách 3**: Import kéo thả folder

## Bước 2: Tạo folder aliconcon
- Tạo folder aliconcon ở Local Disk Workspace
- Liên kết folder với git Repository
![[git-004.png]]

- Tạo thư mục src - Source

![[git-005.png]]

![[git-006.png]]

```git
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/yugiking0/aliconcon.io.git
git push -u origin main
```


![[git-007.png]]


![[git-008.png]]

