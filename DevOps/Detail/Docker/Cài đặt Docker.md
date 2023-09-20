## Hướng dẫn cài đặt Docker
---
### Cài Docker trên macOS

Tải bộ cài tại [Docker Desktop for Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac), cài đặt đơn giản như các công cụ thông thường.

### Cài Docker trên Windows 10

Tải bộ cài tại [Docker Desktop for Windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows), tiến hành cài đặt. Đối với Windows phải kích hoạt chế độ `Hyper-V virtualization` (Ở chế độ này bạn không dùng được VirtualBox nữa).

Nếu chưa kích hoạt `Hyper-V` thì kích hoạt theo hướng dẫn [Enable Hyper-V](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v#enable-hyper-v-using-powershell)

Chạy lệnh PowerShell sau để kích hoạt:

Copy

```bash
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

**Kích hoạt thông qua thiết lập Windows**

1. Nhấn phải chuột vào biểu tượng cửa sổ, chọn **Apps and Features**.
2. Chọn **Programs and Features**.
3. Chọn **Turn Windows Features on or off**.
4. Đánh dấu vào **Hyper-V** như hình dưới.

![[Pasted image 20230907095644.png]]

### Cài Docker trên Ubuntu

Chạy các lệnh để cài đặt:

Copy

```bash
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
apt-cache policy docker-ce
sudo apt install docker-ce
sudo systemctl status docker
```

Sau khi cài đặt, bạn có thể cho user hiện tại thuộc group docker, để khi gõ lệnh không cần xin quyền `sudo`

Copy

```bash
sudo usermod -aG docker $USER
```

Logout sau đó login lại để có hiệu lực.

Ngoài ra khi sử dụng đến thành phần `docker-compose` thì bạn cài thêm

Copy

```bash
sudo apt install docker-compose
```

Nếu có nhu cầu sử dụng Docker Machine trên Ubuntu, (công cụ tạo – quản lý các máy ảo chạy Docker Engine, các máy ảo này tạo bởi VirtualBox, bạn sử dụng Docker-machine để thực hành các ví dụ kết nối nhiều máy chạy Docker Engine khác nhau tạo thành cụm Server), thì cài thêm Docker Machine. Phiên bản mới nhất lấy tại [Docker Machine](https://github.com/docker/machine/releases).

Ví dụ cài bản v0.16.1, gõ lệnh sau:

Copy

```bash
curl -L https://github.com/docker/machine/releases/download/v0.16.1/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
chmod +x /tmp/docker-machine &&
sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
```

Tất nhiên là Docker Machine cần VirtualBox để làm việc, nếu chưa có thì cài thêm

Copy

```bash
sudo apt install virtualbox
```

### Cài Docker trên CentOS7/RHEL7

Copy

```bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce
sudo usermod -aG docker $(whoami)
sudo systemctl enable docker.service
sudo systemctl start docker.service

#Cài thêm Docker Compose
sudo yum install epel-release
sudo yum install -y python-pip
sudo pip install docker-compose
sudo yum upgrade python*
docker-compose version
```

### Cài Docker trên CentOS8/RHEL8

Copy

```bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce

# Nếu lỗi, chạy lệnh sau
sudo dnf install --nobest docker-ce -y


sudo usermod -aG docker $(whoami)
sudo systemctl enable docker.service
sudo systemctl start docker.service

#Cài thêm Docker Compose
sudo yum install epel-release
sudo yum -y install python2-pip
sudo pip2 install docker-compose
sudo yum upgrade python*
docker-compose version
```

Khi đã có **Docker** trên máy, làm việc với Docker để quan lý các thành phần của nó … hầu hết làm việc qua giao diện dòng lệnh CLI của hệ thống: trên macOS/Linux mở `termial` để gõ lệnh, trên Windows thì nên dùng PS (`PowerShell`) để chạy các lệnh Docker.
