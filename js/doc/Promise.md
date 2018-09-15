# Promise object

- Là một đối tượng đặc biệt dùng cho các xử lý bất đồng bộ. Nó đại diện cho một xử lý bất đồng bộ và chứa kết quả cũng như các lỗi xảy ra từ xử lý bất đồng bộ đó.

### Ex:
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