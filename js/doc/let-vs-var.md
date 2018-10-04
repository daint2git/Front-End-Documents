# let vs var

- `var`: tạo ra một biến có phạm vi global, xuyên suốt trong tất cả các function chứa nó.
```js
function varTest() {
   var x = 1;
   if (true) {
      var x = 2; // x ở đây cũng là x ở trên
      console.log(x); // in ra 2
   }
   console.log(x); // vẫn là 2
}
```

- `let`: tạo một biến chỉ có thể truy cập được trong block bao quanh nó, cụ thể là bên trong `{}` chứa nó.
```js
function letTest() {
   let x = 1;
   if (true) {
      let x = 2; // x này là x khác rồi đấy
      console.log(x); // in ra 2
   }
   console.log(x); // in ra 1
}
```
