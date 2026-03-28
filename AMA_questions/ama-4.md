# AMA Questions and Answers

## 1.How to access class in JavaScript?

In JavaScript, we can access elements with a class name using **getElementsByClassName** or **querySelector**.

### Example
```javascript
// HTML
<p class="text">Hello</p>

// JavaScript
let element = document.getElementsByClassName("text");
console.log(element);
```

or

```javascript
let element = document.querySelector(".text");
console.log(element);
```

---

## 2.How to select an element by its id?

We use **getElementById()** to select an element using its id.

### Example

```javascript
// HTML
<h1 id="title">Hello</h1>

// JavaScript
let element = document.getElementById("title");
console.log(element);
```

---

## 3. What is a callback?

A **callback** is a function that is passed as an argument to another function and executed later.

### Example

```javascript
function greet(name, callback){
    console.log("Hello " + name);
    callback();
}

function sayBye(){
    console.log("Goodbye");
}

greet("Sudheer", sayBye);
```

---

## 4. Difference between GET and POST

| Feature       | GET             | POST               |
| ------------- | --------------- | ------------------ |
| Purpose       | Retrieve data   | Send data          |
| Data location | URL             | Request body       |
| Security      | Less secure     | More secure        |
| Size limit    | Limited         | Large data allowed |
| Example       | Fetch user data | Submit form        |

---

## 5. What is a Higher Order Function?

A **Higher Order Function** is a function that takes another function as an argument or returns a function.

### Example

```javascript
function calculate(a, b, operation){
    return operation(a, b);
}

function add(x, y){
    return x + y;
}

console.log(calculate(5, 3, add));
```

---

## 6. What is an Object?

An **object** is a collection of key-value pairs used to store related data.

### Example

```javascript
let person = {
    name: "Sudheer",
    age: 25,
    city: "Bangalore"
};

console.log(person.name);
```

---

## 7. What is HTML?

**HTML (HyperText Markup Language)** is the standard language used to create web pages and structure content on the web.

### Example

```html
<!DOCTYPE html>
<html>
<head>
<title>My Page</title>
</head>
<body>
<h1>Hello World</h1>
</body>
</html>
```

---

## 8. Different ways to select elements in DOM

There are multiple ways to select elements in the DOM.

### Methods

1. getElementById()
2. getElementsByClassName()
3. getElementsByTagName()
4. querySelector()
5. querySelectorAll()

### Example

```javascript
document.getElementById("id")
document.getElementsByClassName("class")
document.getElementsByTagName("p")
document.querySelector(".class")
document.querySelectorAll("p")
```

---

## 9. Explain how the Event Loop works

The **Event Loop** is responsible for handling asynchronous operations in JavaScript.

### Steps

1. JavaScript runs code in the **Call Stack**.
2. If an async task appears (setTimeout, fetch), it goes to **Web APIs**.
3. After completion, it moves to the **Callback Queue**.
4. The **Event Loop** pushes it to the **Call Stack** when the stack is empty.

### Example

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Async Task");
}, 2000);

console.log("End");
```

Output

```
Start
End
Async Task
```

---

## 10.What JS + HTML is known as a specific data structure?

JavaScript and HTML together create the **DOM (Document Object Model)**.

The DOM represents the webpage as a **tree data structure**.

### Example Structure

```
html
 ├── head
 └── body
      ├── h1
      └── p
```

---

## 11.What is setInterval?

**setInterval()** is used to repeatedly execute a function after a specified time interval.

### Example

```javascript
setInterval(() => {
    console.log("Hello");
}, 1000);
```

This prints **Hello every 1 second**.

---

## 12. Full form of HTTP

**HTTP = HyperText Transfer Protocol**

It is a protocol used for communication between **web browsers and web servers**.

---


