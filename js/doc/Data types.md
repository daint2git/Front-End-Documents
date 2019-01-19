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
- Là một primitive type
- Có giá trị đặc biệt
- Có nghĩa là một biến đã được khai báo và gán một giá trị là `empty`, `nothing` `(value is assigned)`
```js
let age = null

typeof null // object (lỗi trong JS, đúng phải là kiểu null)
```

### undefined
- Là một primitive type
- Có giá trị đặc biệt
- Có nghĩa là một biến đã được khai báo nhưng chưa được gán một giá trị `(value is not assigned)`
```js
let x // undefined
// hoặc
let x = undefined

typeof undefined // undefined

null === undefined // false
null == undefined // true
```
- Đối với Reference type, khi truy suất `key` hoặc `index` không tồn tại thì sẽ trả về `undefined`
```js
const obj = {}
console.log(obj.name) // undefined

const arr = [1, 2, 3]
console.log(arr[3]) // undefined
```
