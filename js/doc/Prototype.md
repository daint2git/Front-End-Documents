# Prototype
- Trong JavaScript, trừ undefined, toàn bộ các kiểu còn lại đều là object. Các kiểu string, number, boolean lần lượt là object dạng String, Number, Boolean. Mảng là object dạng Array, hàm là object dạng Function. Prototype của mỗi object chính là cha của nó, cha của String là String.prototype, cha của Number là Number.prototype, của Array là Array.prototype.
- Array, Number hay String có cha là Object, do đó chúng đều có các hàm như `constructor, hasOwnProperty, toString` thuộc về của Object.prototype.

## Thêm thuộc tính và phương thức cho prototype
```js
const str = 'abc'
String.prototype.hello = 'Hello JavaScript'
String.prototype.print = value => value

console.log(str) // "abc"
console.log(str.hello) // "Hello JavaScript"
console.log(str.print(999)) // 999
```
