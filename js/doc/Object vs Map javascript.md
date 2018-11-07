# Object vs Map javascript

## 

```js
// Object chỉ cho phép lưu trữ key kiểu String hoặc Symbol.
const obj = {
  1: 1,
  x: 1,
  "a b": 2,
  [Symbol(1)]: 3
}
console.log(obj)

// Map cho phép mọi kiểu dữ liệu có thể làm key, kể cả Number, NaN, Function, Object,…
const map = new Map()
map.set(Symbol(1), 1)
      .set(1, 2)
      .set('a', 3)
      .set([2], 4)
      .set({x : 3}, 5)
      .set(() => {}, 6)
      .set(new Set(), 7)
      .set([], 8)
      .set({}, 9)
      .set(false, 10)
      .set(null, 11)
      .set(undefined, 12)
      .set(0, 13)
      .set(NaN, 14)
      .set('', 15)
console.log(map)
```
