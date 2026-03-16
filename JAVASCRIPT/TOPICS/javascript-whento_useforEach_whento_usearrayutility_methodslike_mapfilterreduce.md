# When to Use `forEach`, `map`, `filter`, and `reduce` in JavaScript

## Introduction

JavaScript arrays provide several utility methods to process data.

Common ones include:

```

forEach
map
filter
reduce

```

Each method is used for **different purposes**. Choosing the correct method makes code **cleaner and easier to understand**.

---

# 1. forEach()

Use `forEach()` when you want to **loop through an array and perform an action**, but **do not need a new array**.

Important points:

```

Used for side effects
Does not return a new array
Returns undefined

```

### Example

```javascript
const numbers = [1, 2, 3];

numbers.forEach(num => {
  console.log(num);
});
```

Output

```
1
2
3
```

### Example: Updating external variable

```javascript
const numbers = [1, 2, 3];
let total = 0;

numbers.forEach(num => {
  total += num;
});

console.log(total);
```

Output

```
6
```

---

# 2. map()

Use `map()` when you want to **transform each element and create a new array**.

Important points:

```
Returns a new array
Original array remains unchanged
Immutable behavior
```

### Example

```javascript
const numbers = [1, 2, 3];

const doubled = numbers.map(num => num * 2);

console.log(doubled);
```

Output

```
[2, 4, 6]
```

Original array:

```javascript
console.log(numbers);
```

Output

```
[1, 2, 3]
```

---

# 3. filter()

Use `filter()` when you want to **select elements that match a condition**.

Important points:

```
Returns a new array
Elements must pass a condition
Immutable
```

### Example

```javascript
const numbers = [1, 2, 3, 4, 5];

const even = numbers.filter(num => num % 2 === 0);

console.log(even);
```

Output

```
[2, 4]
```

---

# 4. reduce()

Use `reduce()` when you want to **combine array values into a single result**.

Examples include:

```
sum
total
average
object building
```

### Example: Sum of numbers

```javascript
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((total, num) => {
  return total + num;
}, 0);

console.log(sum);
```

Output

```
10
```

### Example: Counting items

```javascript
const fruits = ["apple", "banana", "apple"];

const count = fruits.reduce((acc, fruit) => {
  acc[fruit] = (acc[fruit] || 0) + 1;
  return acc;
}, {});

console.log(count);
```

Output

```
{ apple: 2, banana: 1 }
```

---

# Comparison Example

```javascript
const numbers = [1, 2, 3, 4, 5];

// map
const doubled = numbers.map(n => n * 2);

// filter
const even = numbers.filter(n => n % 2 === 0);

// reduce
const sum = numbers.reduce((a, b) => a + b, 0);

console.log(doubled);
console.log(even);
console.log(sum);
```

Output

```
[2,4,6,8,10]
[2,4]
15
```

---

# Summary

Each array method serves a specific purpose.

| Method  | Use Case                       | Returns      |
| ------- | ------------------------------ | ------------ |
| forEach | Perform actions while looping  | undefined    |
| map     | Transform elements             | New array    |
| filter  | Select elements by condition   | New array    |
| reduce  | Combine values into one result | Single value |

Choosing the correct method helps write **clean and readable JavaScript code**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
