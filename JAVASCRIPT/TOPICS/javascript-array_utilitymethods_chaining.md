# Array Utility Methods Chaining in JavaScript

## Introduction

Array utility methods can be **chained together** to process data in multiple steps.

Method chaining means **calling multiple array methods one after another**.

This works because many array methods return **a new array**.

Common methods used in chaining:

```

map
filter
reduce
slice
flat
sort

```

---

# Basic Example

Instead of writing multiple steps separately, we can chain them.

### Without Chaining

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const even = numbers.filter(n => n % 2 === 0);
const doubled = even.map(n => n * 2);

console.log(doubled);
````

Output

```
[4, 8, 12]
```

---

### With Chaining

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const result = numbers
  .filter(n => n % 2 === 0)
  .map(n => n * 2);

console.log(result);
```

Output

```
[4, 8, 12]
```

This approach is **shorter and easier to read**.

---

# Example: Filter → Map → Reduce

Chain multiple operations to transform data and calculate a result.

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const sum = numbers
  .filter(n => n % 2 === 0)
  .map(n => n * 2)
  .reduce((total, n) => total + n, 0);

console.log(sum);
```

Steps

```
1. filter → keep even numbers
2. map → double the values
3. reduce → calculate total
```

Output

```
24
```

---

# Example: Working With Objects

```javascript
const users = [
  { name: "A", age: 18 },
  { name: "B", age: 25 },
  { name: "C", age: 30 }
];

const names = users
  .filter(user => user.age >= 21)
  .map(user => user.name);

console.log(names);
```

Output

```
["B", "C"]
```

---

# Example: Flatten and Process Data

```javascript
const numbers = [[1, 2], [3, 4], [5, 6]];

const result = numbers
  .flat()
  .map(n => n * 10);

console.log(result);
```

Output

```
[10, 20, 30, 40, 50, 60]
```

---

# Why Method Chaining Is Useful

Method chaining helps:

```
write cleaner code
avoid temporary variables
combine multiple operations
improve readability
```

Example:

```javascript
const result = data
  .filter(condition)
  .map(transform)
  .reduce(calculation);
```

---

# Important Note

Chaining works best with **immutable methods**.

Examples of immutable methods:

```
map
filter
slice
concat
flat
```

These methods return **new arrays**, which allows chaining.

---

# Summary

Array method chaining allows multiple operations to run in sequence on the same data.

Typical pattern:

```
array
  .filter(...)
  .map(...)
  .reduce(...)
```

This approach creates **clean, readable, and functional-style JavaScript code**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---

