
# Methods trong JavaScript mọi developers cần phải biết
---
- [Object javascript là gì?](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-1 "Object javascript là gì?")
- [Object.create()](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-2 "Object.create()")
- [Object.keys()](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-3 "Object.keys()")
- [Object.values()](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-4 "Object.values()")
- [Object.entries()](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-5 "Object.entries()")
- [Object.assign()](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-6 "Object.assign()")
- [Object.freeze()](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-7 "Object.freeze()")
- [Object.seal()](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-8 "Object.seal()")
- [Kết luận và rút ra bài học](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193#t-9 "Kết luận và rút ra bài học")

---
**Object javascript là gì? Thật ra hầu hết mọi thứ trong javascript đều là object. Nhưng ở bài post này thì, chúng ta sẽ tìm hiểu những method object được sử dụng nhiều và rộng rãi nhất, đến nỗi dự án nào cũng phải sử dụng đến. Bên cạnh đó còn kể đến những** [**"Array method in javascript"**](https://anonystick.com/blog-developer/javascript-developer-javascript-nen-biet-nhung-method-arrays-nao-trong-javascript-x0ZB3R6E) 

  

## Object javascript là gì?

  

Để hiểu hết tối đa bài viết này thì trước tiên bạn phải hiểu "Object javascript là gì?" và hơn hết bạn phải hiểu cách creating, modifying, và working một object. Ở những hướng dẫn trước của tipjs, đã nói nhiều về Object bạn có thể xem qua. Ở bài trước **["Array method in javascript"](https://anonystick.com/blog-developer/javascript-developer-javascript-nen-biet-nhung-method-arrays-nao-trong-javascript-x0ZB3R6E)  chúng tôi đã nói rất nhiều về cách sử dụng method của Array.**

  

Object trong javascript là một collection `key/value`. Trong đó các giá trị có thể bao gồm các properties và methods và có thể chứa tất cả các loại dữ liệu JavaScript khác, chẳng hạn như `String`, `Number` và `Booleans`.

  

Object có nhiều method được tích hợp hữu ích mà chúng ta có thể sử dụng và truy cập để làm việc với các Object riêng lẻ một cách đơn giản. Hướng dẫn củ bài post này sẽ đi qua các method Object tích hợp quan trọng, và kèm theo đó là những ví dụ minh hoạ cho từng trường hợp cụ thể khi sử dụng object.

  

## Object.create()

  

`Object.create()` là một method được sử dụng để tạo ra một Object mới và dùng object đó để mở rộng hơn cho một object, chúng ta cùng xem một ví dụ dưới đây.

// Initialize an object with properties and methods
const job = {
    position: 'cashier',
    type: 'hourly',
    isAvailable: true,
    showDetails() {
        const accepting = this.isAvailable ? 'is accepting applications' : "is not currently accepting applications";

        console.log(`The ${this.position} position is ${this.type} and ${accepting}.`);
    }
};

// Use Object.create to pass properties
const barista = Object.create(job);

barista.position = "barista";
barista.showDetails();

Output
The barista position is hourly and is accepting applications.

Trên đó ta cũng thấy là chúng ta có thể thay đổi gia trị của một properties của Object mới mà ta vừa sử dụng `Object.create()` .

  

## Object.keys()

  

`Object.keys()` là một method dùng để tạo ra một Array với tất cả key của một Object. Và theo kinh nghiệm của tipjs thì có lẽ đây là một method rất hay. Vì tipjs đã sử dụng rất nhiều.

// Initialize an object
const employees = {
    boss: 'Michael',
    secretary: 'Pam',
    sales: 'Jim',
    accountant: 'Oscar'
};

// Get the keys of the object
const keys = Object.keys(employees);

console.log(keys);

Output
["boss", "secretary", "sales", "accountant"]

Sau khi chúng ta đã có một Array từ sử dụng `Object.keys()` thì chúng ta có thể tiếp tục sử dụng "Array method javascript" để phát triển thêm như iterate:

// Iterate through the keys
Object.keys(employees).forEach(key => {
    let value = employees[key];

     console.log(`${key}: ${value}`);
});

Output

boss: Michael
secretary: Pam
sales: Jim
accountant: Oscar

## Object.values()

  

`Object.values()` là một method ngược lại với `Object.keys()` thì nó tạo một new Array với tất cả những giá trị của một object.

// Initialize an object
const session = {
    id: 1,
    time: `26-July-2018`,
    device: 'mobile',
    browser: 'Chrome'
};

// Get all values of the object
const values = Object.values(session);

console.log(values);
Output
[1, "26-July-2018", "mobile", "Chrome"]

## Object.entries()

  

`Object.entries()` là một method tạo một nested array với key/value của một Object.

// Initialize an object
const operatingSystem = {
    name: 'Ubuntu',
    version: 18.04,
    license: 'Open Source'
};

// Get the object key/value pairs
const entries = Object.entries(operatingSystem);

console.log(entries);
Output
[
    ["name", "Ubuntu"]
    ["version", 18.04]
    ["license", "Open Source"]
]

## Object.assign()

  

`Object.assign()` là một method dùng để sao chép những giá trị từ một object này sang một object khác. Ở ví dụ dưới đây, chúng ta sử dụng `Object.assign()` để merge chúng lại với nhau:

// Initialize an object
const name = {
    firstName: 'Philip',
    lastName: 'Fry'
};

// Initialize another object
const details = {
    job: 'Delivery Boy',
    employer: 'Planet Express'
};

// Merge the objects
const character = Object.assign(name, details);

console.log(character);
Output
{firstName: "Philip", lastName: "Fry", job: "Delivery Boy", employer: "Planet Express"}

Nhưng điều quang trọng là khi sử dụng `Object.assign()` thì đó là một shallow-cloning. Xem thêm ["shallow-cloning in javascript"](https://anonystick.com/blog-developer/objectassign-co-the-lam-nhung-gi-voi-object-javascript-PPqgJNrs.jsx). Ngoài ra thì merge một object thì chúng ta có thể sử dụng `(...)`, xem tiếp ví dụ nếu bạn còn hứng thú:

// Initialize an object
const name = {
    firstName: 'Philip',
    lastName: 'Fry'
};

// Initialize another object
const details = {
    job: 'Delivery Boy',
    employer: 'Planet Express'
};

// Merge the object with the spread operator
const character = {...name, ...details}

console.log(character);
Output
{firstName: "Philip", lastName: "Fry", job: "Delivery Boy", employer: "Planet Express"}

Và [spread syntax](https://anonystick.com/blog-developer/5-cach-su-dung-spread-operator-trong-javascript-2020040666007774) cũng là một shallow-cloning. Xem thêm [Sự khác nhau giữa Shallow copying và Deep copying trong object javascript](https://anonystick.com/blog-developer/phong-van-su-khac-nhau-giua-shallow-copying-va-deep-copying-trong-object-javascript-2019112823755023)

  

## Object.freeze()

  

`Object.freeze()` dùng để ngăn chặn một hành vi sử đổi thuộc tính giá trị của một object, ngoài ra cũng có thể ngăn chặn một hành vi như xoá or add thêm thuộc tính.

// Initialize an object
const user = {
    username: 'AzureDiamond',
    password: 'hunter2'
};

// Freeze the object
const newUser = Object.freeze(user);

newUser.password = '*******';
newUser.active = true;

console.log(newUser);
Output
{username: "AzureDiamond", password: "hunter2"}

Để hiểu `Object.freeze()` không phải là một ví dụ này là bạn có thể hiểu được những tipjs gợi ý bạn có thể đọc thêm về bài viết này: [How can I deep freeze an object in JavaScript?](https://anonystick.com/blog-developer/how-can-i-deep-freeze-an-object-in-javascript-2020041412698143)

  

## Object.seal()

  

`Object.seal()` thì hơi ngược lại với `Object.freeze()` đó là dùng để ngăn chặn hành vi add thêm một new properties nhưng lại cho phép modification những thuộc tính đã tồn tại trước đó. Ví dụ:

// Initialize an object
const user = {
    username: 'AzureDiamond',
    password: 'hunter2'
};

// Seal the object
const newUser = Object.seal(user);

newUser.password = '*******';
newUser.active = true;

console.log(newUser);
Output
{username: "AzureDiamond", password: "*******"}

Đến đây, chúng tôi khuyên bạn tiếp tục xem thêm bài viết về ["Sự khác nhau Object.freeze() và Object.seal() trong JavaScript"](https://anonystick.com/blog-developer/golobal-const-va-objectfreeze-trong-javascript-2019042650544299)

  

## Kết luận và rút ra bài học

  

Điều tuyệt vời nhất là mang đến cho bạn một cách nhìn, hiểu và sử dụng các method object trong javascript một cách hiệu quả và đầy tinh tế. Mỗi ví dụ, chúng tôi cố gắng truyền đến những bài viết để đi sâu hơn nữa. Bạn đừng bỏ qua nó một cách lãng phí. Vì mỗi bài viết đều chứa đựng nhiều kiến thức hơn nữa. Ngoài ra, bạn cũng nên tìm hiểu về **["Array method in javascript"](https://anonystick.com/blog-developer/javascript-developer-javascript-nen-biet-nhung-method-arrays-nao-trong-javascript-x0ZB3R6E).**

Resource: [digitalocean.com](https://www.digitalocean.com/community/tutorials/how-to-use-object-methods-in-javascript)