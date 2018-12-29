# getDerivedStateFromProps vs componentWillReceiveProps

## getDerivedStateFromProps
- Được kích hoạt trên mỗi lần render.

## componentWillReceiveProps
- Được kích hoạt trước khi `a mounted component` nhận props mới.
- Được kích hoạt khi `parent component` gây ra re-render, ngay cả khi props không thay đổi.
- Không được kích hoạt khi `setState` cục bộ.
- Không được kích hoạt trong lần đầu tiên khi `mounting component`.
