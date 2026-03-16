# Searching in JavaScript (Based on MDN)

## Introduction

Searching means **finding a value inside data** such as strings or arrays.

JavaScript provides multiple built-in methods for searching.  
These methods are documented in **MDN (Mozilla Developer Network)**, which is a reference for JavaScript language features and APIs.

Common searching methods include:

```

1. String search
2. Array indexOf
3. Array find
4. Array findIndex
5. Array includes

```

---

# 1. Searching in Strings

JavaScript provides the `search()` method to find a pattern inside a string.

It returns the **index of the first match** or `-1` if not found. :contentReference[oaicite:1]{index=1}

### Example

```javascript
const text = "JavaScript is powerful";

let result = text.search("Script");

console.log(result);
```

Output

```
4
```

Example when value is not found:

```javascript
const text = "JavaScript";

console.log(text.search("Python"));
```

Output

```
-1
```

---

# 2. Searching in Arrays with indexOf

`indexOf()` returns the **index of a value** in an array.

### Example

```javascript
const numbers = [10, 20, 30, 40];

console.log(numbers.indexOf(30));
```

Output

```
2
```

If the value is not found:

```javascript
console.log(numbers.indexOf(50));
```

Output

```
-1
```

---

# 3. Searching with find()

`find()` returns the **first element that matches a condition**. ([MDN Web Docs][1])

### Example

```javascript
const numbers = [5, 12, 8, 130, 44];

let result = numbers.find((num) => num > 10);

console.log(result);
```

Output

```
12
```

---

# 4. Searching with findIndex()

`findIndex()` returns the **index of the first matching element**.

### Example

```javascript
const numbers = [5, 12, 8, 130];

let index = numbers.findIndex((num) => num > 10);

console.log(index);
```

Output

```
1
```

---

# 5. Searching with includes()

`includes()` checks if a value exists in an array.

### Example

```javascript
const fruits = ["apple", "banana", "mango"];

console.log(fruits.includes("banana"));
```

Output

```
true
```

Example when not found:

```javascript
console.log(fruits.includes("orange"));
```

Output

```
false
```

---

# Example Comparing Search Methods

```javascript
const numbers = [10, 20, 30, 40];

console.log(numbers.indexOf(20));   // index
console.log(numbers.includes(30));  // true/false
console.log(numbers.find(n => n > 25)); 
console.log(numbers.findIndex(n => n > 25));
```

Output

```
1
true
30
2
```

---

# Summary

JavaScript provides several ways to search for values.

| Method      | Use                          |
| ----------- | ---------------------------- |
| search()    | Search inside strings        |
| indexOf()   | Find index of value          |
| find()      | Find element using condition |
| findIndex() | Find index using condition   |
| includes()  | Check if value exists        |

These methods help developers quickly locate data in **strings and arrays**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---