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

## Query string parameters
```js
const objectToQueryString = (obj) => Object.keys(obj).map((key) => `${encodeURIComponent(key)}=${encodeURIComponent(obj[key])}`).join('&');
objectToQueryString({name: 'Anonystick', age: 18, address: 'VietNam'})
```

## Lấy elements chung của 2 arrays
```js
const similarity = (arr1, arr2) => arr1.filter(item => arr2.includes(item));
similarity([0, 1, 2, 3], [1, 2, 4]); // [1,2]
```

## Check loại thiết bị
```js
const detectDeviceType = () =>/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|OperaMini/i.test(navigator.userAgent) ? 'Mobile' : 'Desktop';
```

## Chuyển đổi số thập phân
```js
const toDecimalMark = num => num.toLocaleString('en-US');
toDecimalMark(12305030388.9087); // "12,305,030,388.909"
```

## Chuyển đổi String với chữ Hoa đầu tiên với nhiều định dạng.
```js
const fromCamelCase = (str, separator = '_') =>str.replace(/([a-z\d])([A-Z])/g, '$1' + separator + '$2').replace(/([A-Z]+)([A-Z][a-z\d]+)/g, '$1' + separator + '$2').toLowerCase();

console.log(fromCamelCase('blogJavascriptAnonystick', ' ')); // 'blog javascript anonysticke'
console.log(fromCamelCase('blogJavascriptAnonystick', '-')); // 'blog-javascript-anonystick'
console.log(fromCamelCase('blogJavascriptAnonystick', '_')); // 'blog_javascript_anonystick'
```

## How to get readable format of the given number of milliseconds?
```js
const formatDuration = ms => {
  if (ms < 0) ms = -ms;
  const time = {
    day: Math.floor(ms / 86400000),
    hour: Math.floor(ms / 3600000) % 24,
    minute: Math.floor(ms / 60000) % 60,
    second: Math.floor(ms / 1000) % 60,
    millisecond: Math.floor(ms) % 1000
  };
  return Object.entries(time)
    .filter(val => val[1] !== 0)
    .map(([key, val]) => `${val} ${key}${val !== 1 ? 's' : ''}`)
    .join(', ');
};

// Examples
console.log(formatDuration(1001)); // "1 second, 1 millisecond"
console.log(formatDuration(34325055574)); // "397 days, 6 hours, 44 minutes, 15 seconds, 574 milliseconds"
console.log(formatDuration(new Date())); 
```

## Get scroll position of the document
```js
const getScrollPositionOfDocument = () => ({
  x: window.pageXOffset || document.documentElement.scrollLeft,
  y: window.pageYOffset || document.documentElement.scrollTop,
});
```
