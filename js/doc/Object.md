# Object

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
