# Template Literals in JavaScript

## Introduction

Template literals are a modern way to create **strings in JavaScript**.

They allow:

- string interpolation (embedding variables)
- multi-line strings
- embedded expressions

Template literals use **backticks** instead of quotes.

```

` `

```

---

# Basic Syntax

```javascript
const name = "Sudheer";

const message = `Hello ${name}`;

console.log(message);
````

Output

```
Hello Sudheer
```

`${}` is used to **insert variables or expressions** inside a string.

---

# 1. String Concatenation (Old vs New)

## Old Method

```javascript
const name = "Sudheer";
const age = 25;

const message = "My name is " + name + " and I am " + age + " years old";

console.log(message);
```

Output

```
My name is Sudheer and I am 25 years old
```

## Using Template Literals

```javascript
const name = "Sudheer";
const age = 25;

const message = `My name is ${name} and I am ${age} years old`;

console.log(message);
```

Template literals make the code **cleaner and easier to read**.

---

# 2. Multi-line Strings

Before template literals, multi-line strings were difficult.

## Old Method

```javascript
const text = "Hello\n" +
             "Welcome\n" +
             "JavaScript";

console.log(text);
```

## Using Template Literals

```javascript
const text = `Hello
Welcome
JavaScript`;

console.log(text);
```

Output

```
Hello
Welcome
JavaScript
```

---

# 3. Using Expressions Inside Strings

Template literals allow **JavaScript expressions** inside `${}`.

```javascript
const a = 5;
const b = 10;

const result = `The sum is ${a + b}`;

console.log(result);
```

Output

```
The sum is 15
```

---

# 4. Using Function Calls

Functions can also be used inside template literals.

```javascript
function greet(name) {
  return `Hello ${name}`;
}

const message = `${greet("Sudheer")}, welcome!`;

console.log(message);
```

Output

```
Hello Sudheer, welcome!
```

---

# 5. Building Dynamic Strings

Template literals are useful when building dynamic messages.

```javascript
const product = "Laptop";
const price = 50000;

const message = `The price of ${product} is ${price}`;

console.log(message);
```

Output

```
The price of Laptop is 50000
```

---

# Example: Creating HTML

Template literals are often used to generate HTML.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const html = `
<div>
  <h1>${user.name}</h1>
  <p>Age: ${user.age}</p>
</div>
`;

console.log(html);
```

---

# Benefits

```
Cleaner string creation
Supports multi-line text
Allows expressions inside strings
Improves readability
```

---

# Summary

Template literals provide a **modern and powerful way to work with strings in JavaScript**.

Key syntax:

```
`string ${expression}`
```

They make code **shorter, clearer, and easier to maintain**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
