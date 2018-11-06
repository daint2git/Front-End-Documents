# Tips JavaScript

## JavaScript for Loop Shorthand
```js
// Longhand:
for (let i = 0; i < allImgs.length; i++)

// Shorthand:
for (let index of allImgs)
```

## Mandatory Parameter Shorthand
```js
// Longhand:
function foo(bar) {
  if(bar === undefined) {
    throw new Error('Missing parameter!');
  }
  return bar;
}

// Shorthand:
mandatory = () => {
  throw new Error('Missing parameter!');
}

foo = (bar = mandatory()) => bar;
```

## falsy (false, null, undefined, 0, NaN, '')
```js
const a = [1, 'b', [], {}, false, null, undefined, 0, NaN, ''];
const b = a.filter(Boolean); // [1, "b", [], {}]
```
