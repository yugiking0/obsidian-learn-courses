# Vòng lặp do/while

> Bài tập: In ra 1 dãy số từ 1->10

- Vòng lặp `do/while` sẽ chạy 1 lần trước rồi sau đó kiểm tra điều kiện để chạy vòng lặp.

- Vòng lặp `while` sẽ kiểm tra điều kiện rồi mới chạy vòng lặp.

```js
var i = 0;
do {
  i++;
  console.log('Line :' + i);
} while (i < 100);
```

### Bài toán áp dụng

> Bài toán: Kiểm tra đăng nhập bao nhiêu lần, nếu sai sẽ khóa lại không cho nhập nữa.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>F8 - Javascript Basic</title>
  </head>
  <body>
    <div>
      <p id="text-id"></p>
      Nhập số kiểu tra:
      <input id="btn-id" type="button" value="Nhập số" />
    </div>
    <!-- External -->
    <script src=".\main.js"></script>
  </body>
</html>
```

```js
const textID = document.querySelector('#text-id');
const btnID = document.querySelector('#btn-id');

var hiddenString = '123';
var lan = 1;
btnID.addEventListener('click', function () {
  var isSuccess = false;

  do {
    var numberInput = prompt(`Nhập lần ${lan}`);

    if (numberInput === hiddenString) {
      isSuccess = true;
      doCorrect();
      break;
    }

    lan++;

    if (lan >= 3) {
      doDisable();
      textID.textContent = 'Đã hết lần nhập!';
    }
  } while (lan <= 3 && !isSuccess);
});

function doCorrect() {
  textID.textContent = 'Dung roi!';
  doDisable();
}

// Disable text & Button
function doDisable() {
  btnID.disabled = true;
}
```
