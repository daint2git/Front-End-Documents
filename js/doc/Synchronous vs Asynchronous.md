# Synchronous vs Asynchronous

JavaScript là một ngôn ngữ lập trình đơn luồng, có nghĩa là chỉ một điều gì đó có thể xảy ra tại một thời điểm.
`JavaScript engine` chỉ có thể xử lý một câu lệnh tại một thời điểm trong một luồng.


  
## JavaScript runtime environment

![JavaScript runtime environment](https://miro.medium.com/max/839/1*O_H6XRaDX9FaC4Q9viiRAA.png)

### Event Loop
- Luồng thực thi của Browser JavaScript, cũng như Nodejs là dựa trên một `event loop`.
- Có một vòng lập vô tận, khi `JavaScript engine` chờ đợi các task, thực thi chúng và sau đó sleep chờ thêm các task.
- Thuật toán chung của động cơ:
  1. Khi có các task: thực thi chúng, bắt đầu với các nhiệm vũ cũ nhất.
  2. Sleep cho đến khi 1 task xuất hiện, sau đó đi đến `i`
  
### Chú ý:
`event loop`, `web APIs`, `message queue/ task queue` không phải là một phần của `JavaScript engine`,
nó là một phần của `browser’s JavaScript runtime environment` hay `Nodejs JavaScript runtime environment`(trong trường hợp Nodejs)


## Synchronous JavaScript hoạt động như thế nào ?

### Execution Context và Execution Stack (Call Stack)
#### Execution Context
- Một `Execution Context` là một khái niệm trừu tượng về một môi trường nơi JavaScript code được ước tính và thực thi.
Bất cứ khi nào bấy kì code nào được chạy trong JavaScript, nó sẽ chạy trong 1 `Execution Context`.

- Function code thực thi bên trong `Function Execution Context`.
- Global code thực thi bên trong `Global Execution Context`.
- Mỗi chức năng có `Execution Context` của riêng nó.

#### Execution Stack (Call Stack)
- Theo cấu trúc Stack LIFO (Last in, First out).
- Được sử dụng để lưu trữ tất cả `Execution Context` được tạo trong suốt quá trình thực thi code.
- JavaScript có 1 `Execution Stack` duy nhất vì nó là ngôn ngữ lập trình đơn luồng.

##### Cách Synchronous JavaScript code thực thi bên trong `JavaScript engine`. Ví dụ:
```js
const second = () => {
  console.log('Hello there!');
}

const first = () => {
  console.log('Hi there!');
  second();
  console.log('The End');
}

first();
```
![Call Stack](https://miro.medium.com/max/1257/1*DkG1a8f7rdl0GxM0ly4P7w.png)

## Asynchronous JavaScript hoạt động như thế nào ?

### Cách Asynchronous JavaScript code thực thi bên trong `JavaScript engine`. Ví dụ:
```js
const networkRequest = () => {
  setTimeout(() => {
    console.log('Async Code');
  }, 2000);
};

console.log('Hello World');

networkRequest();

console.log('The End');
```
![Asynchronous JavaScript code executed](https://miro.medium.com/max/842/1*sOz5cj-_Jjv23njWg_-uGA.gif)

### Chú ý:
- `setTimeout` không phải một phần của `JavaScript engine`, nó là 1 phần của web APIs (trong browsers) and C/C++ APIs (trong node.js).

## ES6 Job Queue/ Micro-Task queue
- Khái niệm này được sử dụng bởi `Promises in JavaScript`.
- Nó có độ ưu tiên cao hơn `Message Queue`, nghĩa là `promise` bên trong `Job Queue` sẽ được thực thi trước `callbacks` bên trong `Message Queue`.

Ví dụ:
```js
console.log('Script start');

setTimeout(() => {
  console.log('setTimeout');
}, 0);

new Promise((resolve, reject) => {
    resolve('Promise resolved');
  }).then(res => console.log(res))
    .catch(err => console.log(err));
    
console.log('Script End');

// Script start
// Script End
// Promise resolved
// setTimeout
```

## Visualizing the javascript runtime at runtime
http://latentflip.com/loupe
