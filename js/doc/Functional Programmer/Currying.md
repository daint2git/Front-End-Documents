# Currying

- Currying là kỹ thuật tách một hàm nhận nhiều tham số thành một chuỗi các hàm, với mỗi hàm chỉ nhận một tham số
- Một Curried Fuction là một hàm chỉ nhận một tham số trong một thời điểm.

### Ví dụ:
```js
const add = x => y => x + y

console.log(add(10)) // y => x + y

const add10 = add(10)
console.log(add10(15)) // 25
```

### Ví dụ:
```js
const songs = [
  { id: 1, name: 'name 1' },
  { id: 2, name: 'name 2' },
  { id: 3, name: 'name 3' },
]

// binh thuong
console.group('binh thuong')
console.log(songs.map(item => item.id)) // [1, 2, 3]
console.log(songs.map(item => item.name)) // ["name 1", "name 2", "name 3"]
console.groupEnd()

// curring
const get = attr => item => item[attr]

const getId = get('id')
const getName = get('name')

console.group('curring')
console.log('getId', getId) // getId item => item[attr]
console.log('getName', getName) // getName item => item[attr]
console.log(songs.map(getId)) // [1, 2, 3]
console.log(songs.map(getName)) // ["name 1", "name 2", "name 3"]
console.groupEnd()
```
