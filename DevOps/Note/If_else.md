# If_else
---
### Ví dụ: 

```js
const isOldEnough = (user) => {
  return user?.age ??= user?.age > 30;
};

const player01 = {
  name: {
    firstName: 'Quang',
    lastName: 'Hai',
    age: 40,
  },
  jobs: ['dev js', 'dev php'],
};

const player02 = {
  firstName: 'Quang',
  lastName: 'Hai',
  age: 40,
};

console.log(isOldEnough(player01)); // Fail
console.log(isOldEnough(player02)); // 40
```

***Giải thích:***
- *Optional Chaining ?.*
```js
const player = {
    details: {
        name: {
            firstName: "Quang",
            lastName: "Hai",
	   age: 20
        }
    },
    jobs: [
        "dev js",
        "dev php"
    ]
}

const playerFirstName = player?.details?.name?.firstName;
```
Check element có tồn tại trong Object để lấy ra giá trị theo cấu trúc từ ngoài vào trong. Xem thêm ở : [Optional chaining (?.) - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining)

- The JavaScript ?? (Nullish Coalescing)
> *isNull ?? "Value"*

```js
let favoriteFruit = null;
let result = favoriteFruit ?? "A";
console.log("result:" , result); // result: A

favoriteFruit = "B";
result = favoriteFruit ?? "A";
console.log("result:" , result); // result: B
```
- Xem thêm ở : [Nullish coalescing operator (??) - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing)

```js
const age_user = 40;
const AGE_REQUIREMENT = 30;

const player01 = {
  name: {
    firstName: 'Quang',
    lastName: 'Hai',
    age: age_user,
  },
  jobs: ['dev js', 'dev php'],
};

const player02 = {
  firstName: 'Quang',
  lastName: 'Hai',
  age: age_user,
};

const isOldEnough = user => {
  return (user?.age > AGE_REQUIREMENT) ?? user?.age
}

console.log(isOldEnough(player01)); // Fail
console.log(isOldEnough(player02)); // True
```

![[if_else-001.png | 300]]

- Không nên viết kiểu:
**Ví dụ 2:**
```js
const validateCreate = (create,isRobo) => {
  if(isRobo) {
    // todo..
  } else {
    // todo..
  }
}
```
- Vì vi phạm Rule SOLID in Develope

**SOLID** is an acronym that stands for five key design principles: 
- **S**ingle responsibility principle - ***Nguyên tắc chức năng đảm nhiệm duy nhất***
- **O**pen-closed principle
- **L**iskov substitution principle
- **I**nterface segregation principle
- **D**ependency inversion principle. 

*SOLID là từ viết tắt của năm nguyên tắc thiết kế chính: nguyên tắc trách nhiệm duy nhất, nguyên tắc đóng mở, nguyên tắc thay thế Liskov, nguyên tắc phân tách giao diện và nguyên tắc đảo ngược phụ thuộc.*

**Ví dụ 2:** sẽ tách ra viết thành

```js
// Xử lý Human
const isHuman = user => {
  // todo..
}

// Xử lý Robo
const validateCreate = create => {
  // todo..
}
```

- Không nên viết điều kiện If quá dài và nhiều điều kiện, mà nên tách riêng 1 biến kiểm tra binary rồi truyền vào điều kiện If

```js
const user = {
  name: 'CR7',
  age: 39,
  blog : 'ttjs'
};

if( user.name == 'CR7' && user.age > 30 && user.blog == 'ttjs')
{
  // todo ...
}

// lv1 
const isValid = user.name == 'CR7' && user.age > 30 && user.blog == 'ttjs'
if(isValid)
{
  // todo ...
}

// lv2
const isOk = user => {
  user.name == 'CR7' && 
  user.age > 30 && 
  user.blog == 'ttjs'
}
if(isOk(user))
{
  // todo ...
}
```
