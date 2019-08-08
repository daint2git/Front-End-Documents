# Object

- Có 2 cách để khởi tạo object là sử dụng:
    - Object literal
    - Constructor function

Ví dụ:
```js
// Object literal
const person = {
  firstName: 'Dai',
  lastName: 'Nguyen',
  showName: function() {
    console.log(`${this.firstName} ${this.lastName}`)
  }
} // object này có prototype là Object.prototype

console.log(person.constructor.name) // "Object"

// Constructor function
function Person(_firstName, _lastName) {
  this.firstName = _firstName
  this.lastName = _lastName
  this.showName = function() {
    console.log(`${this.firstName} ${this.lastName}`)
  }
}

const otherPerson = new Person('Dai', 'Nguyen')
// object này có prototype là Person.prototype
// Prototype mới: Person.prototype được tạo ra
// Person.prototype kế thừa Object.prototype
console.log(otherPerson.constructor.name) // "Person"
```
Ví dụ khác
```js
    function Fruit(_name, _color) {
      this.name = _name;
      this.color = _color;
      this.getName = () => console.log(this.name)
    }

    const AppleFruit = new Fruit('apple', 'red')
    const MangoFruit = new Fruit('mango', 'yellow')

    console.log('AppleFruit', AppleFruit) // Fruit {name: "apple", color: "red", getName: () => console.log(this.name)}
    AppleFruit.getName() // apple
    console.log('color' in AppleFruit) // true
    console.log('status' in AppleFruit) // false
    AppleFruit.price = 9999
    console.log('AppleFruit', AppleFruit) // Fruit {name: "apple", color: "red", getName: () => console.log(this.name), price: 9999}
    console.log(AppleFruit.hasOwnProperty('price')) // true
    console.log(AppleFruit.hasOwnProperty('origin')) // false
    Fruit.prototype.origin = 'VN'
    console.log(AppleFruit.origin) // VN
```

## Object literal vs Object create

```js
console.log({}.__proto__) // {constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}
console.log({}.hasOwnProperty) // ƒ hasOwnProperty() { [native code] }

console.log(Object.create(null).__proto__) // undefined
console.log(Object.create(null).hasOwnProperty) // undefined
```
