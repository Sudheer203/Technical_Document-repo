
# JavaScript Data Types

## Introduction

- **JavaScript** is a dynamically typed language. 
- This means variables can store different types of values without specifying the type.

Example:

```javascript
let value = 10;
value = "Hello";
````

In **JavaScript**, data types are divided into two main groups:

1. Primitive Data Types
2. Non-Primitive (Reference) Data Types

---

# 1. Primitive Data Types

Primitive data types store **single values** and are **immutable**.

JavaScript has **7 primitive types**.

```
String
Number
Boolean
Undefined
Null
Symbol
BigInt
```

---

## 1.1 String

A **string** represents text.

Example:

```javascript
let name = "Sudheer";
let message = 'Hello World';

console.log(name);
console.log(typeof name);
```

Output

```
Sudheer
string
```

**Strings can use:**

```
"double quotes"
'single quotes'
`backticks`
```

Example with template string:

```javascript
let name = "Sudheer";
console.log(`Hello ${name}`);
```

---

## 1.2 Number

The **number** type represents both integers and floating point numbers.

Example:

```javascript
let age = 25;
let price = 99.99;

console.log(age);
console.log(typeof age);
```

JavaScript also has special numbers:

```javascript
console.log(Infinity);
console.log(-Infinity);
console.log(NaN);
```

Example:

```javascript
console.log(10 / 0);   // Infinity
console.log("text" / 2); // NaN
```

---

## 1.3 Boolean

Boolean represents **true or false** values.

Example:

```javascript
let isStudent = true;
let isLoggedIn = false;

console.log(isStudent);
console.log(typeof isStudent);
```

Boolean is often used in **conditions**.

Example:

```javascript
let age = 20;

if (age > 18) {
  console.log("Adult");
}
```

---

## 1.4 Undefined

A variable that is declared but **not assigned a value** has the type **undefined**.

Example:

```javascript
let data;

console.log(data);
console.log(typeof data);
```

Output

```
undefined
```

---

## 1.5 Null

`null` represents **intentional empty value**.

Example:

```javascript
let user = null;

console.log(user);
```

Example use case:

```javascript
let selectedUser = null;
```

Meaning: **no user selected yet**.

Note:

```javascript
console.log(typeof null);
```

Output:

```
object
```

This is a **known JavaScript bug**.

---

## 1.6 Symbol

A **Symbol** creates a **unique identifier**.

Example:

```javascript
let id1 = Symbol("id");
let id2 = Symbol("id");

console.log(id1 === id2);
```

Output

```
false
```

Symbols are mostly used for **object property keys**.

Example:

```javascript
let id = Symbol("id");

let user = {
  name: "Sudheer",
  [id]: 123
};

console.log(user[id]);
```

---

## 1.7 BigInt

BigInt is used for **very large integers**.

Example:

```javascript
let bigNumber = 123456789012345678901234567890n;

console.log(bigNumber);
console.log(typeof bigNumber);
```

Without BigInt, JavaScript numbers lose precision.

---

# 2. Non-Primitive (Reference) Data Types

Non-primitive types store **collections of values**.

The main reference types are:

```
Object
Array
Function
```

---

## 2.1 Object

Objects store **key-value pairs**.

Example:

```javascript
let person = {
  name: "Sudheer",
  age: 25,
  city: "Bangalore"
};

console.log(person.name);
console.log(person.age);
```

Accessing properties:

```javascript
person.name
person["age"]
```

---

## 2.2 Array

Arrays store **multiple values in order**.

Example:

```javascript
let numbers = [10, 20, 30, 40];

console.log(numbers[0]);
console.log(numbers.length);
```

Arrays can store mixed data types:

```javascript
let data = ["Sudheer", 25, true];
```

---

## 2.3 Function

Functions are also objects in JavaScript.

Example:

```javascript
function greet(name) {
  return "Hello " + name;
}

console.log(greet("Sudheer"));
```

Functions can be stored in variables.

Example:

```javascript
let add = function(a, b) {
  return a + b;
};

console.log(add(5, 3));
```

---

# Checking Data Types

JavaScript provides the **typeof operator**.

Example:

```javascript
console.log(typeof "Hello");   // string
console.log(typeof 10);        // number
console.log(typeof true);      // boolean
console.log(typeof undefined); // undefined
console.log(typeof null);      // object
console.log(typeof {});        // object
console.log(typeof []);        // object
console.log(typeof function(){}); // function
```

---

# Summary

JavaScript data types are divided into **primitive** and **reference types**.

Primitive types store **single values** and are immutable.

Reference types store **collections of data**.

Understanding data types is important because they affect how values are stored, compared, and manipulated in JavaScript programs.

---

# References

MDN Web Docs

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

--- 