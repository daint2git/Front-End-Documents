# Higher-Order Functions

- Higher-Order Functions có nghĩa là Hàm có cấp bậc cao hơn - với ý nghĩa là hàm có nhiều khả năng và linh hoạt hơn.
- Higher-Order Functions là các hàm hoặc nhận hàm làm tham số, hoặc trả về hàm, hoặc vừa nhận hàm làm tham số vừa trả về hàm.

### Ex:
```js
function makeAdder(constantValue) {
  return function adder(value) {
    return constantValue + value;
  };
}
```
