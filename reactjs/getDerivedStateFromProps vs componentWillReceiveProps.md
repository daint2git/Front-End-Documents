# getDerivedStateFromProps vs componentWillReceiveProps

## getDerivedStateFromProps
- Phương thức này được kích hoạt trên mỗi lần render.

## componentWillReceiveProps
- Phương thức này chỉ kích hoạt khi `parent component` gây ra re-render và không phải là kết quả của `setState` cục bộ.
