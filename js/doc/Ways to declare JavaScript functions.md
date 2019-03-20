# Ways to declare JavaScript functions

## Function declaration

```js
function calcRectArea(width, height) {
  return width * height;
}
```

## Function expression

```js
const getRectArea = function(width, height) {
    return width * height;
}
```

## Arrow function

```js
const getRectArea = (width, height) => width * height;
```

## Generator function

```js
function* generator(i) {
  yield i;
  yield i + 10;
}

var gen = generator(10);

console.log(gen.next().value);
// expected output: 10

console.log(gen.next().value);
// expected output: 20
```

## Function constructor

```js
const sum = new Function('a', 'b', 'return a + b');

console.log(sum(2, 6));
// expected output: 8
```

## Shorthand method definition

```js
const o = {
  property: function (parameters) {},
  get property() {},
  set property(value) {}
};
```
