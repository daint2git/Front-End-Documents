```js
console.log(isPromise({ then: function() {} })) // true
console.log(isPromise(null)) // false
console.log(isPromise({})) // false
console.log(isPromise({ then: true })) // false
console.log(
  isPromise(
    new Promise((resolve, reject) => {
      resolve(1)
    }),
  ),
) // true
console.log(
  isPromise(
    new Promise((resolve, reject) => {
      reject(1)
    }),
  ),
) // true

function isPromise(obj) {
  return (
    !!obj &&
    (typeof obj === 'object' || typeof obj === 'function') &&
    typeof obj.then === 'function'
  )
}
```
