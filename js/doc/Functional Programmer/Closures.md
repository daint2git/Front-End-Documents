# Closures

- Một closure (bao đóng) là một scope của một hàm.
- Scope của một hàm vẫn sẽ tồn tại đến khi nào còn có tham chiếu đến hàm đó.

## Ví dụ:
```js
function grandParent(g1, g2) {
  const g3 = 3;
  return function parent(p1, p2) {
    const p3 = 33;
    return function child(c1, c2) {
      const c3 = 333;
      return g1 + g2 + g3 + p1 + p2 + p3 + c1 + c2 + c3;
    };
  };
}

const parentFunc = grandParent(1, 2); // returns parent() - trả về hàm parent() với g1 = 1, g2 = 2, g3 = 3
const childFunc = parentFunc(11, 22); // returns child() - trả về hàm child() với g1 = 1, g2 = 2, g3 = 3, p1 = 11, p2 = 22, p3 = 33
console.log(childFunc(111, 222)); // prints 738 - in ra 738 vì :
// 1 + 2 + 3 + 11 + 22 + 33 + 111 + 222 + 333 == 738
```

## Closure with function return function
```js
function outer(name) {
  const currentYear = new Date().getFullYear()
  return function inner(yearOfBirth) {
    console.log(`Hi name: ${name}, age: ${currentYear - yearOfBirth}`)
  }
}

const injectName = outer('Dai')
injectName(1993) // Hi name: Dai, age: 26

// or
outer('Dai')(1993) // Hi name: Dai, age: 26
```

## Closure with function return object
```js
function outer(name) {
  return {
    getName: function() {
      console.log(name)
    },
    setName: function(newName) {
      console.log(newName)
    },
  }
}

const injectName = outer('Dai')
injectName.getName() // Dai
injectName.setName('New Dai') // New Da
```

## Closure with function return array
```js
function outer(name) {
  return ['Nguyen', 'Tran', name]
}

const injectName = outer('Dai')
console.log(injectName[0], injectName[1], injectName[2]) // Nguyen Tran Dai

injectName[1] = 'Van'
console.log(injectName[0], injectName[1], injectName[2]) // Nguyen Van Dai
```
