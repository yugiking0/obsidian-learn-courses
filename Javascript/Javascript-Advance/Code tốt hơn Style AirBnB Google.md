# Code tốt hơn bằng cách làm theo các phương pháp hay nhất về JavaScript này
---
Cho dù bạn là một nhà phát triển dày dặn kinh nghiệm đang tìm cách tinh chỉnh phong cách viết mã của mình hay một người mới bắt đầu mong muốn nắm bắt các yếu tố cần thiết, bài đăng này là dành cho bạn. Trong hướng dẫn này, chúng tôi sẽ khám phá các phương pháp hay nhất có thể giúp bạn nâng cao kỹ năng JavaScript của mình lên cấp độ tiếp theo.

### **1. Áp dụng một phong cách mã hóa nhất quán**

Bước đầu tiên để cải thiện cách viết mã của bạn là áp dụng một phong cách viết mã nhất quán. Tại sao điều này lại quan trọng? Một phong cách viết mã nhất quán giúp tăng cường khả năng đọc và khả năng bảo trì mã của bạn. Hãy nghĩ về nó như một bản thiết kế cung cấp cấu trúc và sự gắn kết trong code của bạn.

Có một số hướng dẫn phong cách mã hóa phổ biến mà bạn có thể làm theo:

- [JavaScript Idiomatic](https://github.com/rwaldron/idiomatic.js/), dựa trên cộng đồng 
- [Hướng dẫn phong cách JavaScript của Google](https://google.github.io/styleguide/jsguide.html)
- [Hướng dẫn phong cách JavaScript của Airbnb](https://github.com/airbnb/javascript) Chọn một hướng đi phù hợp với phong cách lập trình của bạn và gắn bó với nó trong suốt các dự án của bạn, các dự án của bạn sẽ trông giống như chỉ có một người viết mã ngay cả khi nhiều nhà phát triển khác làm việc trên cùng một dự án. 
	- [[Airbnb JavaScript Style Guide-Vie]] 
	- [[Airbnb JavaScript Style Guide]]

### **2. Đặt tên biến và hàm**

Tiếp theo trong danh sách của chúng tôi là quy ước đặt tên cho các biến, hàm và các cấu trúc mã khác. Điều này không chỉ là về thẩm mỹ hay ngữ nghĩa, mà còn về khả năng đọc code và gỡ lỗi một cách hiệu quả.

Hãy nhớ rằng, trong JavaScript, tiêu chuẩn là sử dụng kiểu camel-case cho các biến và hàm (ví dụ như myVariableName) và sử dụng kiểu Pascal cho các lớp (như MyClassName).

```none
// ❌ Đặt tên biến và hàm không tốt:
let a = 'Nam';
let fn = () => console.log('Xin Chào');

// ✅ Tên biến và hàm được mô tả rõ:
let firstName = 'Nam';
let sayHello = () => console.log('Xin chào');
```

### **3. Sử dụng cú pháp shorthands nhưng nên thận trọng**

Shorthands là một cách tuyệt vời để viết code nhanh hơn và sạch hơn, nhưng hãy cảnh giác vì chúng có thể mang lại kết quả không mong muốn (không hiểu rõ mà sử dụng). Để ngăn chặn điều đó, hãy đảm bảo luôn kiểm tra tài liệu, tìm các ví dụ có liên quan và kiểm tra kết quả.

```none
// ❌ Khai báo hàm truyền thống:
function square1 (num) {
  return num * num
}
// ✅ Sử dụng arrow functions (shorthand):
const square2 = num => num * num

// ❌ Code rất dài và rối:
let x

if (y) {
  x = y
} else {
  x = 'default'
}
// ✅ Một cách ngắn gọn hơn với kết quả tương tự bằng cách sử dụng logic OR:
let x = y || 'default'
```

### **4. Thêm comments có ý nghĩa vào code của bạn**

Comments về code của bạn giống như để lại mẩu bánh mì cho bản thân tương lai của bạn hoặc các nhà phát triển khác. Nó giúp hiểu được luồng và mục đích code của bạn, đặc biệt là khi làm việc trên các dự án nhóm.

Tuy nhiên, hãy nhớ giữ cho nhận xét của bạn ngắn gọn và súc tích và chỉ bao gồm thông tin chính.

```none
// ❌ comments 1 cách quá mức:
function hashIt(data) {
  // Khai báo hash
  let hash = 0;

  // Lấy chiều dài của chuỗi
  const length = data.length;

  // Lặp qua mỗi kí tự
  for (let i = 0; i < length; i++) {
    // Lấy mã của kí tự
    const char = data.charCodeAt(i);
    // Gán giá trị cho hash
    hash = ((hash << 5) - hash) + char;
    // Chuyển thành định dạng số nguyên 32 bit
    hash &= hash;
  }
}

// ✅ comments 1 cách phù hợp:
function hashIt(data) {
  let hash = 0;
  const length = data.length;

  for (let i = 0; i < length; i++) {
    const char = data.charCodeAt(i);
    hash = ((hash << 5) - hash) + char;

    // Chuyển thành định dạng số nguyên 32 bit
    hash &= hash;
  }
}
```

**Những đoạn code tốt thì đa số tự nó đã là tài liệu rồi.**

### **5. Thực hiện theo nguyên tắc SoC**

Để giữ cho mọi thứ đơn giản và có tổ chức, tốt nhất không nên sử dụng JavaScript để thêm style trực tiếp. Mỗi phần của ứng dụng nên được phân chia thành các thành phần độc lập (SoC). Thay vào đó, hãy sử dụng classList để thêm và xóa các lớp và thêm style bằng CSS. Bằng cách này, CSS thực hiện tất cả các style và JavaScript xử lý tất cả các chức năng khác của ứng dụng của bạn. Để giữ cho nó ngắn gọn: CSS nên làm CSS nhưng JavaScript không nên làm CSS.

```none
// ❌ Tránh dùng JavaScript để styling:
let element = document.getElementById('my-element')
element.style.color = 'red'

// ✅ Thay đổi style bằng cách thêm/xóa classes:
let element = document.getElementById('my-element')
element.classList.add('my-class')
```

### **6. Tránh các biến toàn cục**

Khi khai báo các biến cục bộ, hãy sử dụng let và const để ngăn chặn việc ghi đè các biến toàn cục. Cả hai đều tạo ra các biến cục bộ có phạm vi khối, nhưng sự khác biệt chính là let có thể được khai báo lại trong khi const không thể. Vì vậy, hãy sử dụng chúng một phù hợp theo nhu cầu cụ thể của bạn.

```none
// ❌ Dùng var để khai báo biến:
var x = 1

// ✅ Hãy dùng let và const để khai báo biến:
let x = 1
const y = 2
```

### **7. Sử dụng for... of Thay cho for Loops**

Các for... of câu lệnh, được giới thiệu trong ECMAScript 6, là một giải pháp thay thế hiệu quả hơn cho các vòng lặp truyền thống. Nó đi kèm với một bộ lặp tích hợp, loại bỏ việc phải xác định biến và chiều dài. Điều này làm cho mã của bạn sạch hơn và nâng cao hiệu suất của nó.

```none
// ❌ Sử dụng for loop:
let cities = ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
for (let i = 0; i < cities.length; i++) {
  const city = cities[i]
  console.log(city)
}

// ✅ Sử dụng for of loop:
let cities = ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix']
for (const city of cities) {
  console.log(city)
}
```

### **8. Một hàm chỉ nên làm một việc**

Các hàm phải độc lập để chúng có thể được gọi từ bất kỳ mô-đun nào, tăng cường khả năng tái sử dụng.

```none
// ❌ Làm nhiều việc trong một hàm:
function calculateOrderTotal (order) {
  let total = 0

  for (let i = 0; i < order.items.length; i++) {
    total += order.items[i].price * order.items[i].quantity
  }

  let tax = total * 0.07

  return total + tax
}

// ✅ Mỗi hàm làm một việc cụ thể:
function calculateSubTotal (items) {
  let total = 0

  for (let i = 0; i < items.length; i++) {
    total += items[i].price * items[i].quantity
  }

  return total
}

function calculateTax (total) {
  return total * 0.07
}

function calculateOrderTotal (order) {
  let subTotal = calculateSubTotal(order.items)
  let tax = calculateTax(subTotal)

  return subTotal + tax
}
```

### **9. Xử lý Promises một cách chính xác**

Trong thế giới không đồng bộ của JavaScript, Promises là một khái niệm phổ biến. Tuy nhiên, chúng phải được xử lý đúng cách để ngăn chặn hành vi không mong muốn. JavaScript cung cấp _try...catch_ được sử dụng để xử lý các ngoại lệ có thể phát sinh trong quá trình thực thi mã không đồng bộ của bạn.

Bằng cách này, bạn đảm bảo các lỗi được phát hiện và xử lý thích hợp.

```none
// ❌ Không xử lí đúng promises:
async function fetchData () {
  const response = await fetch('https://jsonplaceholder.typicode.com/todos/1')
  const data = await response.json()

  return data
}

// ✅ Xử lí promises một cách chính xác:
async function fetchData () {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos/1')
    const data = await response.json()

    return data
  } catch (error) {
    // Handle your errors here...
    throw new Error(error)
  }
}
```

### **10. Tránh lồng quá nhiều trong mã của bạn**

Đây là một trong những sai lầm phổ biến nhất mà người mới bắt đầu mắc phải, đó là lồng hết khối này đến khối khác, bên trong một vòng lặp khác... Đó là một mớ hỗn độn và việc gỡ lỗi loại mã này có thể khá khó khăn và bất lực, và khi các lập trình viên khác nhìn thấy nó, cũng sẽ dễ gây nhầm lẫn chúng, và có thể nhìn bạn một cách "Không chuyên nghiệp".

```none
// ❌ Các khối lồng nhau quá nhiều và không sử dụng return
function checkNumber (num) {
  if (num > 0) {
    console.log('Number is positive.')
  } else {
    if (num < 0) {
      console.log('Number is negative.')
    } else {
      console.log('Number is zero.')
    }
  }
}

// ✅ Sử dụng return và tách biệt hợp lí
function checkNumber (num) {
  if (num > 0) {
    console.log('Number is positive.')
    return
  }

  if (num < 0) {
    console.log('Number is negative.')
    return
  }

  console.log('Number is zero.')
}
```

### **11. Tối ưu hóa cho các vòng lặp**

Có một cách viết phổ biến cho các vòng lặp trong JavaScript, đây là một ví dụ về cách hầu hết các nhà phát triển viết vòng lặp trong JavaScript

```none
var languages = ['Python', 'JavaScript', 'C++', 'Ruby'];
for(var i=0;i<languages.length;i++){
  codeIn(languages[i]);
}
```

Đối với một mảng nhỏ như thế này, vòng lặp này có hiệu quả cao và chạy mà không gặp bất kỳ vấn đề gì, nhưng khi nói đến các bộ dữ liệu lớn hơn và một mảng có hàng nghìn chỉ mục, cách tiếp cận này có thể làm chậm quá trình vòng lặp của bạn.

Điều xảy ra là khi bạn chạy, độ dài của mảng sẽ được tính toán lại mỗi khi vòng lặp chạy và mảng của bạn càng dài thì càng kém hiệu quả khi tính toán lại độ dài mảng mỗi khi vòng lặp chạy.

Thay vào đó, những gì bạn nên làm là lưu trữ độ dài mảng trong một biến khác và sử dụng biến đó trong các vòng lặp của bạn, ví dụ:

```none
var languages = ['Python', 'JavaScript', 'C++', 'Ruby'];
var langCount = languages.length;
for(var i=0;i<langCount;i++){
  codeIn(languages[i]);
}
```

Với tinh chỉnh này, thuộc tính 'length' chỉ được truy cập một lần và chúng tôi sử dụng giá trị được lưu trữ cho các lần lặp tiếp theo. Điều này cải thiện hiệu suất, đặc biệt là khi xử lý các tập dữ liệu lớn.

### **Kết thúc**

Hãy nhớ rằng, những điều này không chỉ là viết mã sạch hơn và có cấu trúc tốt hơn. Chúng cũng là về việc tạo ra mã dễ bảo trì và gỡ lỗi hơn.

Phát triển phần mềm là một quá trình liên tục. Tạo mã phát triển chỉ là bước đầu tiên của vòng đời phần mềm. Điều quan trọng là phải liên tục theo dõi, gỡ lỗi và cải thiện mã của bạn trong giai đoạn sản xuất.

Vì vậy, bạn đã có nó, 11phương pháp hay nhất về JavaScript để nâng cao trình độ của bạn. Cho dù bạn là người mới bắt đầu hay nhà phát triển có kinh nghiệm, việc áp dụng những thói quen này sẽ giúp bạn viết mã tốt hơn, hiệu quả hơn và có thể duy trì. Code vui vẻ!