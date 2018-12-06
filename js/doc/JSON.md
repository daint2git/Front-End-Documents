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

### Ex:
```js
const myPet = { name: "cucu", weight: 5, isDead: false }

const myPetString = JSON.stringify(myPet)
console.log(myPetString) // {"name":"cucu","weight":5,"isDead":false}
console.log(typeof myPetString) // string

const myPetObject = JSON.parse(myPetString)
console.log(myPetObject) // { name: 'cucu', weight: 5, isDead: false }
console.log(typeof myPetObject) // object
```
