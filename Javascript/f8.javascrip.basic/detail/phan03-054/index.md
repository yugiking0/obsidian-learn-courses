# Vòng lặp lồng nhau - Nested Loop

```js
// prettier-ignore
var myArr = [
  [1,2],
  [3,4],
  [5,6],
  [7,8]
]
// Print 1->8
for (var i in myArr) {
  // console.log(i);
  for (var j in myArr[i]) {
    console.log(myArr[i][j]);
  }
}
```
