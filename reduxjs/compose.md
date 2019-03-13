```js
// https://github.com/reduxjs/redux/blob/master/src/compose.js
// const compose = (...funcs) => {
//   if (funcs.length === 0) {
//     return arg => arg
//   }

//   if (funcs.length === 1) {
//     return funcs[0]
//   }

//   return funcs.reduce((a, b) => (...args) => a(b(...args)))
// }

// https://github.com/acdlite/recompose/blob/master/src/packages/recompose/compose.js
const compose = (...funcs) => funcs.reduce((a, b) => (...args) => a(b(...args)), arg => arg)

const add10 = result => result + 10

const mul5 = result => result * 5

const div2 = result => result / 2

const sub1 = result => result - 1

// cách sử dụng hàm compose
const res1 = compose(
  add10,
  mul5,
  div2,
  sub1,
)

// cách thực hiện của hàm compose
const res2 = (...args) =>
  ((...args) => ((...args) => add10(mul5(...args)))(div2(...args)))(sub1(...args))
  
// cách thực hiện của hàm compose (đơn giản khi chỉ có một tham số đầu vào)
const res3 = args3 => (args2 => (args1 => add10(mul5(args1)))(div2(args2)))(sub1(args3))

// một cách sử dụng khác để có kết quả tương tự như hàm compose
const res4 = (...args) => add10(mul5(div2(sub1(...args))))

console.log(res1(7)) // 25
console.log(res2(7)) // 25
console.log(res3(7)) // 25
console.log(res4(7)) // 25
```
