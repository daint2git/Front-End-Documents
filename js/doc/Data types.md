# Data types
Trong JavaScript, trừ `undefined`, toàn bộ các kiểu còn lại đều là `object`. Các kiểu string, number, boolean lần lượt là object dạng String, Number, Boolean. Mảng là object dạng Array, hàm là object dạng Function.

## Có 2 kiểu dữ liệu:
### Primitive Types:
- Khi bạn truy cập đến một `Primitive Type`, bạn làm việc trực tiếp với giá trị của nó.
- Giá trị trong bộ nhớ của một kiểu nguyên thủy là giá trị thực của nó (ví dụ: boolean `true`, number `25`). Một kiểu nguyên thủy có thể được lưu trữ trong một lượng bố nhớ cố định có sẵn.
  - Boolean
  - Null
  - Undefined
  - Number
  - String
  - Symbol (new in ECMAScript 6)
- Ví dụ:
```js
const a = 25
let b = a
b = 99
console.log(a) // 25
console.log(b) // 99
```
### Reference Types:
- Khi bạn truy cập đến một `Reference Type`, bạn làm việc với một tham chiếu đến giá trị của nó.
- Một kiểu tham chiếu có thể chứa các giá trị khác. Vì nội dung của một kiểu tham chiếu không thể khớp với số lượng bộ nhớ cố định có sẵn cho một biến, giá trị trong bộ nhớ của một kiểu tham chiếu là tham chiếu chính nó (một địa chỉ bộ nhớ).
  - Object
  - Array
  - Function
- Ví dụ:
```js
const a = {
  c: 25
}
let b = a
b.c = 99
console.log(a) // {c: 99}
console.log(b) // {c: 99}
```

## Chú ý


### null
- Là một giá trị đặc biệt
- Đại diện cho `nothing`, `empty` hay `value unknown`

```js
let age = null
```

### undefined
- Là một giá trị đặc biệt
- Giá trị không được chỉ định `(value is not assigned)`
```js
let x
// hoặc
let x = undefined
// Cả 2 cách khai báo thì biến x đều có giá trị là undefined
```

### Sự khác nhau giữa `undefined` và `null`
```js
typeof undefined           // undefined
typeof null                // object (lỗi trong JS, đúng phải là kiểu null)

null === undefined         // false
null == undefined          // true
```
