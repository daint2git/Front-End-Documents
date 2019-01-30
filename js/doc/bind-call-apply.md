# bind, call, apply
```js
// method with arrow function
const user1 = {
  firstName: 'Dai',
  lastName: 'Nguyen',
  age: 26,
  showName: () => console.log(`${user1.firstName} ${user1.lastName}`),
}

// method with anonymous function declaration
const user2 = {
  firstName: 'Dai',
  lastName: 'Nguyen',
  age: 26,
  showName: function() {
    console.log(`${this.firstName} ${this.lastName}`)
  },
}

// method with function declaration
const user3 = {
  firstName: 'Dai',
  lastName: 'Nguyen',
  age: 26,
  showName: function xxx() {
    console.log(`${this.firstName} ${this.lastName}`)
  },
}

user1.showName() // Dai Nguyen
user2.showName() // Dai Nguyen
user3.showName() // Dai Nguyen

function showMoreUserInfo(skills = [], totalYearsOfExperience = 0, hobbies = []) {
  console.log(this.age, skills, totalYearsOfExperience, hobbies)
}

showMoreUserInfo.bind(user1)() // 26 [] 0 []
showMoreUserInfo.call(user1) // 26 [] 0 []
showMoreUserInfo.apply(user1) // 26 [] 0 []

showMoreUserInfo.bind(user1)(['js', 'html', 'css'], 3, ['research', 'game']) // 26 ["js", "html", "css"] 3 ["research", "game"]
showMoreUserInfo.call(user1, ['js', 'html', 'css'], 3, ['research', 'game']) // 26 ["js", "html", "css"] 3 ["research", "game"]
showMoreUserInfo.apply(user1, [['js', 'html', 'css'], 3, ['research', 'game']]) // 26 ["js", "html", "css"] 3 ["research", "game"]
```

# call() vs apply() method
- Là một phương thức JS được xác định trước.
- Một đối tượng có thể sử dụng một phương thức thuộc về một đối tượng khác.
- Khác nhau giữa `call` và `apply`
  - `call` method lấy đối số `riêng biệt`
  - `apply` method lấy đối số `như một mảng`

## call
```js
const person = {
  showInfo: function(city, country) {
    return `${this.firstName}, ${this.lastName}, ${city}, ${country}`
  },
}

const anotherPerson = {
  firstName: 'Dai',
  lastName: 'Nguyen',
}

console.log(person.showInfo.call(anotherPerson, 'Da Nang', 'VN')) // Dai, Nguyen, Da Nang, VN
```

## apply
```js
const person = {
  showInfo: function(city, country) {
    return `${this.firstName}, ${this.lastName}, ${city}, ${country}`
  },
}

const anotherPerson = {
  firstName: 'Dai',
  lastName: 'Nguyen',
}

console.log(person.showInfo.apply(anotherPerson, ['Da Nang', 'VN'])) // Dai, Nguyen, Da Nang, VN
```