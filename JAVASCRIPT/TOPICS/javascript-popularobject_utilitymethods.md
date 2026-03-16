# Popular Object Utility Methods in JavaScript

## Introduction

Objects store **key–value pairs** in JavaScript.

JavaScript provides several **object utility methods** to read, copy, and modify objects.

Important idea:

```

Mutable   → modifies the original object
Immutable → returns a new object/value without changing the original

```

---

# Object.keys() (Immutable)

Returns an **array of object keys**.

```javascript
const user = {
  name: "Sudheer",
  age: 25,
  city: "Hyderabad"
};

const keys = Object.keys(user);

console.log(keys);
```

Output

```
["name", "age", "city"]
```

---

# Object.values() (Immutable)

Returns an **array of object values**.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const values = Object.values(user);

console.log(values);
```

Output

```
["Sudheer", 25]
```

---

# Object.entries() (Immutable)

Returns an **array of key-value pairs**.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const entries = Object.entries(user);

console.log(entries);
```

Output

```
[["name","Sudheer"],["age",25]]
```

---

# Object.assign() (Mutable)

Copies properties from one object to another.

```javascript
const target = { a: 1 };
const source = { b: 2 };

Object.assign(target, source);

console.log(target);
```

Output

```
{ a: 1, b: 2 }
```

The **target object is modified**, so this method is mutable.

---

# Object.freeze() (Mutable behavior)

Prevents modification of an object.

```javascript
const user = {
  name: "Sudheer"
};

Object.freeze(user);

user.name = "Ravi";

console.log(user);
```

Output

```
{ name: "Sudheer" }
```

Changes are **not allowed after freezing**.

---

# Object.seal() (Mutable behavior)

Prevents adding or removing properties but allows updating existing values.

```javascript
const user = {
  name: "Sudheer"
};

Object.seal(user);

user.name = "Ravi";
user.age = 25;

console.log(user);
```

Output

```
{ name: "Ravi" }
```

`age` cannot be added.

---

# Object.hasOwn() (Immutable)

Checks if a property exists in the object.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

console.log(Object.hasOwn(user, "name"));
console.log(Object.hasOwn(user, "city"));
```

Output

```
true
false
```

---

# Object Spread (Immutable)

Creates a **new object copy**.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const newUser = { ...user, city: "Hyderabad" };

console.log(newUser);
```

Output

```
{ name: "Sudheer", age: 25, city: "Hyderabad" }
```

Original object remains unchanged.

---

# Example: Looping Object Data

```javascript
const user = {
  name: "Sudheer",
  age: 25,
  city: "Hyderabad"
};

Object.entries(user).forEach(([key, value]) => {
  console.log(key, value);
});
```

Output

```
name Sudheer
age 25
city Hyderabad
```

---

# Summary

JavaScript objects have several useful utility methods.

| Method           | Behavior             |
| ---------------- | -------------------- |
| Object.keys()    | Immutable            |
| Object.values()  | Immutable            |
| Object.entries() | Immutable            |
| Object.assign()  | Mutable              |
| Object.freeze()  | Prevent modification |
| Object.seal()    | Restrict structure   |

These methods help developers **read, copy, and control object data efficiently**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---