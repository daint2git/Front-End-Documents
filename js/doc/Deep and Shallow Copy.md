# Deep and Shallow Copy

```js
let user = {
  name: 'my name',
  age: '23'
};

// shallow
let userClone = user;
userClone.name = 'my name was changed!'

// deep
let userClone = {
  name: user.name,
  age: user.age
};
userClone.name = 'my name was changed too!';
```
