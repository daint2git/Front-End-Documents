# Higher-Order Functions

- Hàm có cấp bậc cao hơn → có nghĩa là hàm có nhiều khả năng và linh hoạt hơn.
- Là hàm có hoạt động dựa trên 1 hàm khác. Cụ thể các trường hợp sau:
  - Nhận hàm làm tham số đầu vào
  - Trả về hàm
  - Vừa nhận hàm làm tham số đầu vào, vừa trả về hàm

### Nhận hàm làm tham số đầu vào:
```js
function A(func) {
  console.log('Hàm A')
  func()
}

function B() {
  console.log('Hàm B')
}

A(B)
```

### Trả về hàm:
```js
function A() {
  console.log('Hàm A')
  return function B() {
    console.log('Hàm B')
  }
}

A()()
```
### Vừa nhận hàm làm tham số đầu vào, vừa trả về hàm:
```js
function A(func) {
  console.log('Hàm A')
  return function B() {
    console.log('Hàm B')
    func()
  }
}

function C() {
  console.log('Hàm C')
}

A(C)()
```
