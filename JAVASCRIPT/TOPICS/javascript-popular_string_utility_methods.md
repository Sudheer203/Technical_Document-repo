# Popular String Utility Methods in JavaScript

## Introduction

Strings are used to store **text data** in JavaScript.

Important concept:

```

Strings are immutable

```

This means **string methods never change the original string**.  
They always **return a new string or value**.

---

# Basics

## String.length (Immutable)

Returns the number of characters in a string.

```javascript
const text = "JavaScript";

console.log(text.length);
```

Output

```
10
```

---

## String.toUpperCase() (Immutable)

Converts text to uppercase.

```javascript
const text = "javascript";

const result = text.toUpperCase();

console.log(result);
```

Output

```
JAVASCRIPT
```

---

## String.toLowerCase() (Immutable)

Converts text to lowercase.

```javascript
const text = "HELLO";

const result = text.toLowerCase();

console.log(result);
```

Output

```
hello
```

---

## String.trim() (Immutable)

Removes whitespace from both ends.

```javascript
const text = "   hello   ";

const result = text.trim();

console.log(result);
```

Output

```
hello
```

---

# Extracting Strings

## String.slice() (Immutable)

Extracts part of a string.

```javascript
const text = "JavaScript";

const result = text.slice(0, 4);

console.log(result);
```

Output

```
Java
```

---

## String.substring() (Immutable)

Similar to slice but does not accept negative indexes.

```javascript
const text = "Programming";

const result = text.substring(0, 7);

console.log(result);
```

Output

```
Program
```

---

# Searching

## String.includes() (Immutable)

Checks if text exists in a string.

```javascript
const text = "JavaScript";

console.log(text.includes("Script"));
```

Output

```
true
```

---

## String.indexOf() (Immutable)

Returns the position of a substring.

```javascript
const text = "JavaScript";

console.log(text.indexOf("Script"));
```

Output

```
4
```

---

## String.startsWith() (Immutable)

Checks if a string starts with a specific value.

```javascript
const text = "JavaScript";

console.log(text.startsWith("Java"));
```

Output

```
true
```

---

## String.endsWith() (Immutable)

Checks if a string ends with a value.

```javascript
const text = "JavaScript";

console.log(text.endsWith("Script"));
```

Output

```
true
```

---

# Modifying Strings

## String.replace() (Immutable)

Replaces part of a string.

```javascript
const text = "Hello World";

const result = text.replace("World", "JavaScript");

console.log(result);
```

Output

```
Hello JavaScript
```

---

## String.repeat() (Immutable)

Repeats a string multiple times.

```javascript
const text = "JS ";

const result = text.repeat(3);

console.log(result);
```

Output

```
JS JS JS
```

---

# Converting Strings

## String.split() (Immutable)

Splits a string into an array.

```javascript
const text = "apple,banana,mango";

const result = text.split(",");

console.log(result);
```

Output

```
["apple", "banana", "mango"]
```

---

# Example Combining Methods

```javascript
const text = "  javascript programming  ";

const result = text
  .trim()
  .toUpperCase()
  .replace("PROGRAMMING", "LANGUAGE");

console.log(result);
```

Output

```
JAVASCRIPT LANGUAGE
```

---

# Summary

Important points about strings:

```
Strings are immutable
All string methods return new values
Original string never changes
```

Common string methods:

| Category   | Methods                          |
| ---------- | -------------------------------- |
| Basics     | length, toUpperCase, toLowerCase |
| Extracting | slice, substring                 |
| Searching  | includes, indexOf                |
| Modifying  | replace, repeat                  |
| Conversion | split                            |

These methods help manipulate text efficiently in JavaScript.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---