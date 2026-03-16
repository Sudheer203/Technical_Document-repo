# Popular Array Utility Methods in JavaScript

## Introduction

Arrays store multiple values in JavaScript.  
JavaScript provides many **array utility methods** to modify, search, and transform arrays.

Array methods can be:

```

Mutable   → change the original array
Immutable → return a new array without changing the original

```

---

# Basics

## Array.push()  (Mutable)

Adds elements to the **end** of the array.

```javascript
const numbers = [1, 2, 3];

numbers.push(4);

console.log(numbers);
````

Output

```
[1, 2, 3, 4]
```

---

## Array.pop()  (Mutable)

Removes the **last element**.

```javascript
const numbers = [1, 2, 3];

numbers.pop();

console.log(numbers);
```

Output

```
[1, 2]
```

---

## Array.concat()  (Immutable)

Combines arrays and returns a **new array**.

```javascript
const arr1 = [1, 2];
const arr2 = [3, 4];

const result = arr1.concat(arr2);

console.log(result);
```

Output

```
[1, 2, 3, 4]
```

---

## Array.slice()  (Immutable)

Returns a **portion of an array**.

```javascript
const numbers = [10, 20, 30, 40];

const result = numbers.slice(1, 3);

console.log(result);
```

Output

```
[20, 30]
```

---

## Array.splice()  (Mutable)

Adds or removes elements from an array.

```javascript
const numbers = [1, 2, 3, 4];

numbers.splice(1, 2);

console.log(numbers);
```

Output

```
[1, 4]
```

---

## Array.join()  (Immutable)

Converts array elements into a string.

```javascript
const words = ["Hello", "JavaScript"];

const result = words.join(" ");

console.log(result);
```

Output

```
Hello JavaScript
```

---

## Array.flat()  (Immutable)

Flattens nested arrays.

```javascript
const numbers = [1, [2, 3], [4, 5]];

const result = numbers.flat();

console.log(result);
```

Output

```
[1, 2, 3, 4, 5]
```

---

# Finding

## Array.find()  (Immutable)

Returns the **first element that matches a condition**.

```javascript
const numbers = [5, 10, 15];

const result = numbers.find(num => num > 7);

console.log(result);
```

Output

```
10
```

---

## Array.indexOf()  (Immutable)

Returns the **index of an element**.

```javascript
const numbers = [10, 20, 30];

console.log(numbers.indexOf(20));
```

Output

```
1
```

---

## Array.includes()  (Immutable)

Checks if a value exists in the array.

```javascript
const fruits = ["apple", "banana"];

console.log(fruits.includes("banana"));
```

Output

```
true
```

---

## Array.findIndex()  (Immutable)

Returns the **index of the first element that matches a condition**.

```javascript
const numbers = [5, 12, 8];

const index = numbers.findIndex(num => num > 10);

console.log(index);
```

Output

```
1
```

---

# Higher Order Functions

Higher order functions take **functions as arguments**.

---

## Array.forEach()  (Mutable behavior / no return)

Executes a function for each element.

```javascript
const numbers = [1, 2, 3];

numbers.forEach(num => {
  console.log(num);
});
```

---

## Array.filter()  (Immutable)

Creates a new array with elements that pass a condition.

```javascript
const numbers = [1, 2, 3, 4];

const even = numbers.filter(num => num % 2 === 0);

console.log(even);
```

Output

```
[2, 4]
```

---

## Array.map()  (Immutable)

Transforms each element.

```javascript
const numbers = [1, 2, 3];

const doubled = numbers.map(num => num * 2);

console.log(doubled);
```

Output

```
[2, 4, 6]
```

---

## Array.reduce()  (Immutable)

Reduces an array to a single value.

```javascript
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((total, num) => total + num, 0);

console.log(sum);
```

Output

```
10
```

---

## Array.sort()  (Mutable)

Sorts elements in place.

```javascript
const numbers = [4, 1, 3, 2];

numbers.sort();

console.log(numbers);
```

Output

```
[1, 2, 3, 4]
```

---

# Advanced

## Array Method Chaining

Multiple array methods can be chained together.

```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter(num => num % 2 === 0)
  .map(num => num * 10)
  .reduce((sum, num) => sum + num, 0);

console.log(result);
```

Output

```
60
```

Explanation

```
filter → keep even numbers
map → multiply values
reduce → calculate total
```

---

# Summary

JavaScript arrays provide many utility methods.

| Category     | Examples                         |
| ------------ | -------------------------------- |
| Basics       | push, pop, concat, slice, splice |
| Finding      | find, indexOf, includes          |
| Higher Order | map, filter, reduce              |
| Advanced     | method chaining                  |

Understanding these methods helps developers write **clean, efficient, and readable code**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
