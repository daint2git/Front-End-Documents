# Purity - Sự thuần khiết

- Pure Function là những hàm hết sức đơn giản, chỉ thao tác dựa trên tham số đầu vào.
- Hầu hết các Pure Function đều có ít nhất một tham số.
- Một Pure Function chỉ có giá trị sử dụng khi có giá trị trả về.
- Pure Function sẽ luôn trả về cùng output với cùng input, bất kể có thực hiện bao nhiêu lần.
- Pure Function đảm bảo việc hàm sẽ không có Side Effects.

### Ex:
```js
function add(x, y) {
  return x + y;
}
```
