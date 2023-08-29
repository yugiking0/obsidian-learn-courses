# The Most Useful Features in the Latest Javascript (Since ES6)
---
**Table of contents:**

- [ES6 (ECMAScript 2015)](https://www.blog.duomly.com/the-most-useful-features-in-the-latest-javascript-since-es6/#es6-ecmascript-2015)
  - [ES7 (ECMAScript 2016)](https://www.blog.duomly.com/the-most-useful-features-in-the-latest-javascript-since-es6/#es7-ecmascript-2016)
  - [ES8 (ECMAScript 2017)](https://www.blog.duomly.com/the-most-useful-features-in-the-latest-javascript-since-es6/#es8-ecmascript-2017)
  - [ES9 (ECMAScript 2018)](https://www.blog.duomly.com/the-most-useful-features-in-the-latest-javascript-since-es6/#es9-ecmascript-2018)
  - [Conclusion](https://www.blog.duomly.com/the-most-useful-features-in-the-latest-javascript-since-es6/#conclusion)

In June 2015, after six years of break, there was a significant update of Javascript which brought lots of new features. Since that time every year we a new edition with a set of new features which are supposed to help developers and make our work more efficient. To help you keep track on what is going on with Javascript versions, I’m going to list the most useful features grouped by the edition and add some code examples for a better overview.

### ES6 (ECMAScript 2015)

###### 1. Arrow functions (=>)

An arrow function is a shorthand for function syntax (=>). It brings into development two main facilities for developers. First of all arrow function help us to avoid using .bind() or other methods used to apply properly this because arrow function shares the same lexical this as their surrounding. Another advantage of using arrow function is that our code looks much better, it’s not so verbose like with regular functions.

```javascript
// traditional function expression
var numbers = [2, 6, 40];
var twiceNum = numbers.map(function(number) { return number*2 })
// arrow functional
var numbers = [2, 6, 40];
var twiceNum = numbers.map((number) => number*2);
// lexical this
var greenBtn = document.getElementById(‘greenBtn’);
greenButton.addEventListener(‘click’, function() {
 this.style.backgroundColor = “red”; // no more binding
})
```

###### 2. Classes

For every fun of Object-Oriented Programming, classes may be a very useful feature. They made it super easy to write code based on a class pattern. Classes support prototype inheritance, constructors, super calls and instance and static methods. Let’s take a look at how easy it is now to create the class:

```javascript
// Class
class Person {
 constructor(firstName, lastName, age) {
   this.firstName = firstName;
   this.lastName = lastName;
   this.age = age;
 }
sayHi() {
   return ‘Hi, my name is ${firstName}. Nice to meet you.’;
 }
}
```

###### 3. Template strings

Probably in the example above you realized I didn’t use plus sign to add variable to the string. ES6 implemented a really useful feature called template strings. It allows us to implement variables into the string without aborting it. It’s enough to put the variable into curly brackets and place $ sign in front of is. It’s also important to put the string into back-ticks around. It may be very useful while constructing API requests. Let’s take a look at the code:

```javascript
var name = ‘Peter’, city = ‘London’;
// Before ES6
var greeting = "Hello, my name is " + name + ". I am from " + city + ".";
// After ES6 
var greeting = ‘Hello, my name is ${name}. I’m from ${city}.‘
```

Smart and easy, right?

###### 4. Let and Const

ES6 implemented two new keywords: const and let. Both of them are used to declare variables. Let works very similar to var, but the variable has block scope, so it’s available only in the block of code where was declared. Const is used to declare constants. It works like let, but you need to assign value while declaring const. Let’s take a look at code examples:

```javascript
// Let — variable is available only in the block of code
function calculate(x) {
 var y = 0;
 if (x > 10) { 
// let y is only available in this block of code
   let y = 30;
   return y;
 }
 return y;
}
```

###### 5. Promises

ECMAScript 2015 creators gave us also standardized Promise implementation, which is crazy useful, while we are using asynchronous programming very often right now. We don’t have to worry about callback hell anymore. The promise always is in one of three states: pending, fulfilled, or rejected. You also have .then() method to react if a promise is resolved or .catch() method to check why it’s rejected. Let’s take a look at the code:

```javascript
const checkResult = () => new Promise(resolve, reject) => {
setTimeout(resolve, 500)} 
checkResult()
 .then((result) => { console.log(result); }) 
 .catch((error) => { console.log(error); })
```

### ES7 (ECMAScript 2016)

###### 1. Array.prototype.includes

In ES7 there is a new method for arrays appeared. .includes() method made it easier to check if a certain value is in the array. Previously developers used indexOf and had to create an additional function to check this, now we can use .includes(), and it will return true if an array has specific element and false if not. Let’s take a look at a code example:

```javascript
var fruits = ['banana', 'apple', 'grape', 'nut', 'orange'];
var favoriteFruit = 'banana';
// Before ES7
function isFruit(fruit) {
 if (fruits.indexOf(fruit) !== -1) {
   return true;
 } else {
   return false;
 }
}
isFruit(favoriteFruit); // returns true
// After ES7
fruits.includes(favoriteFruit); // returns true
```

###### 2. Exponentiation Operator

It’s mostly important for developers working on more advanced Math operations, 3D, VR, or data visualization. Previously, this could be done by loop, Math.pow() or recursive function, now the way is much less complicated. Let’s take a look at some code:

```javascript
// Before ES7 (loop case) 
function calculate(num, exponent) { 
   var res = 1; 
   for (var i = 0; i < exponent; i++) { 
     res *= num; 
   } 
   return res;
}
// After ES7
const calculate = (num, exponent) => num ** exponent;
```

Easy, right?

### ES8 (ECMAScript 2017)

###### 1. Object.values() and Object.entries()

Object.values() method implemented in ECMAScript2017 allows us to take all values of the object and returns them as an array. Another useful feature about Object in ES8 is Object.entries() method. It allows us to take all the entries and display them as an array of arrays. Let’s take a look at some code:

```javascript
var person = {
 name: ‘Jenny’,
 age: 24,
 country: ‘UK’,
 city: ‘London’,
}
// Object.values()
var arrJenny = Object.values(person); // returns [‘Jenny’, 24, ‘UK’, ‘London’];
// Object.entries()
var arrJennyEntries = Object.entries(person); // returns [[‘name’, ‘Jenny’], [‘age’, 24], [‘country’, ‘UK’], [‘city’, ‘London’]];
```

###### 2. String.prototype.padEnd() and String.prototype.padStart()

There is also something new for strings in ES8. While your string doesn’t have enough length, you can use one of the new methods to add a few characters until it will reach the desired length. padEnd() will add selected character (or space by default) at the end of the string and padStart() at the beginning. Let’s check how it works on the example:

```javascript
var string = ‘Alice’; 
// padStart() — we assume our string needs to have 10 characters 
string.padStart(10, ‘o’); // returns ‘oooooAlice’
// padEnd() 
string.padEnd(10, ‘o’); // returns ‘Aliceooooo’;
```

###### 3. Async function (async/await)

In ES8 creators gave us another alternative to callbacks and Promise for asynchronous programming, it’s async/await function. Async function defines an asynchronous function, and it returns a Promise which will be resolved or rejected. There is also .await() operator which is used inside an async function, and it waits for a Promise. Async functions provide us more friendly syntax. Let’s take a look at some code:

```javascript
function delayResult() {
 return new Promise(resolve => {
   setTimeout(() => {
     resolve(‘Done’);
   }, 5000)
 })
}
async function getResult() {
 var result = await delayResult();
 return result;
}
getResult();
```

### ES9 (ECMAScript 2018)

###### 1. Asynchronous iteration

With ES9 creators added asynchronous iteration, which means you can declare asynchronous loops, by using await. But it may be used only if data is from synchronous source, so we can’t iterate asynchronously iterate data from https fetch. Let’s take a look at the code example:

```javascript
for await (let book of books) { 
 console.log(book) 
};
```

###### 2. Rest operator

ECMAScript2019 also brings new behavior for rest operator. Now, it can copy the remaining object key-values pairs which weren’t mentioned in the object literal into operand. The rest operator should be used at the end; otherwise, it will cause an error. Also, it’s possible to use it inside a function and get needed property. Let’s take a look a the example to understand it better:

```javascript
const fruits = { orange: 1, apple: 10, banana: 4, } 
const { orange, …rest } = fruits; 
console.log(rest); // { apple: 10, banana: 4 };
// in the function
function getFruits(apple, …rest) { 
 return rest.banana;
}
```

###### 3. Promise.prototype.finally

Another useful feature which came with ES9 is .finally(), another callback for Promise, which is always executed, no matter if .then() or .catch() were called. It may be useful if you need to call some action after Promise, no matter if it was successful or not. Let’s take a look at the code:

```javascript
const checkResult = () => new Promise(resolve, reject) => {setTimeout(resolve, 500)}
checkResult() 
 .then((result) => { console.log(result); }) 
 .catch((error) => { console.log(error); }) 
 .finally(() => { console.log(‘Promise finished!’) })
```

### Conclusion

We went through the most useful, not every, updates of Javascript since ES6 in 2015. There are a lot of changes you may not know until today. Remember, that it’s very important to use it to make your programming knowledge updated and your code smarter, shorter, and cleaner. Also, join Javascript Course to master your knowledge.

Thank you for reading, Anna from Duomly

## Related readings 📖

[How to pass the machine learning interview?](https://www.blog.duomly.com/how-to-pass-machine-learning-interview/)

[What do you need to learn to become a front-end developer?](https://www.blog.duomly.com/what-do-you-need-to-learn-to-become-a-front-end-developer/)

[20 Essential Python Tips and Tricks You Should Know](https://www.blog.duomly.com/20-essential-python-tips-and-tricks-you-should-know/)