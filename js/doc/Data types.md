# Data types
Trong JavaScript, trừ `undefined`, toàn bộ các kiểu còn lại đều là `object`. Các kiểu string, number, boolean lần lượt là object dạng String, Number, Boolean. Mảng là object dạng Array, hàm là object dạng Function.

## Có 2 kiểu dữ liệu:
### Primitive Types:
  - Boolean
  - Null
  - Undefined
  - Number
  - String
  - Symbol (new in ECMAScript 6)
### Reference Types:
  - Object
  - Array
  - Function

### Sự khác nhau giữa `Undefined` và `Null`
```js
typeof undefined           // undefined
typeof null                // object

null === undefined         // false
null == undefined          // true
```
