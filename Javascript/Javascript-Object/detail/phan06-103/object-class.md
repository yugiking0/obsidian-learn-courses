![Object](Javascript/Javascript-Object/detail/phan06-103/images/code-object.png 'Object')

![Function Constructor](Javascript/Javascript-Object/detail/phan06-103/images/code-constructor.png 'Function Constructor')

![Class](Javascript/Javascript-Object/detail/phan06-103/images/code-class.png 'Class')

```js
// Object
const cssCourse = {
  name: 'CSS',
  price: 150,

  getName: function () {
    return this.name;
  },
  setName: function (newName) {
    this.name = newName;
  },
};

console.log('O.Course Name: ', cssCourse.getName());
// Course Name:  CSS
cssCourse.setName('Python');
console.log('O.Course Name: ', cssCourse.getName());
// Course Name:  Python

// Function Constructor
function fcCourse(name, price) {
  this.name = name;
  this.price = price;

  this.getName = function () {
    return this.name;
  };
  this.setName = function (newName) {
    this.name = newName;
  };
}
var jsCourse = new fcCourse('JavaScript', 1000);
console.log('FC Course Name: ', jsCourse.getName());
// Course Name:  JavaScript
jsCourse.setName('PHP');
console.log('FC Course Name: ', jsCourse.getName());
// Course Name:  PHP

// Class
class ClassCourse {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  getName() {
    return this.name;
  }
  setName(newName) {
    this.name = newName;
  }
  getPrice() {
    return this.price;
  }

  run() {
    let isSucceeded = false;
    if (true) {
      isSucceeded = true;
    }
  }
}

var jsCourse = new ClassCourse('JavaScript', 1000);
console.log('Course Name: ', jsCourse.getName());
// Course Name:  CSS
jsCourse.setName('Python');
console.log('Course Name: ', jsCourse.getName());
// Course Name:  Python
```
