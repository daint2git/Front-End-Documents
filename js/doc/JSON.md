# JSON object

- `stringify`: convert an object to a JSON string
- `parse`: convert a JSON string to an object

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
