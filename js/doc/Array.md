# Array Methods

## Array.from
method creates a new, shallow-copied Array instance from an array-like or iterable object.

```js
Array.from('foo') // ["f", "o", "o"]
Array.from([1, 2, 3], x => x + x) // [2, 4, 6]
Array.from({ length: 10 }, (v, k) => k).map(k => k) // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Array.of
method creates a new Array instance with a variable number of arguments, regardless of number or type of the arguments.

```js
Array.of(7) // [7]
Array.of(1, 2, 3) // [1, 2, 3]
```

## Array.keys
method returns a new `Array Iterator` object that contains the keys for each index in the array.

```js
const array = ['a', 'b', 'c']
const iterator = array.keys()

for (let key of iterator) {
  console.log(key)
}
// 0
// 1
// 2
```

## Array.values
method returns a new `Array Iterator` object that contains the values for each index in the array.

```js
const array = ['a', 'b', 'c']
const iterator = array.values()

for (let value of iterator) {
  console.log(value)
}
// a
// b
// c
```

## Array.entries
method returns a new `Array Iterator` object that contains the key/value pairs for each index in the array.

```js
const array = ['a', 'b', 'c']
const iterator = array.entries()

console.log(iterator.next()) // { value: Array [0, "a"], done: false }
console.log(iterator.next()) // { value: Array [1, "b"], done: false }
console.log(iterator.next()) // { value: Array [2, "c"], done: false }
console.log(iterator.next()) // { value: undefined, done: true }
```

## Array.find
method returns the `value` of the `first element` in the array that satisfies the provided testing function. Otherwise `undefined` is returned.

```js
const array = [5, 12, 8, 130, 44]

console.log(array.find(element => element < 10)) // 5
console.log(array.find(element => element > 40)) // 130
console.log(array.find(element => element > 130)) // undefined
```

## Array.findIndex
method returns the `index` of the `first element` in the array `that satisfies the provided testing function`. Otherwise, it returns `-1`, indicating no element passed the test.

```js
const array = [5, 12, 8, 130, 44]

console.log(array.findIndex(element => element > 13)) // 3
console.log(array.findIndex(element => element > 130)) // -1
```

## Array.fill
method fills all the elements of an array from a start index to an end index with a static value. The end index is not included.

```js
const array = [1, 2, 3, 4]

// fill with 0 from position 2 until position 4
console.log(array.fill(0, 2, 4)) // [1, 2, 0, 0]

// fill with 5 from position 1
console.log(array.fill(5, 1)) // [1, 5, 5, 5]

console.log(array.fill(6)) // [6, 6, 6, 6]
```

## Array.copyWithin
method shallow copies part of an array to another location in the same array and returns it, without modifying its size.

```js
const array1 = [1, 2, 3, 4, 5]
const array2 = [1, 2, 3, 4, 5]

// place at position 0 the element between position 3 and 4
console.log(array1.copyWithin(0, 3, 4)) // [4, 2, 3, 4, 5]

// place at position 1 the elements after position 3
console.log(array2.copyWithin(1, 3)) // [4, 4, 5, 4, 5]
```

## Array.every
method tests whether all elements in the array pass the test implemented by the provided function.

```js
const array = [1, 30, 39, 29, 10, 13]

console.log(array.every(currentValue => {
  console.log(currentValue)
  return currentValue < 40
}))
// 1
// 30
// 39
// 29
// 10
// 13
// true

console.log(array.every(currentValue => {
  console.log(currentValue)
  return currentValue > 40
}))
// 1
// false

console.log([].every(currentValue => {
  console.log(currentValue)
  return currentValue > 40
}))
// true
```

## Array.some
method tests whether at least one element in the array passes the test implemented by the provided function.

```js
const array = [1, 2, 3, 4, 5]

console.log(array.some(currentValue => {
  console.log(currentValue)
  return currentValue > 2
}))
// 1
// 2
// 3
// true

console.log(array.some(currentValue => {
  console.log(currentValue)
  return currentValue > 5
}))
// 1
// 2
// 3
// 4
// 5
// false

console.log([].some(currentValue => {
  console.log(currentValue)
  return currentValue > 5
}))
// false
```

## Array.indexOf
method returns the first index at which a given element can be found in the array, or -1 if it is not present.

```js
const beasts = ['ant', 'bison', 'camel', 'duck', 'bison']

console.log(beasts.indexOf('bison')) // 1

// start from index 2
console.log(beasts.indexOf('bison', 2)) // 4

console.log(beasts.indexOf('giraffe')) // -1
```

## Array.shift
method removes the `first` element from an array and returns that removed element. This method changes the length of the array.

```js
const array = [1, 2, 3]

console.log(array.shift()) // 1

console.log(array) // [2, 3]

array.shift()

console.log(array) // [3]
```

## Array.unshift
method adds one or more elements to the beginning of an array and returns the new length of the array.

```js
const array = [1, 2, 3]

console.log(array.unshift(4, 5)) // 5

console.log(array) // [4, 5, 1, 2, 3]
```

## Array.pop
method removes the `last` element from an array and returns that element. This method changes the length of the array.

```js
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato']

console.log(plants.pop()) // "tomato"

console.log(plants) // ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop()

console.log(plants) // ["broccoli", "cauliflower", "cabbage"]
```

## Array.splice
method changes the contents of an array by removing or replacing existing elements and/or adding new elements.

```js
const months = ['Jan', 'March', 'April', 'June']
months.splice(1, 0, 'Feb')
// inserts at 1st index position
console.log(months) // ['Jan', 'Feb', 'March', 'April', 'June']

months.splice(4, 1, 'May')
// replaces 1 element at 4th index
console.log(months) // ['Jan', 'Feb', 'March', 'April', 'May']
```

## Array.slice
method returns a shallow copy of a portion of an array into a new array object selected from `begin` to `end` (`end` not included). The original array will not be modified.

```js
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant']

console.log(animals.slice(2)) // ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4)) // ["camel", "duck"]

console.log(animals.slice(1, 5)) // ["bison", "camel", "duck", "elephant"]
```

## Array.includes
method determines whether an array includes a certain element, returning `true` or `false` as appropriate.

```js
const array = [1, 2, 3]

console.log(array.includes(2)) // true
console.log(array.includes(4)) // false

var pets = ['cat', 'dog', 'bat']

console.log(pets.includes('cat')) // true
console.log(pets.includes('at')) // false
```

## Array.reduce
method executes a `reducer` function (that you provide) on each member of the array resulting in a single output value.

```js
const array = [1, 2, 3, 4]
const reducer = (accumulator, currentValue) => accumulator + currentValue

// 1 + 2 + 3 + 4
console.log(array.reduce(reducer)) // 10

// 5 + 1 + 2 + 3 + 4
console.log(array.reduce(reducer, 5)) // 15
```

## Array.reduceRight
method applies a function against an accumulator and each value of the array (from right-to-left) to reduce it to a single value.

```js
const array = [[0, 1], [2, 3], [4, 5]]
const reducer = (accumulator, currentValue) => accumulator.concat(currentValue)

console.log(array.reduceRight(reducer)) // [4, 5, 2, 3, 0, 1]

console.log(array.reduceRight(reducer, [9, 10])) // [9, 10, 4, 5, 2, 3, 0, 1]
```
