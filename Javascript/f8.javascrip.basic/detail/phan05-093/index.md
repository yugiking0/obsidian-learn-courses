# Promise example

---

- [Bài tập](#1-bài-tập)
- [Các bước thực hiện](#2-các-bước-thực-hiện)
  - [1 Tạo data](#21-tạo-data)
  - [2 Load dữ liệu comments từ back-end](#22-load-dữ-liệu-comments-từ-back-end)
  - [3 Load dữ liệu User từ back-end](#23-load-dữ-liệu-user-từ-back-end)
  - [4 Xử lý Promise Chain cho load Comments => UserByID](#24-xử-lý-promise-chain-cho-load-comments-userbyid)
  - [5 Xử lý hiển thị trên comments-box](#25-xử-lý-hiển-thị-trên-comments-box)
- [Tổng hợp](#3-tổng-hợp)

---

## 1. Bài tập

- Xây dựng chat box đơn giản như sau:

![load Data](Javascript/f8.javascrip.basic/detail/phan05-093/images/007.png 'Lấy data')

- Giải lập Fake API Load dữ liệu từ Back-End bảng: user, comment
- Xử lý có độ trễ và hiển thị nội dung đoạn hội thoại chat.

## 2. Các bước thực hiện

### 2.1 Tạo data

```js
/**
 * Data Users, Comments
 */

var users = [
  {
    id: 1,
    name: 'Kien Pham',
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
    userID: 1,
    content: 'anh Son chua ra video :(',
  },
  {
    id: 2,
    userID: 2,
    content: 'Vừa ra em ơi!',
  },
  {
    id: 3,
    userID: 1,
    content: 'Cam on anh ^^',
  },
];
```

- Gồm bảng:
  - Bảng user: Lưu thông tin các user
  - Bảng comments: Gồm các comment

### 2.2 Load dữ liệu comments từ back-end

- Ta sẽ tạo 1 Promise giả lập lấy dữ liệu từ máy chủ về, sẽ có độ trễ

```js
function getComments() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(comments);
    }, 1000);
  });
}

getComments().then((comments) => {
  console.log(comments);
});
```

![get Comments](Javascript/f8.javascrip.basic/detail/phan05-093/images/002.png 'Lấy Comments')

### 2.3 Load dữ liệu User từ back-end

- Sau khi load xong Comments, ta cần lấy dữ liệu User từ Back-end
- Để tránh lấy nhiều dữ liệu cả bảng Users, ta chỉ cần lấy các user đã comment mà thôi.
- Cần xử lý Bất đồng bộ lấy Users sẽ là Promise

```js
function getUsersByID(userIds) {
  return new Promise((resolve) => {
    setTimeout(() => {
      //Lọc những User nằm trong Array userIDs
      var results = users.filter(function (user) {
        // Kiểm tra đối chiếu userIds các phần tử là user.id
        return userIds.includes(user.id);
      });
      return resolve(results);
    }, 1000);
  });
}

getUsersByID([1, 2]).then(function (users) {
  console.log(users);
});
```

![get usersByID](Javascript/f8.javascrip.basic/detail/phan05-093/images/003.png 'Lấy usersByID')

- Ở đây ta sẽ truyền vào 1 list là mảng user_id sẽ lấy từ danh sách các user_id của bảng Comments, để lấy ra những user trong bảng Users.

### 2.4 Xử lý Promise Chain cho load Comments => UserByID

- Xử lý phương thức Promise getComments, lấy danh sách các list User ID comment

```js
// Xử lý lấy Data cần lấy từ back-end theo Promise Chain
getComments().then(function (comments) {
  // Lấy userIds từ comments
  var userIds = comments.map(function (comment) {
    return comment.user_id;
  });
  console.log(userIds);
});

// [ 1, 2, 1 ]
```

- Để đảm bảo Promise Chain nên cần xử lý .then phải trả về là một Promise

```js
// Xử lý lấy Data cần lấy từ back-end theo Promise Chain
getComments()
  .then(function (comments) {
    // Lấy userIds từ comments
    var userIds = comments.map(function (comment) {
      return comment.user_id;
    });
    return getUsersByID(userIds).then(function (users) {
      return users;
    });
  })
  .then(function (users) {
    console.log(users);
  });

// [ { id: 1, name: 'Kien Pham' }, { id: 2, name: 'Son Dang' } ]
```

- Ta xử lý trả về data gồm những bảng liên quan cần xử lý

```js
getComments()
  .then(function (comments) {
    // Lấy userIds từ comments
    var userIds = comments.map(function (comment) {
      return comment.user_id;
    });
    return getUsersByID(userIds).then(function (users) {
      return {
        users: users,
        comments: comments,
      };
    });
  })
  .then(function (data) {
    console.log(data);
  });
```

![load Data](Javascript/f8.javascrip.basic/detail/phan05-093/images/004.png 'Lấy data')

### 2.5 Xử lý hiển thị trên comments-box

- Tạo file html như sau:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>F8 - Javascript Basic</title>
    <style>
      body {
        height: 100vh;
        /* display: flex; */
        align-items: center;
        background: linear-gradient(to top left, #28b487, #7dd56f);
      }

      h1 {
        width: 100%;
        text-align: center;
        color: white;
      }
      .hidden {
        display: dis;
      }
    </style>
  </head>
  <body>
    <body>
      <h1>Promise Javascript</h1>
      <ul id="comments-box">
        <li></li>
      </ul>
    <script src=".\script.js"></script>
  </body>
</html>
```

- Có tab ul.li có id = "comments-box"

```html
<ul id="comments-box">
  <li></li>
</ul>
```

- Ta sẽ đẩy dữ liệu vào đây

![load Data](Javascript/f8.javascrip.basic/detail/phan05-093/images/004.png 'Lấy data')

- ở .then tiếp theo ta xử lý data:
  - Duyệt qua từng data.comments là comment
  - Mỗi comment ta sẽ có user_id và content
  - Lấy user_id truy xuất bảng data.users lấy user name tương ứng từ liên kết user id.

```js

.then(function (data) {
    // var commentsBox = document.getElementById('comments-box');
    var html = '';

    // Lặp qua các Comments để lấy nội dung
    data.comments.forEach(function (comment) {
      // Với mỗi comment có user_id sẽ kết nối qua user để lấy thông tin user
      var user = data.users.find(function (user) {
        return user.id == comment.user_id;
      });
      console.log(user);
    });
  });
```

![load Data](Javascript/f8.javascrip.basic/detail/phan05-093/images/005.png 'Lấy data')

- Load lên comments-box

```js
  .then(function (data) {
    //   var commentsBox = document.getElementById('comments-box');
    var html = '';

    // Lặp qua các Comments để lấy nội dung
    data.comments.forEach(function (comment) {
      // Với mỗi comment có user_id sẽ kết nối qua user để lấy thông tin user
      var user = data.users.find(function (user) {
        return user.id == comment.user_id;
      });
      html += `<li> ${user.name} : ${comment.content}</li>`;
    });
    console.log(html);
  });

```

![load Data](Javascript/f8.javascrip.basic/detail/phan05-093/images/006.png 'Lấy data')

```js
  .then(function (data) {
    var commentsBox = document.getElementById('comments-box');
    var html = '';

    // Lặp qua các Comments để lấy nội dung
    data.comments.forEach(function (comment) {
      // Với mỗi comment có user_id sẽ kết nối qua user để lấy thông tin user
      var user = data.users.find(function (user) {
        return user.id == comment.user_id;
      });
      html += `<li> ${user.name} : ${comment.content}</li> \n`;
    });

    commentsBox.innerHTML = html;
  });

```

![load Data](Javascript/f8.javascrip.basic/detail/phan05-093/images/007.png 'Lấy data')

## 3. Tổng hợp

- Ta tạo 1 file html như sau:

```html

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>F8 - Javascript Basic</title>
    <style>
      body {
        height: 100vh;
        align-items: center;
        background: linear-gradient(to top left, #28b487, #7dd56f);
      }

      h1 {
        width: 100%;
        text-align: center;
        color: white;
      }
      .hidden {
        display: dis;
      }
    </style>
  </head>
  <body>
    <body>
      <h1>Promise Javascript</h1>
      <ul id="comments-box">
        <li></li>
      </ul>
    <script src=".\script.js"></script>
  </body>
</html>

```

- file script.js sẽ là

```js
/**
 * Data Users, Comments
 */

var users = [
  {
    id: 1,
    name: 'Kien Pham',
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
    user_id: 1,
    content: 'anh Son chua ra video :(',
  },
  {
    id: 2,
    user_id: 2,
    content: 'Vừa ra em ơi!',
  },
  {
    id: 3,
    user_id: 1,
    content: 'Cam on anh ^^',
  },
];

// Tạo load dữ liệu Comments Bất đồng bộ là một Promise
function getComments() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(comments);
    }, 1000);
  });
}

// Tạo load dữ liệu Users Bất đồng bộ là một Promise
// lấy theo list ID từ user đã Comments

function getUsersByID(userIds) {
  return new Promise((resolve) => {
    setTimeout(() => {
      //Lọc những User nằm trong Array userIDs
      var results = users.filter(function (user) {
        // Kiểm tra đối chiếu userIds các phần tử là user.id
        return userIds.includes(user.id);
      });
      return resolve(results);
    }, 1000);
  });
}

// Xử lý lấy Data cần lấy từ back-end theo Promise Chain
getComments()
  .then(function (comments) {
    // Lấy userIds từ comments
    var userIds = comments.map(function (comment) {
      return comment.user_id;
    });
    return getUsersByID(userIds).then(function (users) {
      return {
        users: users,
        comments: comments,
      };
    });
  })
  .then(function (data) {
    var commentsBox = document.getElementById('comments-box');
    var html = '';

    // Lặp qua các Comments để lấy nội dung
    data.comments.forEach(function (comment) {
      // Với mỗi comment có user_id sẽ kết nối qua user để lấy thông tin user
      var user = data.users.find(function (user) {
        return user.id == comment.user_id;
      });
      html += `<li> ${user.name} : ${comment.content}</li> \n`;
    });

    commentsBox.innerHTML = html;
  });
```

![load Data](Javascript/f8.javascrip.basic/detail/phan05-093/images/007.png 'Lấy data')

- Hiểu chứng năng mảng và làm việc với Mảng(filter, includes, map, find)
- Hiểu về hàm và callback
- Hiểu về Promise và promise chain
- DOM

---


```js
var btn = document.querySelector("button");
// var btn = document.querySelector("#btnLoad");
var commentsBox = document.querySelector("#comments-box");

btn.onclick = function () {
  showChat();
};

// 01. DataBase
var users = [
  {
    id: 1,
    name: "Sơn Đặng",
  },
  {
    id: 2,
    name: "Kiên Nguyễn",
  },
  {
    id: 3,
    name: "Hưng Đàm",
  },
];

var comments = [
  {
    id: 1,
    content: "Anh Sơn chưa ra Video à :(",
    user: 1,
  },
  {
    id: 2,
    content: "Vừa ra xong em ơi!",
    user: 2,
  },
  {
    id: 3,
    content: "Cảm ơn anh ^^",
    user: 1,
  },
];

function showChat() {
  // console.log("Hello:" + Math.random());
  loadComments()
    .then(function (coments) {
      // console.log(data);
      var userIds = coments.map(function (comment) {
        return comment.user;
      });
      return getUserbyIDs(userIds)
        .then(function (users) {
          return {
            users: users,
            comments: comments,
          };
        })
        .catch((err) => console.error(err + ""));
    })
    .then(function (data) {
      // Load chatBlock
      renderBlock(data);
    })
    .catch((err) => console.error(err + ""));
}

// 02. Load comments
function loadComments() {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      resolve(comments);
    }, 1000);
  });
}

// 03. Load Users in list UserIds of comments
function getUserbyIDs(userIds) {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      //  Check userID không có ở users
      var checkId = userIds.every((id) => {
        var err = users.find((user) => user.id === id);
        if (!err) reject(new Error("Lỗi tại ID: " + id));
        return 1;
      });

      //  Lấy danh sách thông tin Users
      var result = users.filter(function (user) {
        return userIds.find(function (userId) {
          return userId === user.id;
        });
      });
      resolve(result);
    }, 1000);
  });
}

// getUserbyIDs([1,2,3])
//   .then((data) => console.log(data))
//   .catch((err) => console.error(err+''));

// Show chatBlocks
function renderBlock(data) {
  var htmls = "";

  data.comments.forEach(function (comment) {
    var userInfo = data.users.find(function (user) {
      return user.id == comment.user;
    });
    htmls += `<li> ${userInfo.name} : ${comment.content}</li> \n`;
  });

  commentsBox.innerHTML = htmls;
}
```