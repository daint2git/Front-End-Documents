# Callback function

- Là hàm được truyền vào một hàm khác như một tham số đầu vào, sau đó sẽ được gọi thực thi bên trong hàm đó.

### Ví dụ:
```js
const A = func => {
  console.log('Hàm A')
  func()
}

const B = () => {
  console.log('Hàm B')
}

A(B)

// Hàm B được xem là callback function
```
