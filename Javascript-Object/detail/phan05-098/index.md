# Promise Pain

---

Ở ví dụ: Thiết lập chatbox ở bài trước khi cần thực hiện các bước:

- Bước 1: Load Comments ở Backend
- Bước 2: Lấy danh sách các User comment ở bước 1.
- Bước 3: Xử lý load dữ liệu Backend chỉ lấy thông tin id,name của table Users ở Backend chỉ riêng theo danh sách User comment bước 2.
- Bước 4: Kết hợp các dữ liệu trả về: Comments và UserInfo để hiển thị.

Ta xem code:

```js
var users = [
  {
    id: 1,
    name: 'Kien Dam',
  },
  {
    id: 2,
    name: 'Son Dang',
  },
  {
    id: 3,
    name: 'Hung Dam',
  },
];

var comments = [
  {
    id: 1,
    user: 1,
    comment: 'Anh Son chua ra video a :(',
  },
  {
    id: 2,
    user: 2,
    comment: 'Vua ra xong em oi!',
  },
  {
    id: 3,
    user: 1,
    comment: 'Cam on anh ^^',
  },
];

// Load table comments
var getComments = new Promise(function (resolve, reject) {
  setTimeout(() => {
    resolve(comments);
  }, 1000);
});

var btn = document.querySelector('button');

/**
 * 1. Load comments
 * 2. Lấy userIDs
 * 3. Load users
 * 4. Lấy userInfo
 * 5. Kết hợp userInfo +  comments
 */

btn.onclick = () => {
  getComments
    .then(dataComments => {
      var userIds = dataComments.map(comment => comment.user);
      // Loađ infor user trong mảng User Comments
      return getUsers.then(users => {
        return [dataComments, users, userIds];
      });
    })
    .then(data => {
      var infoUsers = loadUsers(data[1], data[2]);
      // console.log(infoUsers);

      var html = '';
      for (var i = 0; i < data[0].length; i++) {
        // console.log(data[0][i].comment);
        var user = infoUsers.find(user => {
          return user.id == data[0][i].user;
        });
        html += `${user.name} : ${data[0][i].comment} \n`;
      }
      // console.log(html);
      document.body.innerText = html;
    });
};

var getUsers = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(users);
  }, 1000);
});

function loadUsers(users, userIds) {
  var result = users.filter(user => {
    return userIds.find(id => user.id == id);
  });
  return result;
}
```

- Ta thấy việc kế thừa lại biến data để xử lý ở bước sau theo chuỗi Promise Chain sẽ khó khăn khi khác block phải đẩy qua Array.
- Nếu có sự xen kẻ liên tục kế thừa dữ liệu ở các khối block và lúc thì xử lý đồng bộ lúc thì xử lý bất đồng bộ thì sẽ thực hiện thế nào?

Ví dụ: 
- Load dữ liệu của hóa đơn bán hàng sẽ liên quan đến các bảng ở backend 
    - Bảng Issue
    - Thông tin khách hàng
    - Bảng thông tin hàng hóa
    - Bảng thông tin tồn kho của hàng hóa đó.
    - Bảng công nợ của khách hàng
    - Bảng doanh thu - chi phí
    - Nhân viên bán hàng
    - ...
- Khi này cần xử lý:
    - Bước 1: Load backend phiếu Issue hóa đơn bán hàng
    - Bước 2: Lấy các danh sách id của: Mã khách, Mã nhân viên, Mã doanh thu - chi phí, Mã hàng,...
    - Bước 3: Xử lý load backend bất đồng bộ những thông tin cần lấy chỉ theo các danh sách bước 3.
    - Bước 4: Kết hợp kiểm tra tồn kho có đáp ứng số lượng xuất, kiểm tra công nợ, kiểm tra chi phí, sau khi có được số lượng tồn kho ở các kho, có công nợ khách hàng cho phép hoặc nợ quá lâu, kiểm tra có vượt chi phí cho phép,...
- Bài toán sẽ rất phức tạp nếu chỉ dùng Promise Chain ở các khối block cần return một promise để có thể vừa Đồng bộ theo luồng có kế thừa dữ liệu, vừa đôi khi load kiểm tra bất đồng bộ từng mục. Việc này sẽ dẫn đến nối đau:
    - Promise hell
    - Việc khó khăn có thể tái sử dụng dữ liệu bước trước và luôn phải trả về promise để dùng cho bước sau.
> Một trong những điểm hạn chế của Promise là không có cơ chế mặc định để bạn truyền dữ liệu giữa các promise objects với nhau

-> Nên cần có một công cụ nào đó khắc phục, bổ trợ cùng Promise nên tạm thời đó là chức năng `Async / Await`