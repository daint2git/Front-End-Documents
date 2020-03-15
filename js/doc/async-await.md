# async-await

## Khái niệm
- async-await dựa trên promise

- async trước 1 function có 2 hiệu ứng:
  - Làm cho nó luôn luôn trả về 1 promise.
  - Cho phép `await` được sử dụng bên trong nó.
- await trước 1 promise làm cho JavaScript chờ cho đến khi promise đó được giải quyết, và sau đó:
  - Nếu có lỗi, exception được tạo ra.
  - Nếu không có lỗi, nó trả về kết quả.
  
## Ví dụ
- Cơ bản
```js
async function f1() {
  return 1
}

async function f2() {
  return Promise.resolve(1)
}

f1().then(console.log)
f2().then(console.log)

// 1
// 1
```
- Chaining
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

// p1(1).then((data) => {
//   console.log(data)
//   return p2(data + 1)
// })
// .then((data) => {
//   console.log(data)
//   return p3(data + 1)
// })
// .then((data) => {
//   console.log(data)
// })

async function main() {
 console.log('async-await')
 const p1Result = await p1(1) 
 console.log(p1Result)
 const p2Result = await p2(p1Result + 1) 
 console.log(p2Result)
 const p3Result = await p3(p2Result + 1)
 console.log(p3Result)
}

main()

// Promise 1
// 1
// Promise 2
// 2
// Promise 3
// 3
```

## Ví dụ trong nodejs
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

const readFiles = async (...filesPath) => {
  const fileContent1 = await readFilePromise(filesPath[0])
  const fileContent2 = await readFilePromise(filesPath[1])
  console.log(fileContent1, fileContent2)
}

readFiles('Data types.md', 'JSON.md')

console.log('---End')
```

```js
const userInfo = {
  id: 1,
  name: 'Nguyen Tran Dai',
  age: 25,
}

const userSkills = ['js', 'html', 'css']

setTimeout(() => {
  const getUserInfo = () => new Promise((resolve, reject) => resolve(userInfo))

  const getUserSkills = () => new Promise((resolve, reject) => resolve(userSkills))

  const countUserFriends = () => new Promise((resolve, reject) => resolve(69))

  Promise.all([getUserInfo(), getUserSkills(), countUserFriends()]).then(
    ([info, skills, friends]) => console.log(info, skills, friends),
  )
}, 500)

setTimeout(async () => {
  const getUserInfo = () => new Promise((resolve, reject) => resolve(userInfo))

  const getUserSkills = () => new Promise((resolve, reject) => resolve(userSkills))

  const countUserFriends = () => new Promise((resolve, reject) => resolve(69))

  // const info = await getUserInfo()
  // const skills = await getUserSkills()
  // const friends = await countUserFriends()

  // or
  const [info, skills, friends] = await Promise.all([
    getUserInfo(),
    getUserSkills(),
    countUserFriends(),
  ])
  console.log(info, skills, friends)
}, 1000)
```
