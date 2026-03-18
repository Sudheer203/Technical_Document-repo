# JavaScript Loop Types

## 1. Introduction

In JavaScript, 
- loops are used to repeat a block of code multiple times.
- Instead of writing the same code again and again, we use loops to perform repeated tasks automatically.

Example:

If we want to print numbers from 1 to 5:

Without loop

```javascript
console.log(1)
console.log(2)
console.log(3)
console.log(4)
console.log(5)
```

This is not efficient.  
So we use loops.

### JavaScript provides different types of loops.

1. for loop
2. for...in loop
3. for...of loop
4. forEach() method
5. while loop

Reference: **MDN (Mozilla Developer Network)**

---

# 2. for Loop (Number Loop)

## What is a for loop?

The `for` loop is used when we know how many times the loop should run.

## Syntax

```javascript
for (initialization; condition; increment) {
   code
}
```
## Example

```javascript
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
````

## How it works step by step

1. Initialization -
   `let i = 1`

2. Condition check -
   `i <= 5`

3. Run the code inside the loop

4. Increment - 
   `i++`

5. Repeat until condition becomes - **false**

Output
```
1
2
3
4
5
```
---

# 3. for...in Loop

## What is for...in?

The `for...in` loop is used to iterate through the **keys of an object**.

It returns the **property name**.

## Syntax

```javascript
for (let key in object) {
code
}
```

## Example

```javascript
const student = {
  name: "John",
  age: 22,
  course: "JavaScript"
};

for (let key in student) {
  console.log(key, student[key]);
}
```

Output

```
name John
age 22
course JavaScript
```
---

# 4. for...of Loop

## What is for...of?

The `for...of` loop is used to iterate through **values of an array or iterable object**.

It directly gives the value.

## Syntax

```javascript
for (let value of array) {
code
}
```
## Example

```javascript
const numbers = [10, 20, 30, 40];

for (let num of numbers) {
  console.log(num);
}
```

Output

```
10
20
30
40
```
---

# 5. forEach() Method

## What is forEach?

`forEach()` is an array method used to execute a function for each element of the array.

It is commonly used for array operations.

## Syntax

```javascript
array.forEach(function(element){
code
})
```
## Example

```javascript
const colors = ["red", "green", "blue"];

colors.forEach(function(color) {
  console.log(color);
});
```

Output

```
red
green
blue
```
 - Arrow function version

```javascript
colors.forEach(color => console.log(color));
```

---

# 6. while Loop

## What is a while loop?

A `while` loop runs as long as the condition is true.

It is useful when we don't know exactly how many times the loop should run.

## Syntax

```javascript
while (condition) {
code
}
```

## Example

```javascript
let i = 1;

while (i <= 5) {
  console.log(i);
  i++;
}
```

Output

```
1
2
3
4
5
```
---

# 7. Comparison of Loops

| Loop     | Used For                                |
| -------- | --------------------------------------- |
| for      | When number of iterations is known      |
| for...in | Iterating object properties             |
| for...of | Iterating array values                  |
| forEach  | Running function for each array element |
| while    | Loop runs until condition becomes false |

---

# 8. Conclusion

Loops help developers write cleaner and shorter code.

They are very useful when working with:

* Arrays
* Objects
* Data processing
* Repeated tasks

Understanding loops is an important step in learning JavaScript.

---

# 9. References

MDN Web Docs

[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
