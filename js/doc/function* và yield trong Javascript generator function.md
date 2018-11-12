# function* và yield trong Javascript generator function

## function*

- giúp khai báo 1 `generator function`, trả về 1 `Generator object`.

## yield

- yield sẽ trả về giá trị cho iterator.

## Generator function

- là một function, có khả năng tạm ngưng thực thi trước khi hàm kết thúc, và có thể tiếp tục chạy ở 1 thời điểm khác.

- Cú pháp
```js
function* name([param[, param[, ... param]]]) {
   statements
}
```
    - name: tên hàm.
    - param: tham số đầu vào của hàm, tối đa 255 tham số.
    - statements: nội dung của hàm.
Hàm sẽ không được thực thi ngay sau khi gọi, mà thay vào đó generator function trả về iterator, giống như con trỏ trong vòng lặp.
Sau khi hàm next() của iterator được gọi, generator function sẽ thực thi hàm cho đến khi gặp từ khóa yield đầu tiên. yield sẽ trả về giá trị cho iterator, generator function kết thúc cho đến khi hết giá trị để yield.    

### Ví dụ 1
```js
function* id_maker() {
  let index = 0
  while(index < 3)
    yield index++
}

const gen1 = id_maker()
console.log(gen1)
console.log(gen1.next()) // {value: 0, done: false}
console.log(gen1.next()) // {value: 1, done: false}
console.log(gen1.next()) // {value: 2, done: false}
console.log(gen1.next()) // {value: undefined, done: true}
```

### Ví dụ 2
```js
function* anotherGenerator(i) {
  yield i + 1
  yield i + 2
  yield i + 3
}

function* generator(i) {
  yield i
  yield* anotherGenerator(i)
  yield i + 10
}

const gen2 = generator(10)
console.log(gen2)
console.log(gen2.next()) // {value: 10, done: false}
console.log(gen2.next()) // {value: 11, done: false}
console.log(gen2.next()) // {value: 12, done: false}
console.log(gen2.next()) // {value: 13, done: false}
console.log(gen2.next()) // {value: 20, done: false}
console.log(gen2.next()) // {value: undefined, done: true}

```

### Ví dụ 3
```js
function* foo(x) {
  const y = x * (yield)
  return y
}

const it = foo(5)
console.log(it.next()) // {value: undefined, done: false}
console.log(it.next(6)) // {value: 30, done: true}
```
