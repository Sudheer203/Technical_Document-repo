# Python Cheatsheet

## 1. **Python Concepts**

* **Variable** – Store data

  ```python
  name = "Sudheer"
  age = 24
  ```
* **Data Types** – Common types:

  * `int` - 5
  * `float` - 5.6
  * `str` - "Hello"
  * `bool` - True / False
  * `list` - [1,2,3]
  * `dict` - {"key": "value"}
* **Conditional Statements** – if/elif/else

  ```python
  if age > 18:
      print("Adult")
  else:
      print("Minor")
  ```
* **Loops** – Repeat actions

  ```python
  for i in range(3):
      print(i)  # 0,1,2
  ```

  ```python
  while age < 30:
      print(age)
      age += 1
  ```
* **Functions** – Reusable code blocks

  ```python
  def greet(name):
      return f"Hello, {name}"
  print(greet("Sudheer"))
  ```
* **Classes & Objects** – OOP basics

  ```python
  class Person:
      def __init__(self, name, age):
          self.name = name
          self.age = age
  p = Person("Sudheer", 24)
  print(p.name)
  ```

---

## 2. **Popular String Methods**

| Method         | Purpose                | Example                                |
| -------------- | ---------------------- | -------------------------------------- |
| `upper()`      | Converts to uppercase  | `"hello".upper()` -- `"HELLO"`          |
| `lower()`      | Converts to lowercase  | `"HELLO".lower()` --`"hello"`          |
| `strip()`      | Removes spaces at ends | `"  hi  ".strip()` -- `"hi"`            |
| `replace()`    | Replace substring      | `"apple".replace("a","o")` -- `"opple"` |
| `split()`      | Split into list        | `"a,b,c".split(",")` -- `['a','b','c']` |
| `join()`       | Join list into string  | `",".join(['a','b','c'])` -- `"a,b,c"`  |
| `find()`       | Find substring index   | `"apple".find("p")` -- `1`              |
| `startswith()` | Check start            | `"apple".startswith("a")` -- `True`     |
| `endswith()`   | Check end              | `"apple".endswith("e")` -- `True`       |

---

## 3. **Popular List Methods**

| Method      | Purpose                  | Example                             |
| ----------- | ------------------------ | ----------------------------------- |
| `append()`  | Add single item          | `lst.append(4)` -- `[1,2,3,4]`       |
| `extend()`  | Add multiple items       | `lst.extend([4,5])` -- `[1,2,3,4,5]` |
| `insert()`  | Insert at index          | `lst.insert(1,99)` -- `[1,99,2,3]`   |
| `remove()`  | Remove first occurrence  | `lst.remove(2)` -- `[1,3]`           |
| `pop()`     | Remove by index & return | `lst.pop(0)` -- `1`                  |
| `sort()`    | Sort list                | `lst.sort()` -- `[1,2,3]`            |
| `reverse()` | Reverse list             | `lst.reverse()` -- `[3,2,1]`         |
| `count()`   | Count occurrences        | `lst.count(2)` -- `1`                |
| `index()`   | Find index of item       | `lst.index(3)` -- `2`                |

---

## 4. **Popular Dictionary Methods**

| Method     | Purpose                   | Example                                       |
| ---------- | ------------------------- | --------------------------------------------- |
| `keys()`   | Get all keys              | `d.keys()` -- `dict_keys(['a','b'])`           |
| `values()` | Get all values            | `d.values()` -- `dict_values([1,2])`           |
| `items()`  | Get key-value pairs       | `d.items()` -- `dict_items([('a',1),('b',2)])` |
| `get()`    | Get value safely          | `d.get('a')` -- `1`                            |
| `pop()`    | Remove key & return value | `d.pop('a')` -- `1`                            |
| `update()` | Add/update key-value      | `d.update({'c':3})` -- `{'a':1,'b':2,'c':3}`   |
| `clear()`  | Remove all items          | `d.clear()` -- `{}`                            |

---

