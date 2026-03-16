# Destructuring in JavaScript

## Introduction

Destructuring is a JavaScript feature that allows us to **extract values from arrays or properties from objects** and assign them to variables.

It makes code **shorter and easier to read**.

---

# Array Destructuring

Array destructuring extracts values based on **position (index)**.

## Example

```javascript
const numbers = [10, 20, 30];

const [a, b, c] = numbers;

console.log(a);
console.log(b);
console.log(c);
```

Output

```
10
20
30
```

---

## Skipping Values

You can skip elements using commas.

```javascript
const numbers = [10, 20, 30];

const [first, , third] = numbers;

console.log(first);
console.log(third);
```

Output

```
10
30
```

---

## Default Values

Default values are used when the array does not have enough elements.

```javascript
const numbers = [5];

const [a, b = 10] = numbers;

console.log(a);
console.log(b);
```

Output

```
5
10
```

---

# Object Destructuring

Object destructuring extracts values based on **property names**.

## Example

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const { name, age } = user;

console.log(name);
console.log(age);
```

Output

```
Sudheer
25
```

---

## Renaming Variables

You can rename variables while destructuring.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const { name: userName, age: userAge } = user;

console.log(userName);
console.log(userAge);
```

Output

```
Sudheer
25
```

---

## Default Values in Objects

```javascript
const user = {
  name: "Sudheer"
};

const { name, age = 20 } = user;

console.log(name);
console.log(age);
```

Output

```
Sudheer
20
```

---

# Destructuring in Function Parameters

Destructuring can be used directly in function parameters.

```javascript
function printUser({ name, age }) {
  console.log(name);
  console.log(age);
}

const user = {
  name: "Sudheer",
  age: 25
};

printUser(user);
```

Output

```
Sudheer
25
```

---

# Destructuring Arrays in Functions

```javascript
function printNumbers([a, b]) {
  console.log(a);
  console.log(b);
}

printNumbers([1, 2]);
```

Output

```
1
2
```

---

# Practical Example

```javascript
const product = {
  name: "Laptop",
  price: 50000,
  brand: "Dell"
};

const { name, price } = product;

console.log(`${name} costs ${price}`);
```

Output

```
Laptop costs 50000
```

---

# Summary

Destructuring helps extract values from arrays and objects easily.

Common patterns:

```
Array → const [a, b] = arr
Object → const {name, age} = obj
```

Benefits:

* shorter code
* cleaner variable assignments
* easier data extraction

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
