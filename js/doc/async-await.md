# async-await

## Ví dụ
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