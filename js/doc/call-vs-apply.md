# call() vs apply() method
- là một phương thức JavaScript được xác định trước.
- một đối tượng có thể sử dụng một phương thức thuộc về một đối tượng khác.
- Khác nhau giữa call() và apply()
  - call() method lấy đối số `riêng biệt`
  - apply() method lấy đối số `như một mảng`
  
Example with `call()`
```js
var person = {
    fullName: function(city, country) {
        return this.firstName + " " + this.lastName + "," + city + "," + country;
    }
}

var person1 = {
    firstName:"John",
    lastName: "Doe",
}

console.log(person.fullName.call(person1, "Oslo", "Norway")); // "John Doe,Oslo,Norway"
```

Example with `apply()`
```js
var person = {
    fullName: function(city, country) {
        return this.firstName + " " + this.lastName + "," + city + "," + country;
    }
}

var person1 = {
    firstName:"John",
    lastName: "Doe",
}

console.log(person.fullName.apply(person1, ["Oslo", "Norway"])); // "John Doe,Oslo,Norway"
```
