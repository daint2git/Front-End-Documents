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
  age: 26,
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

### Vấn đề với Object lồng nhau

#### Kết quả không mong muốn
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26,
  skill: {
    fe: ['html', 'css'],
    be: ['java'],
  },
}

const userClone = { ...user }

userClone.skill.fe = ['js']

console.log(user) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'js' ], be: [ 'java' ] } }
console.log(userClone) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'js' ], be: [ 'java' ] } }
```

#### Kết quả mong muốn

##### Spread operator
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26,
  skill: {
    fe: ['html', 'css'],
    be: ['java'],
  },
}

const userClone = { ...user }

userClone.skill = {
  ...userClone.skill,
  fe: ['js'],
}

console.log(user) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'html', 'css' ], be: [ 'java' ] } }
console.log(userClone) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'js' ], be: [ 'java' ] } }
```

Hoặc
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26,
  skill: {
    fe: ['html', 'css'],
    be: ['java'],
  },
}

const userClone = { 
  ...user,
  skill: {
    ...user.skill,
    fe: ['js'],
  },
}

console.log(user) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'html', 'css' ], be: [ 'java' ] } }
console.log(userClone) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'js' ], be: [ 'java' ] } }
```

##### JSON.parse và JSON.stringify
```js
const user = {
  name: 'Nguyen Tran Dai',
  age: 26,
  skill: {
    fe: ['html', 'css'],
    be: ['java'],
  },
}

const userClone = JSON.parse(JSON.stringify(user))

userClone.skill.fe = ['js']

console.log(user) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'html', 'css' ], be: [ 'java' ] } }
console.log(userClone) // { name: 'Nguyen Tran Dai', age: 26, skill: { fe: [ 'js' ], be: [ 'java' ] } }
```
