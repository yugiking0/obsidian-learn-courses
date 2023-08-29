# Object.freeze() Object.seal() và Object.preventExtensions() cần hiểu rõ sự khác nhau trong Object Javascript

---
- [Object.freeze()](https://anonystick.com/blog-developer/objectfreeze-objectseal-va-objectpreventextensions-can-hieu-ro-su-khac-nhau-trong-object-javascript-2022010388692105#t-1 "Object.freeze()")
- [Object.preventExtension()](https://anonystick.com/blog-developer/objectfreeze-objectseal-va-objectpreventextensions-can-hieu-ro-su-khac-nhau-trong-object-javascript-2022010388692105#t-2 "Object.preventExtension()")
- [Object.seal()](https://anonystick.com/blog-developer/objectfreeze-objectseal-va-objectpreventextensions-can-hieu-ro-su-khac-nhau-trong-object-javascript-2022010388692105#t-3 "Object.seal()")
- [Kết luận](https://anonystick.com/blog-developer/objectfreeze-objectseal-va-objectpreventextensions-can-hieu-ro-su-khac-nhau-trong-object-javascript-2022010388692105#t-4 "Kết luận")

Làm việc với [Object trong JS](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193) là chúng ta đa số add, update, or delete những phần tử có trong Object. Giả sử, nếu như chúng ta muốn ngăn cho object này không thể thêm được một phần tử mới, hay không thể xóa những phần tử tồn tại đã khai báo, hoặc có thể xóa thì chúng ta phải làm như thế nào?

JavaScript cung cấp ba methods object sau đây để đáp ứng tất cả các trường hợp này một cách dễ dàng, và trong bài viết này chúng ta sẽ giải thích qua ví dụ cụ thể. Đó là 3 phương thức `Object.freeze()`, `Object.preventExtension()` và `Object.seal()`

## Object.freeze()

`Object.freeze()` đóng băng một object chúng ta muốn. Điều đó có nghĩa là một khi chúng ta sử dụng thuộc tính này cho một object thì object này không thể add mới một phần tử, các bạn xem ví dụ sau:

```
const player = {
    name: 'CR7',
    age: 37,
    club: {
        2020: "Juve",
        2021: "MU"
    }
}
// use freeze()
Object.freeze(player);
// update name
player.name = "Cristian CR7"; //Not working...
```

Nếu chúng ta cố tính update thuộc tính `name` trong object `player` thì sẽ thực hiện được. Bởi vì nó đã hoàn toàn đóng băng. Nhưng giả sử chúng ta thử update thuộc tính trong `club` thì sẽ như thế nào?

```
player.club['2020'] = 'VietNam';

console.log(player)
/*
1.  age:  37
2.  club:  {2020:  'VietNam',  2021:  'MU'}
3.  name:  "CR7"
*/
```

Vậy là chúng ta có thể sử đổi thuộc tính trong `club`, điều đó có nghĩa khi bạn sử dụng `Object.freeze()` thì chỉ tác dụng đóng băng ở những thuộc tính cao nhất, còn những thuộc tính được lồng vào nhau vẫn bị thay đổi nếu muốn. Hay chú ý điều đó. Tiếp tục ta đi qua phương thức thứ 2 đó là `Object.preventExtension()`

## Object.preventExtension()

`Object.preventExtension()` method này cho phép một `object` có thể update một thuộc tính nhưng không thể cho phép add thêm một thuộc tính, xem xét ví dụ sau:

Ví dụ 2:

```
const player = {
    name: 'CR7',
    age: 37,
    club: {
        2020: "Juve",
        2021: "MU"
    }
}
// use preventExtension()
Object.preventExtension(player);
// update name
player.name = "Cristian CR7"; //Working...

// Add properties
player.country = "Portugal"; // Not Working....

// delete properties

delete player.age; // Working...
```

Chúng ta nhìn ví dụ thứ 2, và có thể kết luận khi sử dụng `Object.preventExtension()` thì chúng ta có thể update, delete một thuộc tính, nhưng chúng ta không thể add một phần tử mới vào `object` một khi đã sử dụng `preventExtension()`

## Object.seal()

Method cuối cùng mà chúng ta cần biết đến đó là `Object.seal()` cũng giống như `Object.preventExtension()` nhưng việc xóa một thuộc tính thì không được phép. Ví dụ 3:

```
const player = {
    name: 'CR7',
    age: 37,
    club: {
        2020: "Juve",
        2021: "MU"
    }
}
// use preventExtension()
Object.preventExtension(player);
// update name
player.name = "Cristian CR7"; //Working...

// Add properties
player.country = "Portugal"; // Not Working....

// delete properties

delete player.age; // Not Working...
```

Khi sử dụng `Object.seal()` thì chúng ta sẽ không thao tác được việc xóa `delete player.age; // Not Working...`.

## Kết luận

Tùy thuộc vào mỗi hoàn cảnh, mỗi tính chất của mỗi task trong công việc mà chúng ta có thể xem xét để sử dụng phù hợp 3 phương thức `Object.freeze()`, `Object.preventExtension()`và `Object.seal()`. Ngoài ra, nếu như bạn có thêm thời gian vui lòng có thể tham khảo nhiều [Phương thức cần biết trong Object Javascript](https://anonystick.com/blog-developer/object-methods-trong-javascript-moi-developers-can-phai-biet-202005052214193)