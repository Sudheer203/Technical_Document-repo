# Python Cheatsheet Technical Paper

## 1. Array Methods

In Python, arrays can be represented using lists. Lists are versatile, ordered collections that allow duplicates. Python provides several built-in methods to manipulate arrays/lists.

| Method             | Description                                                                   | Example             |
| ------------------ | ----------------------------------------------------------------------------- | ------------------- |
| `append(x)`        | Adds an element `x` at the end of the list                                    | `arr.append(5)`     |
| `extend(iterable)` | Adds all elements from an iterable to the end                                 | `arr.extend([6,7])` |
| `insert(i, x)`     | Inserts element `x` at index `i`                                              | `arr.insert(1, 10)` |
| `remove(x)`        | Removes the first occurrence of `x`                                           | `arr.remove(5)`     |
| `pop([i])`         | Removes and returns element at index `i` (last element if index not provided) | `arr.pop()`         |
| `index(x)`         | Returns the index of the first occurrence of `x`                              | `arr.index(7)`      |
| `count(x)`         | Returns the number of occurrences of `x`                                      | `arr.count(7)`      |
| `sort()`           | Sorts the list in ascending order                                             | `arr.sort()`        |
| `reverse()`        | Reverses the list in place                                                    | `arr.reverse()`     |
| `copy()`           | Returns a shallow copy of the list                                            | `arr2 = arr.copy()` |

## 2. String Methods

Python strings are immutable sequences of Unicode characters. String methods allow easy manipulation and formatting.

| Method               | Description                                             | Example                                        |
| -------------------- | ------------------------------------------------------- | ---------------------------------------------- |
| `upper()`            | Converts all characters to uppercase                    | `"hello".upper()` → `"HELLO"`                  |
| `lower()`            | Converts all characters to lowercase                    | `"HELLO".lower()` → `"hello"`                  |
| `capitalize()`       | Capitalizes the first character                         | `"hello world".capitalize()` → `"Hello world"` |
| `title()`            | Capitalizes the first character of each word            | `"hello world".title()` → `"Hello World"`      |
| `strip()`            | Removes leading and trailing whitespace                 | `" hello ".strip()` → `"hello"`                |
| `replace(old, new)`  | Replaces occurrences of `old` with `new`                | `"apple".replace("a","A")` → `"Apple"`         |
| `split(sep)`         | Splits string into a list by separator                  | `"a,b,c".split(",")` → `['a','b','c']`         |
| `join(iterable)`     | Joins elements of iterable with the string as separator | `",".join(['a','b'])` → `"a,b"`                |
| `find(sub)`          | Returns index of first occurrence of substring or `-1`  | `"apple".find("p")` → `1`                      |
| `startswith(prefix)` | Checks if string starts with prefix                     | `"apple".startswith("a")` → `True`             |
| `endswith(suffix)`   | Checks if string ends with suffix                       | `"apple".endswith("e")` → `True`               |

## 3. Objects and Object-Oriented Programming (OOP)

Python is an object-oriented programming language, supporting classes, objects, inheritance, polymorphism, encapsulation, and abstraction.

### Key Concepts:

1. **Class:** A blueprint for creating objects.
2. **Object:** An instance of a class.
3. **Attributes:** Variables associated with an object.
4. **Methods:** Functions defined inside a class that operate on objects.

### Example:

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model
    
    def display(self):
        print(f"{self.brand} {self.model}")

car1 = Car("Toyota", "Corolla")
car1.display()  # Output: Toyota Corolla
```

### OOP Principles:

* **Encapsulation:** Hiding internal state using private variables (`_` or `__` prefix).
* **Inheritance:** Reusing code from parent class.
* **Polymorphism:** Same interface, different implementations.
* **Abstraction:** Hiding implementation details and exposing only necessary functions.

## 4. Decorators

Decorators are functions that modify the behavior of other functions or methods. They are often used for logging, access control, or memoization.

### Syntax:

```python
def decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before function
# Hello!
# After function
```

* `@decorator` is syntactic sugar for `say_hello = decorator(say_hello)`.
* Decorators can also accept arguments for more flexible behavior.

## 5. virtualenv

`virtualenv` is a tool to create isolated Python environments. Each environment has its own Python interpreter and installed packages, preventing conflicts between projects.

### Basic Commands:

```bash
# Install virtualenv
pip install virtualenv

# Create a new environment
virtualenv myenv

# Activate environment
# On Linux/Mac
source myenv/bin/activate
# On Windows
myenv\Scripts\activate

# Deactivate environment
deactivate
```

## 6. pip Package Manager

`pip` is the default package manager for Python, used to install, update, and remove Python packages.

### Common Commands:

```bash
# Install package
pip install package_name

# Install specific version
pip install package_name==1.0.0

# Upgrade package
pip install --upgrade package_name

# List installed packages
pip list

# Uninstall package
pip uninstall package_name
```

## 7. PEP-8 Standards Summary

PEP-8 is the official Python style guide. Following it improves readability and maintainability.

### Key Guidelines:

* **Indentation:** 4 spaces per level.
* **Line Length:** Max 79 characters.
* **Imports:** Each import on a separate line; grouped as standard, third-party, local.
* **Variables and Functions:** `snake_case`.
* **Classes:** `PascalCase`.
* **Constants:** `UPPER_CASE`.
* **Whitespace:**

  * Surround operators with spaces (`x = 1` not `x=1`).
  * No extra spaces inside parentheses.
* **Docstrings:** Use triple quotes `"""` for module, class, and function documentation.

---

### References

1. [Python Official Documentation](https://docs.python.org/3/)
2. [PEP-8 Style Guide](https://peps.python.org/pep-0008/)
3. [Python Decorators Tutorial](https://realpython.com/primer-on-python-decorators/)
