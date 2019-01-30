# tips

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

## remove falsy (false, null, undefined, 0, NaN, '')
```js
const a = [1, 'b', [], {}, false, null, undefined, 0, NaN, '']
const b = a.filter(Boolean) // [1, "b", [], {}]
```

## Compare Array
```js
const arr1 = [1, 2, 3, 4, 5, 6, 7, 8, 9]
const arr2 = [2, 3, 6, 9]

const difference1 = (arr1, arr2) => arr1.filter(i => !arr2.includes(i))
const difference2 = (arr1, arr2) => arr1.filter(i1 => !arr2.some(i2 => i2 === i1))
const difference3 = (arr1, arr2) => arr1.filter(i => arr2.indexOf(i) === -1)
```

## remove duplicates
```js
const arr = [
  { id: 1, name: 'Nguyen Van A' },
  { id: 2, name: 'Nguyen Van A' },
  { id: 3, name: 'Nguyen Van B' },
  { id: 4, name: 'Nguyen Van C' },
  { id: 5, name: 'Nguyen Van A' },
]

const names = arr.map(({ name }) => name)

const namesUnique = names.filter((n, index) => names.indexOf(n) >= index)
```

## parse a url
```js
const url = 'https://example.com.vn/folder1/folder2/index.html'
const [fullUrl, protocol, fullHost, fullPath] = /^(\w+)\:\/\/([^\/]+)\/(.*)$/.exec(url)
console.log(fullUrl)
console.log(protocol)
console.log(fullHost)
console.log(fullPath)
```