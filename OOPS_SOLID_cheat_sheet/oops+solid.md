#  Object Oriented Programming (OOP)
---
## 🔹 What is OOP?

OOP (Object Oriented Programming) is a programming style that uses:

- Classes
- Objects

### Real World Example

- Car → Blueprint (Class)
- My Car → Object

---

# 4 - Main Pillars of OOP

1. Encapsulation  
2. Abstraction  
3. Inheritance  
4. Polymorphism  

---

## 1. Encapsulation

### Definition
Encapsulation means hiding data and allowing access only through methods.

### Example

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # private variable

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance


account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())
````

### Key Points

* `__balance` is private
* Cannot access directly
* Use methods to modify data

---

## 2. Abstraction

### Definition

Abstraction hides internal implementation and shows only essential features.

### Example

```python
from abc import ABC, abstractmethod


class Shape(ABC):

    @abstractmethod
    def area(self):
        pass


class Circle(Shape):

    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius


c = Circle(5)
print(c.area())
```

### Key Points

* Abstract class defines rules
* Child class must implement methods

---

## 3. Inheritance

###  Definition

Inheritance allows a child class to reuse properties and methods of a parent class.

### Example

```python
class Animal:

    def speak(self):
        print("Animal makes sound")


class Dog(Animal):

    def bark(self):
        print("Dog barks")


d = Dog()
d.speak()
d.bark()
```

### Key Points

* Code reuse
* Child class extends parent behavior

---

## 4. Polymorphism

### Definition

Polymorphism means same method name, different behavior.

### Example

```python
class Cat:
    def sound(self):
        print("Meow")


class Dog:
    def sound(self):
        print("Bark")


def make_sound(animal):
    animal.sound()


make_sound(Cat())
make_sound(Dog())
```

### Key Points

* Same method name
* Different output
* Works with multiple objects

---

# OOP Summary

| Concept       | Meaning                         |
| ------------- | ------------------------------- |
| Encapsulation | Hide data                       |
| Abstraction   | Hide implementation             |
| Inheritance   | Reuse code                      |
| Polymorphism  | Same method, different behavior |

---

---

# SOLID Principles

SOLID is a set of 5 design principles for writing clean and maintainable code.

---

## S — Single Responsibility Principle (SRP)

###  Definition

A class should have only one responsibility.

###  Wrong Example

```python
class Report:

    def generate(self):
        print("Generating report")

    def save(self):
        print("Saving report")
```

###  Correct Example

```python
class ReportGenerator:

    def generate(self):
        print("Generating report")


class ReportSaver:

    def save(self):
        print("Saving report")
```

---

## O — Open/Closed Principle (OCP)

###  Definition

Open for extension, closed for modification.

```python
class Discount:

    def get_discount(self):
        return 0


class FestivalDiscount(Discount):

    def get_discount(self):
        return 20
```

---

## L — Liskov Substitution Principle (LSP)

###  Definition

Child classes should replace parent classes without breaking the program.

### Wrong Example

```python
class Bird:
    def fly(self):
        print("Flying")


class Penguin(Bird):
    def fly(self):
        raise Exception("Penguins cannot fly")
```

---

## I — Interface Segregation Principle (ISP)

### Definition

Do not force a class to implement methods it does not use.

### Better Example

```python
class Workable:
    def work(self):
        pass


class Eatable:
    def eat(self):
        pass
```

---

## D — Dependency Inversion Principle (DIP)

### Definition

Depend on abstractions, not concrete classes.

```python
class Keyboard:
    pass


class Computer:

    def __init__(self, keyboard):
        self.keyboard = keyboard
```

---

# SOLID Summary

| Letter | Principle             |
| ------ | --------------------- |
| S      | Single Responsibility |
| O      | Open/Closed           |
| L      | Liskov Substitution   |
| I      | Interface Segregation |
| D      | Dependency Inversion  |

---

#  Final Conclusion

* OOP helps structure your code.
* SOLID helps design clean and scalable software.
* OOP = Building blocks.
* SOLID = Design rules.

---
----