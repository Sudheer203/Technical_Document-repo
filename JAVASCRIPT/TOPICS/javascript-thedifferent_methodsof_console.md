# Console Methods in JavaScript

## Introduction

The `console` object in JavaScript is used for **debugging and logging information**.

Common console methods:

```

console.log
console.error
console.warn
console.info
console.table
console.time
console.timeEnd
console.clear
console.count

```

These help developers **inspect values, debug errors, and monitor program execution**.

---

# console.log()

`console.log()` prints general messages or values.

```javascript
const name = "Sudheer";

console.log("Hello", name);
```

Output

```
Hello Sudheer
```

Used for **general debugging and printing values**.

---

# console.error()

`console.error()` prints error messages.

```javascript
console.error("Something went wrong");
```

Output

```
Something went wrong
```

Often shown in **red color in browsers or terminals**.

Example

```javascript
function divide(a, b) {
  if (b === 0) {
    console.error("Cannot divide by zero");
  }
}
```

---

# console.warn()

`console.warn()` prints warning messages.

```javascript
console.warn("This feature is deprecated");
```

Output

```
Warning: This feature is deprecated
```

Used when something is **not an error but may cause problems**.

---

# console.info()

`console.info()` prints informational messages.

```javascript
console.info("Server started successfully");
```

Output

```
Server started successfully
```

Used to display **informational logs**.

---

# console.table()

`console.table()` displays data in **table format**.

```javascript
const users = [
  { name: "A", age: 20 },
  { name: "B", age: 25 }
];

console.table(users);
```

Output

```
(index) | name | age
0       | A    | 20
1       | B    | 25
```

Useful for **arrays of objects**.

---

# console.time() and console.timeEnd()

These measure **execution time**.

```javascript
console.time("loop");

for (let i = 0; i < 1000000; i++) {}

console.timeEnd("loop");
```

Output

```
loop: 5ms
```

Used for **performance testing**.

---

# console.count()

Counts how many times something runs.

```javascript
function test() {
  console.count("Function called");
}

test();
test();
test();
```

Output

```
Function called: 1
Function called: 2
Function called: 3
```

---

# console.clear()

Clears the console.

```javascript
console.clear();
```

Useful when logs become **too cluttered**.

---

# Practical Example

```javascript
console.info("Application starting");

const users = ["A", "B", "C"];

console.log("Users:", users);

console.warn("Demo warning");

console.error("Demo error");
```

---

# Summary

The `console` object provides multiple methods for debugging.

| Method        | Purpose             |
| ------------- | ------------------- |
| console.log   | general output      |
| console.error | errors              |
| console.warn  | warnings            |
| console.info  | informational logs  |
| console.table | display tables      |
| console.time  | measure performance |
| console.count | count executions    |

Using the right console method makes **debugging easier and logs clearer**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/API/console](https://developer.mozilla.org/en-US/docs/Web/API/console)

---