# Pass by Value and Pass by Reference in JavaScript

## Introduction

When values are passed to a function in JavaScript, they behave in two ways:

```

1. Pass by Value
2. Pass by Reference

```

Primitive types use **pass by value**.  
Objects and arrays use **pass by reference**.

---

# 1. Pass by Value

In pass by value, a **copy of the value** is passed to the function.

Changing the parameter **does not affect the original variable**.

### Example

```javascript
function changeValue(num) {
  num = num + 10;
  console.log("Inside function:", num);
}

let number = 5;

changeValue(number);

console.log("Outside function:", number);
````

Output

```
Inside function: 15
Outside function: 5
```

Explanation:

* `number` is copied into `num`
* Changes happen only to the copy
* The original value remains unchanged

---

### Example with String

```javascript
function changeName(name) {
  name = "Ravi";
}

let username = "Sudheer";

changeName(username);

console.log(username);
```

Output

```
Sudheer
```

Strings are **primitive values**, so they follow pass by value.

---

# 2. Pass by Reference

In pass by reference, the **reference (memory address)** of the object is passed.

Changes inside the function **affect the original object**.

### Example with Object

```javascript
function updateUser(user) {
  user.name = "Ravi";
}

let person = {
  name: "Sudheer"
};

updateUser(person);

console.log(person.name);
```

Output

```
Ravi
```

Explanation:

* The function receives a reference to the same object
* Changing the property modifies the original object

---

### Example with Array

```javascript
function addItem(arr) {
  arr.push(4);
}

let numbers = [1, 2, 3];

addItem(numbers);

console.log(numbers);
```

Output

```
[1, 2, 3, 4]
```

The original array is modified.

---

# Comparing Both

### Pass by Value

```javascript
let a = 10;
let b = a;

b = 20;

console.log(a);
console.log(b);
```

Output

```
10
20
```

### Pass by Reference

```javascript
let obj1 = { value: 10 };
let obj2 = obj1;

obj2.value = 20;

console.log(obj1.value);
console.log(obj2.value);
```

Output

```
20
20
```

---

# Summary

JavaScript handles function arguments in two ways:

| Type             | Behavior          |
| ---------------- | ----------------- |
| Primitive Values | Pass by Value     |
| Objects / Arrays | Pass by Reference |

Primitive values create **copies**, while objects and arrays share **references**.

Understanding this helps avoid unexpected changes in data.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---