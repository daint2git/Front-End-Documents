# Deep and Shallow Copy

## Shallow
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26,
}

// shallow
const userClone = user

userClone.name = 'Nguyen Tran Dai da bi thay doi'

console.log(user) // { name: 'Nguyen Tran Dai da bi thay doi', age: 26 }
console.log(userClone) // { name: 'Nguyen Tran Dai da bi thay doi', age: 26 }
```

## Deep

### Value from original object  
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26
}

const userClone = {
  name: user.name,
  age: user.age,
}

userClone.name = 'Nguyen Tran Dai da bi thay doi'

console.log(user) // { name: 'Nguyen Tran Dai', age: 26 }
console.log(userClone) // { name: 'Nguyen Tran Dai da bi thay doi', age: 26 }
```

### Spread operator
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26,
}

const userClone = { ...user }

userClone.name = 'Nguyen Tran Dai da bi thay doi'

console.log(user) // { name: 'Nguyen Tran Dai', age: 26 }
console.log(userClone) // { name: 'Nguyen Tran Dai da bi thay doi', age: 26 }
```

### Object.assign
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26,
}

const userClone = Object.assign({}, user)

userClone.name = 'Nguyen Tran Dai da bi thay doi'

console.log(user) // { name: 'Nguyen Tran Dai', age: 26 }
console.log(userClone) // { name: 'Nguyen Tran Dai da bi thay doi', age: 26 }
```
