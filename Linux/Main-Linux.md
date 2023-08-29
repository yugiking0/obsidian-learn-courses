# Linux
---

**1. Cài đặt ntpdate**
//Cai dat ntpdate
apt-get install ntpdate

//Update datetime IP Server 10.133.79.7
ntpdate 10.133.79.7

**2. Trỏ Repo về DN**
//Tai bo cai 
wget http://unix-repo-dn.fsoft.com.vn/setup/installrepo.sh

//Cap quyen bo cai
chmod 777 installrepo.sh 

//Cai dat
./installrepo.sh

**3. User - Pass Root**
- Dat pass root
passwd root
dat pass la: sU@F$0ft.com.vn
- User: itdn
itfdn
2!T@F$0ft.com.vn
- User Administrator
admin.win
uMhtR84J

**4. Cài SSH - Remoted**
***Ubuntu***
apt-get install openssh-server
sed -i '/#PermitRootLogin yes/c\PermitRootLogin no' /etc/ssh/sshd_config

***Redhat***
yum install openssh-server

// Restart service SSH
service sshd restart

***Check SSH Installed***
ssh -V
*OpenSSH_8.2p1 Ubuntu-4ubuntu0.8, OpenSSL 1.1.1f  31 Mar 2020*

**5. Check Remoted SSH**

![[ssh-002.png]]

![[Linux/image/Hostname/server-001.png]]

- Xem các thông tin:
whoami
Kiểm tra IP
> ip addr show
> ip a

- Remoted SSH
ssh user@ip_local
ví dụ: 
> ssh it@192.168.232.132

![[ssh-001.png]]

**5. Java** 
- Check java Installed
> java -version
 //hien ra cau lenh cai dat java 
> apt install openjdk-11-jre-headless

![[install-java-01.png]]

![[check-java-001.png]]

![[shutdown-001.png]]

**9. Join Domain**
- Đổi tên PC Hostname
- Bước 1: Đổi tên hiển thị
hostnamectl set-hostname [hostname]
Ví dụ: hostnamectl set-hostname ubuntuserver

![[hostname-change-03.png]]

- Bước 2: Thay đổi thông số
nano /etc/hosts
sua dong so 2 
127.0.1.1.1	[hostname]

![[hostname-change-01.png]]

Luu lai (Ctrl X -> Y)
sau do go reboot
> Reboot

- *Vì nếu chỉ change **Bước 1** thì mặc dù tên hiển thị đúng, nhưng vào vẫn còn tên cũ chưa đổi*
![[hostname-change-02.png]]

Tham khảo: [Ubuntu Linux Change Hostname (computer name))](https://www.cyberciti.biz/faq/ubuntu-change-hostname-command/)


- Kiem tra cau hinh dns
> nano /etc/resolv.conf

them 2 dong
nameserver 10.133.79.7
nameserver 10.133.79.6

luu lai

apt-get update
apt-get install realmd samba-common samba-common-bin samba-libs sssd-tools krb5-user adcli packagekit vim -y

hien bang thi go ( viet hoa)
FSOFT.FPT.VN
ok

kinit -V [account join domain]

realm --verbose join -U [account join domain] fsoft.fpt.vn

nano /etc/sssd/sssd.conf
sua lai

use_fully_qualified_names = True -> use_fully_qualified_names = False
fallback_homedir = /home/%d/%u -> fallback_homedir = /home/%u

Luu Lai
check da  join domain chua

realm list

check 1 account thuoc domain fsoft
reboot

id [account]

nano /etc/pam.d/common-account

them dong

session	required	pam_mkhomedir.so	skel=/etc/skel/	umask=0022
Luu lai