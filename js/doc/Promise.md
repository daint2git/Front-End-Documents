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
- Promise.resolve(value): Trả về một promise resolved (hoàn thành) với một giá trị cụ thể.
- Promise.reject(reason): Trả về một promise rejected (lỗi) với một lỗi cụ thể.
- Promise.all(iterable of multiple promises)
  - Chờ cho tất cả các promise trong mảng resolved và trả về một mảng chứa kết quả của từng promise.
  - Nếu 1 promise bất kì rejected, nó lập tức trả về lỗi. Các promise khác vẫn chạy nhưng kết quả bị bỏ qua.
  - Thực thi promise dạng parallel.
- Promise.race(iterable of multiple promises): Trả về một kết quả của promise bất kì đầu tiên resolved hoặc rejected.
- Promise.allSetted(iterable of multiple promises): Chờ cho tất cả các promise được xử lý, kết quả trả về là mảng chứa các object chứa trạng thái và giá trị của promise kể cả resolved hay rejected.
- Promise.any(iterable of multiple promises): experimental

## Chú ý
- instance được tạo từ `new Promise()` không truy cập được các static method.

## Example
Với es5
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

Với es6
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

#### chaining
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

### Catch error vs callback error
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

### return vs không return trong `callback` của `then`
Có return
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

Không return
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


### Example:
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

- `Promise.all(iterator)`: Nhận vào một mảng các promises và trả về một promise mới và promise mới này chỉ được kết thúc khi tất cả các promise trong `iterable` kết thúc hoặc có một promise nào đó xử lý thất bại. Kết quả của promise mới này là một mảng chứa kết quả của tất cả các promise theo đúng thứ tự hoặc kết quả lỗi của promise gây lỗi.

### Example:
```js
Promise.all([readFilePromise('Data types.md'), readFilePromise('JSON.md')])
  .then(values => values.map(value => console.log(value)))
  .catch(err => console.error(err))
```

- `Promise.race(iterator)`: Nhận vào một mảng các promises và resolve/reject ngay khi một trong các promises trong mảng resolve/reject.
- `Promise.resolve()`: Trả về một promise được tự động resolve.
- `Promise.reject()`: Trả về một promise được tự động reject.

