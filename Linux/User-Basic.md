# User
---
**1. Show all user**
getent passwd {1000..60000}

![[user-001.png]]

**2. Add User**

![[user-002.png]]

**- Create a standard user account** 
useradd -m [cli_user]
Ví dụ: useradd -m duy_user

**- Create an administrator user account** 
useradd -m [admin_user] -G sudo
Ví dụ: useradd -m duy_admin -G sudo

**- Change Password**
passwd cli_user1
passwd duy_user

![[sudo-001.png]]

**3. Delete User**
> deluser duy_user

![[user-003.png]]

Tham khảo: [How to Add and Delete Users on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-20-04)

**4. Set Root**
- Change user Standard to user Root(Administrator)


**5. Group Root**
- Create Goup User

- Create Goup Root

- Add user to Group

- Remove User out Group



**9. FSoft**
- **ADD USER**
adduser [accoutn user] 
useradd -m itfdn.root
useradd –m user-account

- **SET PASSWORD** 
// Dat pass root
passwd root
//Dat pass la: sU@F$0ft.com.vn

**- User itfdn.root**
User: itfdn.root
Pass: *2!T@F$0ft.com.vn*

**- User itfdn**
User: itfdn
Pass: *2!T@F$0ft.com.vn*

**- User root**
User: root
Pass: *sU@F$0ft.com.vn*

- **User Administrator admin.wins**
User: admin.win
Pass: *uMhtR84J*

- **User Local User/ WFH**
User: [UserName]
Pass: WFH@12345 / *WFH!12345*
Pass: Fsoft@12345@
