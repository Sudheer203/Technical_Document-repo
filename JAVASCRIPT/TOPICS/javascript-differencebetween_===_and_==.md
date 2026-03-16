# Difference Between `==` and `===` in JavaScript

## Introduction

JavaScript provides two operators to compare values.

Both are used for **comparison**, but they behave differently.

---

# `==` (Loose Equality)

`==` compares **values only**.

Before comparing, JavaScript **automatically converts types** if needed.

This process is called **type coercion**.

## Example

```javascript
console.log(5 == "5");
```

Output

```
true
```

Explanation

```
"5" (string) is converted to number 5
then comparison happens
```

---

## Example 2

```javascript
console.log(true == 1);
```

Output

```
true
```

Explanation

```
true → converted to 1
1 == 1 → true
```

---

## Example 3

```javascript
console.log(null == undefined);
```

Output

```
true
```

JavaScript treats them as equal when using `==`.

---

# `===` (Strict Equality)

`===` compares **both value and type**.

No type conversion happens.

## Example

```javascript
console.log(5 === "5");
```

Output

```
false
```

Explanation

```
number !== string
```

---

## Example 2

```javascript
console.log(true === 1);
```

Output

```
false
```

Explanation

```
boolean !== number
```

---

# Example Comparison

```javascript
console.log(0 == false);
console.log(0 === false);
```

Output

```
true
false
```

Explanation

```
false converts to 0 in loose comparison
strict comparison checks type
```

---

# Practical Example

```javascript
const userInput = "10";

if (userInput == 10) {
  console.log("Loose comparison matched");
}

if (userInput === 10) {
  console.log("Strict comparison matched");
}
```

Output

```
Loose comparison matched
```

Strict comparison fails because types are different.

---

# Why `===` is Recommended

Using `===` avoids unexpected type conversions.

Example problem:

```javascript
console.log("" == 0);
```

Output

```
true
```

This can cause confusing bugs.

Using strict comparison prevents this.

```javascript
console.log("" === 0);
```

Output

```
false
```

---

# Summary

| Operator | Comparison   | Type Conversion |
| -------- | ------------ | --------------- |
| `==`     | Value only   | Yes             |
| `===`    | Value + Type | No              |

Best practice:

```
Always prefer === for comparisons
```

This makes code **predictable and safer**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
