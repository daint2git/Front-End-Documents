# JSON

## JSON là cái gì ?
- Kí hiệu đối tượng JavaScript (JavaScript Object Notation) là biểu mẫu dữ liệu dùng để kí hiệu đối tượng trong JavaScript
- Trong JSON, toàn bộ dữ liệu đều được coi là một mảng(array) hoặc là một đối tượng(object) (là cấu trúc dữ liệu dựa trên các cặp key-value)
- Các kiểu dữ liệu chính của JSON gồm có:
  - string
  - number (gồm số nguyên và số thực)
  - boolean (true/ false)
  - array
  - object
  - null

## Các phương thức của JSON 
- `stringify` convert an object to a JSON string
- `parse` convert a JSON string to an object

Ex:
```js
const myPet = { name: "cucu", weight: 5, isDead: false }

const myPetString = JSON.stringify(myPet)
console.log(myPetString) // {"name":"cucu","weight":5,"isDead":false}
console.log(typeof myPetString) // string

const myPetObject = JSON.parse(myPetString)
console.log(myPetObject) // { name: 'cucu', weight: 5, isDead: false }
console.log(typeof myPetObject) // object
```

### Các tham số khác của `JSON.stringify`

Ex:
```js
const obj = {
  a: 1,
  b: 2,
  c: 3,
  d: {
    e: 4,
  },
  f: 'hahaha',
}

const replacer = (key, value) => {
  if (typeof value === 'number') return value + 1
  return value
}

console.log(JSON.stringify(obj, replacer))
// {"a":2,"b":3,"c":4,"d":{"e":5},"f":"hahaha"}

console.log(JSON.stringify(obj, null, 2))
// {
//   "a": 1,
//   "b": 2,
//   "c": 3,
//   "d": {
//     "e": 4
//   },
//   "f": "hahaha"
// }

console.log(JSON.stringify(obj, null, '_'))
// {
// _"a": 1,
// _"b": 2,
// _"c": 3,
// _"d": {
// __"e": 4
// _},
// _"f": "hahaha"
// }
```
