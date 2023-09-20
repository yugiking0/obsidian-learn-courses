```js
var m = new Map();
m.set('foo',42);
m.set('bar',11);
m.set({cool:true},'Hello World');

var it1 = m[Symbol.iterator]();
var it2 = m.entries();
var it3 = [1,2,3,4][Symbol.iterator]();
console.log("m:::",m);
// m::: Map(3) { 'foo' => 42, 'bar' => 11, { cool: true } => 'Hello World' }

var i = 0;
do {
  var {value : getValue, done : isDone} = it1.next();
  console.log(`Show it1[${i}]:: `, getValue);
  i++;
}
while (!isDone);
/**
Show it1[0]::  [ 'foo', 42 ]
Show it1[1]::  [ 'bar', 11 ]
Show it1[2]::  [ { cool: true }, 'Hello World' ]
Show it1[3]::  undefined
*/

```