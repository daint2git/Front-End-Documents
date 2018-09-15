# async-await

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

const readFiles = async (...filesPath) => {
  const fileContent1 = await readFilePromise(filesPath[0])
  const fileContent2 = await readFilePromise(filesPath[1])
  console.log(fileContent1, fileContent2)
}

readFiles('Data types.md', 'JSON.md')

console.log('---End')
```