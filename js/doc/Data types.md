# Data types
Trong JavaScript, trừ `undefined`, toàn bộ các kiểu còn lại đều là `object`. Các kiểu string, number, boolean lần lượt là object dạng String, Number, Boolean. Mảng là object dạng Array, hàm là object dạng Function.

## Có 2 kiểu dữ liệu:
### Primitive Types:
Giá trị trong bộ nhớ của một kiểu nguyên thủy là giá trị thực của nó (ví dụ: boolean `true`, number `25`). Một kiểu nguyên thủy có thể được lưu trữ trong một lượng bố nhớ cố định có sẵn.
  - Boolean
  - Null
  - Undefined
  - Number
  - String
  - Symbol (new in ECMAScript 6)
Ví dụ:
```js
const a = 25
let b = a
b = 99
console.log(a) // 25
console.log(b) // 99
```
### Reference Types:
Một kiểu tham chiếu có thể chứa các giá trị khác. Vì nội dung của một kiểu tham chiếu không thể khớp với số lượng bộ nhớ cố định có sẵn cho một biến, giá trị trong bộ nhớ của một kiểu tham chiếu là tham chiếu chính nó (một địa chỉ bộ nhớ).
  - Object
  - Array
  - Function
Ví dụ:
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

### Sự khác nhau giữa `Undefined` và `Null`
```js
typeof undefined           // undefined
typeof null                // object

null === undefined         // false
null == undefined          // true
```
