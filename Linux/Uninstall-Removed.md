# Gỡ cài đặt package bằng terminal
---
**1. Kiểm tra các package**
- Những app đã được cài đặt
sudo apt list --installed

- Toàn bộ Apt Full Repo
sudo apt list   | grep ssh

- Check App Name search Grep trong Repo
![[search-dpkg-01.png]]

- Liệt kê theo search Grep

```
$ dpkg --list | grep ssh
```

![[search-dpkg-03.png]]

**2. Removed**
- Vẫn còn rác file cũ
sudo apt-get --purge remove [app]

- Xóa toàn bộ ten_package
sudo apt-get --purge remove <ten_package>

- Xóa luôn những [package] phụ thuộc được cài còn xót lại
sudo apt-get autoremove

**3. Các cách cài đặt App Lib**
- Cài đặt từ Repo
apt-get install ntpdate
sudo apt install openssh-server

- Cài đặt từ file tải về
[root@localhost opt]#sudo chmod +x install.sh
[root@localhost opt]#sudo ./install.sh -i (lưu ý: cần quyền root để chạy file cài đặt)

- Gen ITC Asset
cd ./Desktop
chmod +x /aescan.sh
/aescan.sh -i

