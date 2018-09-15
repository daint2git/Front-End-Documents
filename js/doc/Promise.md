# Promise object

- `Promise`: Là một đối tượng đặc biệt dùng cho các xử lý bất đồng bộ. Nó đại diện cho một xử lý bất đồng bộ và chứa kết quả cũng như các lỗi xảy ra từ xử lý bất đồng bộ đó.

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

- `Promise.all()`: Phương thức `Promise.all(iterable)` trả ra một Promise mới và promise mới này chỉ được kết thúc khi tất cả các promise trong `iterable` kết thúc hoặc có một promise nào đó xử lý thất bại. Kết quả của promise mới này là một mảng chứa kết quả của tất cả các promise theo đúng thứ tự hoặc kết quả lỗi của promise gây lỗi.

### Example:
```js
Promise.all([readFilePromise('Data types.md'), readFilePromise('JSON.md')])
  .then(values => values.map(value => console.log(value)))
  .catch(err => console.error(err))
```
