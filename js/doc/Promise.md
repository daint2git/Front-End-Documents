# Promise

## Định nghĩa
`Promise`: Là một đối tượng đặc biệt dùng cho các xử lý bất đồng bộ. Nó đại diện cho một xử lý bất đồng bộ và chứa kết quả cũng như các lỗi xảy ra từ xử lý bất đồng bộ đó.

## States
- pending
- fulfilled
- rejected

## Prototype
#### Properties
- constructor

#### Methods
- then
- catch
- finally

## Static methods
- `Promise.resolve(value)`: Trả về một promise resolved (hoàn thành) với một giá trị cụ thể.
- `Promise.reject(reason)`: Trả về một promise rejected (lỗi) với một lỗi cụ thể.
- `Promise.all(iterable of multiple promises)`
  - Nhận vào một mảng các promise hoặc cũng có thể là non-promise (number, boolean, .etc).
  - Trả về một promise mới.
  - Chờ tất cả các promise trong mảng resolved, kết quả của promise mới này là một mảng chứa kết quả của các promise theo đúng thứ tự.
  - 1 promise bất kì rejected, kết quả của promise mới này được trả về ngay lập tức lỗi của promise rejected đó, các promise khác vẫn tiếp tục thực thi nhưng kết quả bị bỏ qua.
  - Thực thi promise dạng parallel.
- `Promise.race(iterable of multiple promises)`: 
  - Nhận vào một mảng các promise hoặc cũng có thể là non-promise (number, boolean, .etc).
  - Trả về một promise mới.
  - Kết quả của promise mới là kết quả của promise bất kì đầu tiên resolved hoặc rejected.
- `Promise.allSetted(iterable of multiple promises)`: 
  - Nhận vào một mảng các promise hoặc cũng có thể là non-promise (number, boolean, .etc).
  - Trả về một promise mới.
  - Chờ cho tất cả các promise được xử lý, kết quả trả về là mảng chứa các object chứa trạng thái và giá trị của promise kể cả resolved hay rejected.
- `Promise.any(iterable of multiple promises)`: `experimental`

### Mô phỏng
- es5
```js
function MyPromise() {}

MyPromise.prototype.then = function() {
  console.log("prototype method then")
}

MyPromise.propertyX = "property"

MyPromise.resolve = function(value) {
  console.log('static method resolve', value)
}

MyPromise.all = function(array) {
  console.log('static method all', array)
}

const instance = new MyPromise()

// prototype property
console.log(instance.constructor)
// prototype method
instance.then()

// static property
console.log(MyPromise.propertyX)
// static method
MyPromise.resolve('xxx')
MyPromise.all(['xxx', 'yyy'])
```

- es6
```js
class MyPromise {
  then() {
    console.log("prototype method then")
  }

  static resolve(value) {
    console.log('static method resolve', value)
  }

  static all(array) {
    console.log('static method all', array)
  }
}

MyPromise.propertyX = "property"

const instance = new MyPromise()

// prototype property
console.log(instance.constructor)
// prototype method
instance.then()

// static property
console.log(MyPromise.propertyX)
// static method
MyPromise.resolve('xxx')
MyPromise.all(['xxx', 'yyy'])
```

### all, race, allSetted
- all
```js
const p1 = Promise.resolve(100)
const p2 = Promise.resolve(true)
const p3 = Promise.reject('error')
const p4 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("p4")
  }, 2000)
})

Promise.all([p1,p2,p4])
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.log(err)
  })

Promise.all([p1,p2,p3,p4])
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.log(err)
  })
  
// error
// [ 100, true, 'p4' ]
```

- race
```js
const p1 = Promise.resolve(100)
const p2 = Promise.resolve(true)
const p3 = Promise.reject('error')
const p4 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("p4")
  }, 2000)
})

Promise.race([p1,p2,p4])
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.log(err)
  })

Promise.race([p1,p2,p3,p4])
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.log(err)
  })

// 100
// 100
```

- allSettled
```js
const p1 = Promise.resolve(100)
const p2 = Promise.resolve(true)
const p3 = Promise.reject('error')
const p4 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("p4")
  }, 2000)
})

Promise.allSettled([p1,p2,p4])
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.log(err)
  })

Promise.allSettled([p1,p2,p3,p4])
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.log(err)
  })

// Array [Object { status: "fulfilled", value: 100 }, Object { status: "fulfilled", value: true }, Object { status: "fulfilled", value: "p4" }]
// Array [Object { status: "fulfilled", value: 100 }, Object { status: "fulfilled", value: true }, Object { status: "rejected", reason: "error" }, Object { status: "fulfilled", value: "p4" }]
```

## Thực tế

#### Instance được tạo từ `new Promise()` không truy cập được các static method.
```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("resolve")
  }, 500)
})

promise.resolve(10)

// Error: promise.resolve is not a function
```


#### Catch error vs callback error
- Callback lỗi không bắt được lỗi khi khối promise resolved và trong `callback` của `then` có `throw Error`

Example:
```js
const resolvePromise = new Promise((resolve, reject) => {
  resolve('OK')
})

const rejectPromise = new Promise((resolve, reject) => {
  reject('Error nè')
})

rejectPromise.then(() => {
  throw new Error('Oh no')
}).catch((err) => {
  console.log('Catch lỗi', err)
})

rejectPromise.then(() => {
  throw new Error('Oh no')
}, (err) => {
  console.log('Callback lỗi', err)
})

resolvePromise.then(() => {
  throw new Error('Oh no')
}).catch((err) => {
  console.log('Catch lỗi', err)
})

resolvePromise.then(() => {
  throw new Error('Oh no')
}, (err) => {
  console.log('Callback lỗi', err)
})
```

#### return vs không return trong `callback` của `then`
- Có return
```js
const promise = new Promise((resolve, reject) => {
  resolve(100)
})

promise.then(data1 => {
  console.log("ok 1", data1)
  return data1 * 2
})
.then(data2 => {
  console.log("ok 2", data2)
})
.catch(err => {
  console.log('error', err)
})
.finally(() => {
  console.log('done')
})

// ok 1 100
// ok 2 200
// done
```

- Không return
```js
const promise = new Promise((resolve, reject) => {
  resolve(100)
})

promise.then(data1 => {
  console.log("ok 1", data1)
})
.then(data2 => {
  console.log("ok 2", data2)
})
.catch(err => {
  console.log('error', err)
})
.finally(() => {
  console.log('done')
})

// ok 1 100
// ok 2 undefined
// done
```

#### chaining
- Example 1
```js
const p1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Promise 1')
  })
})

const p2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Promise 2')
  })
})

const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Promise 3')
  })
})

p1.then((data) => {
  console.log(data)
  return p2
})
.then((data) => {
  console.log(data)
  return p3
})
.then((data) => {
  console.log(data)
})

// Promise 1
// Promise 2
// Promise 3
```

- Example 2
```js
const p1 = data => new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log('Promise 1')
    resolve(data)
  })
})

const p2 = data => new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log('Promise 2')
    resolve(data)
  })
})

const p3 = data => new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log('Promise 3')
    resolve(data)
  })
})

p1(1).then((data) => {
  console.log(data)
  return p2(data + 1)
})
.then((data) => {
  console.log(data)
  return p3(data + 1)
})
.then((data) => {
  console.log(data)
})

// Promise 1
// 1
// Promise 2
// 2
// Promise 3
// 3
```

- Example 3
```js
const promise1 = () => fetch('https://jsonplaceholder.typicode.com/posts/1')
const promise2 = () => fetch('https://jsonplaceholder.typicode.com/posts/2')

function withoutChaining() {
  promise1()
    .then(data => data.json())
    .then(json => {
      console.log(json.id)
      console.log(json.title)
    })
  
  promise2()
    .then(data => data.json())
    .then(json => {
      console.log(json.id)
      console.log(json.title)
    })
}

function chaining() {
  promise1()
    .then(data => data.json())
    .then(json => {
      console.log(json.id)
      console.log(json.title)
    })
    .then(promise2)
    .then(data => data.json())
    .then(json => {
      console.log(json.id)
      console.log(json.title)
    })
}
 
withoutChaining()
chaining()
```

#### Microtasks queue (ES8 term)
- Khi 1 promise đã sẵn sàng, `.then/catch/finally` của nó được đẩy vào queue, chúng chưa được thực hiện ngay. Khi `JavaScript engine` đã hoàn thành code hiện tại (hoàn thành các task synchronous), nó lấy các task từ queue và thực thi nó.
- Example
```js
console.log('start')

const promise1 = Promise.resolve()
const promise2 = Promise.reject()

promise1
  .then(() => {
    console.log('promise1 then 1 ok')
  })
  .then(() => {
    console.log('promise1 then 2 ok')
  })
  .catch(() => {
    console.log('catch 1')
  })

promise2
  .then(() => {
    console.log('promise2 then 1 ok')
  })
  .then(() => {
    console.log('promise2 then 2 ok')
  })
  .catch(() => {
    console.log('catch 2')
  })

setTimeout(() => {
  console.log('setTimeout done')
}, 0)

console.log('stop')

// start
// stop
// promise1 then 1 ok
// promise1 then 2 ok
// catch 2
// setTimeout done
```
- Thứ tự xử lý callback trong `then/catch/finally` trong `queue`
```js
const promise1 = Promise.reject()
const promise2 = Promise.resolve()
const promise3 = Promise.resolve()

promise1
  .then(() => {
    console.log('promise1 then')
  })
  .catch(() => {
    console.log('promise1 catch')
  })
  .finally(() => {
    console.log('promise1 finally')
  })

promise2
  .then(() => {
    console.log('promise2 then')
  })
  .catch(() => {
    console.log('promise2 catch')
  })
  .finally(() => {
    console.log('promise2 finally')
  })

promise3
  .then(() => {
    console.log('promise3 then')
  })
  .catch(() => {
    console.log('promise3 catch')
  })
  .finally(() => {
    console.log('promise3 finally')
  })


// promise2 then
// promise3 then
// promise1 catch
// promise1 finally
// promise2 finally
// promise3 finally
```

### Ví dụ trong nodejs
- Example 1
```js
const fs = require('fs')

const readFilePromise = path =>
  new Promise((resolve, reject) =>
    fs.readFile(path, { encoding: 'utf8' }, (err, data) =>
      err ? reject(err) : resolve(data)
    )
  )

console.log('---Start')

console.log('---Reading...')

readFilePromise('Data types.md')
  .then(data => console.log(data))
  .catch(err => console.error(err))

console.log('---End')
```

- Example 2
```js
Promise.all([readFilePromise('Data types.md'), readFilePromise('JSON.md')])
  .then(values => values.map(value => console.log(value)))
  .catch(err => console.error(err))
```
