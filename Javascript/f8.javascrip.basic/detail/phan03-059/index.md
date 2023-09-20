# Bài tập reduce method của Array

```js
/**
 * làm phẳng mảng
 */
var depthArray = [1, 2, 3, [4, 5], 6, [7, 8, 9]];
var flatArray = depthArray.reduce(function (acc, cur) {
  return acc.concat(cur);
}, []);

console.log(flatArray);
```

**_Bài tập_**

- Làm phẳng mảng khi một mảng có những mảng con.

```js
var depthArray = [1, 2, 3, [4, 5], 6, [7, 8, 9]];
/**
 * Original Reduce Method Array
var flatArray = depthArray.reduce(function (acc, cur) {
  return acc.concat(cur);
}, []);
console.log(flatArray);
*/

// DuyDQ: New Method Array Reduce2
Array.prototype.reduce2 = function (myCallBack, myInitialValue) {
  if (myInitialValue == undefined) {
    myInitialValue = 0;
  }
  this.forEach(function (value, index, originArray) {
    myInitialValue = myCallBack(myInitialValue, value, index, originArray);
  });
  return myInitialValue;
};

var newArr = depthArray.reduce2(function (acc, cur) {
  return acc.concat(cur);
}, []);

console.log(newArr);
```
