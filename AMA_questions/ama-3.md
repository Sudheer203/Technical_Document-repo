# AMA QUESTIONS

**Finally Block:**

“Finally block always runs, whether error happens or not.”

---

**Error Methods (Error Handling in JS)**

Common ways to handle errors:

* `try...catch` → catches runtime errors
* `throw` → creates custom error
* `finally` → always runs
  Example:

```js
try {
  let x = y; // error
} catch (e) {
  console.log("Error:", e.message);
}
```

---

**Pass by Value vs Pass by Reference**

* **Pass by Value**: copy is passed (primitives like number, string)
* **Pass by Reference**: reference is passed (objects, arrays)

```js
let a = 10;
let b = a;
b = 20; // a not affected

let obj1 = {name: "A"};
let obj2 = obj1;
obj2.name = "B"; // obj1 also changes
```

---

**Convert to Uppercase Method**
Use:

```js
let str = "hello";
console.log(str.toUpperCase()); // HELLO
```

---

**Map and Object**

* **Object**: key-value pairs, keys are strings
* **Map**: allows any data type as key, maintains order

```js
let obj = {a: 1};
let map = new Map();
map.set("a", 1);
```

---

**Is String Mutable or Immutable?**

Strings are **immutable** → cannot be changed after creation.

```js
let str = "hello";
str[0] = "H"; // no change
```

---

**if (" ") True or False?**

```js
if (" ") → TRUE
```

Reason: non-empty string (even space) is **truthy**.

---

**Difference Between `==` and `===`**

* `==` → compares value only (type conversion happens)
* `===` → compares value + type (strict)

```js
5 == "5"   // true
5 === "5"  // false
```

---

**Two Phases of Execution (JS)**

1. **Memory Creation Phase** → variables & functions stored
2. **Execution Phase** → code runs line by line

---

**Some Array Methods**

* `push()` → add element
* `pop()` → remove last
* `map()` → transform array
* `filter()` → filter values
* `reduce()` → reduce to single value

---

**Types of Scopes**

* Global scope
* Function scope
* Block scope (`let`, `const`)

---

**Concatenate Arrays Methods**

```javascript
let a = [1,2];
let b = [3,4];

a.concat(b);       // [1,2,3,4]
[...a, ...b];      // spread method
```

---

**Falsy and Truthy Values**

Falsy values:

```js
false, 0, "", null, undefined, NaN
```

Everything else → truthy

---

**`every()` Method**

Checks if all elements satisfy condition

```js
[2,4,6].every(x => x % 2 === 0); // true
```

---

**Primitive Datatypes Mutable or Immutable**

Primitive types are **immutable**
(number, string, boolean, null, undefined, symbol, bigint)

---

**Key Error (General Concept)**

A **Key Error** happens when you try to access a key that does not exist.

Example (JS):

```js
let obj = {a: 1};
console.log(obj.b); // undefined (no key)
```
---
