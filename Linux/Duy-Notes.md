### 1. Xem các thông tin:
whoami

**- Show all user** 
getent passwd {1000..60000}

**- User it as Administrator - SU**
User: it
Pass: *123*

**- User admin**
User: admin
Pass: *admin*

- Exit the root shell 
> exit 

- Switch to the new user account 
> su - admin 
> su - it
> su - username

- Show the current user account 
> whoami

- Kiểm tra IP
ip addr show : để check IP
ip a

### 2. SSH
- SSH
ssh it@192.168.232.132
user@ip_local

- Cài đặt SSH
sudo apt install openssh-server

### 3. GUI
- Tắt giao diện GUI chỉ dùng command
Disable
sudo systemctl set-default multi-user
gnome-session-quit

- Bat Desktop
sudo systemctl start gdm3

Tắt giao diện GUI chỉ dùng command

sudo systemctl set-default multi-user

gnome-session-quit

- How to enable GUI to start on boot
sudo systemctl set-default graphical

sudo systemctl start gdm3
