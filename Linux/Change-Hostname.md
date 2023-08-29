# Change Hostname
---
![[hostname-change-00.png]]

**Bước 1: Dùng Distro** 
sudo hostname [new-server-name-here]
hostnamectl set-hostname [hostname]

Ví dụ: hostnamectl set-hostname ubuntuserver

![[hostname-change-03.png]]

- **Bước 2: Thay đổi thông số hosts**
sudo nano /etc/hosts

- sua dong so 2 
127.0.1.1.1	[hostname]

![[hostname-change-01.png]]
Luu lai (Ctrl X -> Y)

- sau do go reboot
> Reboot
