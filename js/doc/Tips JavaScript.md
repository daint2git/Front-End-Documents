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
