# Higher-Order Functions

- Hàm có cấp bậc cao hơn → có nghĩa là hàm có nhiều khả năng và linh hoạt hơn.
- Là hàm có hoạt động dựa trên 1 hàm khác. Cụ thể các trường hợp sau:
  - Nhận hàm làm tham số đầu vào
  - Trả về hàm
  - Vừa nhận hàm làm tham số đầu vào, vừa trả về hàm

### Ex:
```js
// Nhận hàm làm tham số đầu vào
function A(func) {
  console.log('Hàm A')
  func()
}

function B() {
  console.log('Hàm B')
}

A(B)

// Trả về hàm
function A(value1) {
  console.log(value1)
  return function B(value2) {
    console.log(value2)
  }
}

A(1)(2)
```
