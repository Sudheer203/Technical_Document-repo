# Python Module vs Python Class 

## 1. Introduction

In Python programming, **modules** and **classes** are fundamental concepts used to organize code.

Although both help structure programs, they serve **different purposes**.

Understanding the difference between a **module** and a **class** is important for writing **clean, reusable, and maintainable Python code**.

---

# 2. What is a Python Module?

A **module** is a **Python file (`.py`) that contains code** such as:

* Functions
* Classes
* Variables
* Constants

Modules help **organize code into separate files**, making large programs easier to manage.

### Example Module

File name:

```
math_operations.py
```

Code:

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b
```

### Importing a Module

You can use the module in another file:

```python
import math_operations

result = math_operations.add(5, 3)
print(result)
```

Output:

```
8
```

### Purpose of Modules

Modules help:

* Organize code into separate files
* Improve code readability
* Reuse code across projects

---

# 3. What is a Python Class?

A **class** is a **blueprint for creating objects**.

Classes define:

* **Attributes** (data)
* **Methods** (functions inside the class)

Objects created from a class contain **data and behavior**.

### Example Class

```python
class Car:

    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def start(self):
        print("Car started")
```

### Creating an Object

```python
my_car = Car("Toyota", "Camry")
my_car.start()
```

Output:

```
Car started
```

### Purpose of Classes

Classes help:

* Represent real-world objects
* Group related data and functions
* Support **object-oriented programming (OOP)**

---

# 4. Key Differences Between Module and Class

| Feature        | Module                        | Class                            |
| -------------- | ----------------------------- | -------------------------------- |
| Definition     | A Python file containing code | A blueprint for creating objects |
| File Structure | Stored as `.py` file          | Defined inside a module          |
| Purpose        | Organize code                 | Define object behavior           |
| Contains       | Functions, classes, variables | Methods and attributes           |
| Usage          | Imported using `import`       | Instantiated to create objects   |

---

# 5. Relationship Between Module and Class

A **module can contain multiple classes**.

Example:

```
project/
│
├── vehicles.py
```

Inside `vehicles.py`:

```python
class Car:
    pass

class Bike:
    pass
```

Another file can import the module:

```python
from vehicles import Car

car = Car()
```

So the hierarchy is:

```
Module → contains Classes → creates Objects
```

---

# 6. Real World Example

Example structure of a Python project:

```
project/
│
├── models.py      (module)
├── views.py       (module)
├── utils.py       (module)
```

Inside `models.py`:

```python
class User:
    pass

class Product:
    pass
```

Here:

* `models.py` is a **module**
* `User` and `Product` are **classes**

---

# 7. Advantages of Using Modules and Classes

### Modules

* Code organization
* Reusability
* Separation of concerns

### Classes

* Encapsulation
* Code reuse using inheritance
* Object-oriented design

---

# 8. Conclusion

Modules and classes both help organize Python programs, but they operate at different levels.

Key points:

* A **module** is a Python file that groups related code.
* A **class** is a blueprint used to create objects.
* Modules can contain multiple classes and functions.
* Classes support **object-oriented programming** concepts.

Understanding this distinction helps developers design **clean, modular, and scalable Python applications**.

---
