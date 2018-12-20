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