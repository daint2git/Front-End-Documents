# Currying

- Một Curried Fuction là một hàm chỉ nhận một tham số trong một thời điểm.

Ex:

const add = x => y => x + y

console.log(add(10)) // y => x + y

const add10 = add(10)
console.log(add10(15)) // 25