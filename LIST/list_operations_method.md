# PYTHON LIST – COMPLETE OPERATIONS & METHODS
##  What is a List?

A **list** is like a box that can store many values in one place.

Example:

```python
numbers = [1, 2, 3, 4, 5]
```

This list stores 5 numbers.

You can store:

* Numbers   - `[1, 2, 3]`
* Strings   - `["apple", "banana"]`
* Mixed     - `[1, "apple", 3.5]` (not recommended but possible)
---
# PART 1: LIST OPERATIONS (Using Symbols & Built-in Functions)

**Operations** are general actions we perform on lists.

---

## 1.Create a List

```python
numbers = [10, 20, 30]
```

Creates a list with 3 values.

---

## 2. Access Element (Using Index)

```python
numbers = [10, 20, 30]
print(numbers[1])
```

Output:

```
20
```

Index starts from 0.

---

## 3. Negative Index

```python
numbers = [10, 20, 30]
print(numbers[-1])
```

Output:

```
30
```

`-1` means last element.

---

## 4. Change Value

```python
numbers = [10, 20, 30]
numbers[1] = 50
print(numbers)
```

Output:

```
[10, 50, 30]
```

**Lists are changeable (mutable).**

---

## 5. Length (Count items)

```python
numbers = [10, 20, 30]
print(len(numbers))
```

Output:

```
3
```

---

## 6. Join Lists (+)

```python
a = [1, 2]
b = [3, 4]
print(a + b)
```

Output:

```
[1, 2, 3, 4]
```

---

## 7. Repeat List (*)

```python
numbers = [1, 2]
print(numbers * 2)
```

Output:

```
[1, 2, 1, 2]
```

---

## 8.Check Value Exists (in)

```python
numbers = [10, 20, 30]
print(20 in numbers)
```

Output:

```
True
```

---

## 9. Slicing (Get part of list)

```python
numbers = [1, 2, 3, 4, 5]
print(numbers[1:4])
```

Output:

```
[2, 3, 4]
```
Start from index 1, stop before 4.

---

## 10. Delete using del

```python
numbers = [10, 20, 30]
del numbers[1]
print(numbers)
```

Output:

```
[10, 30]
```

---

# PART 2: LIST METHODS (Built-in List Functions)

Methods use dot `.` after list name.

---

## 1. append()

Add one item at end.

```python
numbers = [1, 2]
numbers.append(3)
print(numbers)
```

Output:

```
[1, 2, 3]
```

---

## 2. extend()

Add multiple items.

```python
numbers = [1, 2]
numbers.extend([3, 4])
print(numbers)
```

Output:

```
[1, 2, 3, 4]
```

---

## 3. insert()

Insert at specific position.

```python
numbers = [1, 3]
numbers.insert(1, 2)
print(numbers)
```

Output:

```
[1, 2, 3]
```

---

## 4. remove()

Remove by value.

```python
numbers = [1, 2, 2]
numbers.remove(2)
print(numbers)
```

Output:

```
[1, 2]
```

---

## 5. pop()

Remove last item and return it.

```python
numbers = [1, 2, 3]
numbers.pop()
print(numbers)
```

Output:

```
[1, 2]
```

You can also remove **specific index**:

```python
numbers.pop(0)
```

---

## 6. clear()

Remove all items.

```python
numbers = [1, 2, 3]
numbers.clear()
print(numbers)
```

Output:

```
[]
```

---

## 7. index()

Find position of value.

```python
numbers = [10, 20, 30]
print(numbers.index(20))
```

Output:

```
1
```

---

## 8. count()

Count occurrences.

```python
numbers = [1, 2, 2, 3]
print(numbers.count(2))
```

Output:

```
2
```

---

## 9. sort()

Sort ascending.

```python
numbers = [3, 1, 2]
numbers.sort()
print(numbers)
```

Output:

```
[1, 2, 3]
```

Descending:

```python
numbers.sort(reverse=True)
```

---

## 10. reverse()

Reverse list.

```python
numbers = [1, 2, 3]
numbers.reverse()
print(numbers)
```

Output:

```
[3, 2, 1]
```

---

## 11. copy()

Create copy of list.

```python
numbers = [1, 2, 3]
new_list = numbers.copy()
print(new_list)
```

Output:

```
[1, 2, 3]
```
---

# Python List – Complete Operations & Methods

## List Operations (Symbol Based)

| No | Operation | Syntax             | Example        | Output     |
|----|-----------|--------------------|----------------|------------|
| 1  | Create    | `[]`               | `a = [1, 2]`   | `[1, 2]`   |
| 2  | Access    | `a[index]`         | `a[1]`         | `2`        |
| 3  | Modify    | `a[index] = value` | `a[0] = 9`     | `[9, 2]`   |
| 4  | Join      | `+`                | `[1,2] + [3]`  | `[1,2,3]`  |
| 5  | Repeat    | `*`                | `[1] * 3`      | `[1,1,1]`  |
| 6  | Check     | `in`               | `2 in [1,2,3]` | `True`     |
| 7  | Length    | `len(a)`           | `len([1,2])`   | `2`        |
| 8  | Slice     | `a[start:end]`     | `[1,2,3][0:2]` | `[1,2]`    |
| 9  | Delete    | `del a[index]`     | `del a[0]`     | Item removed |

---

## List Methods (Dot Methods)

| No | Method   | Syntax           | Purpose            | Example                   | Output       |
|----|----------|------------------|--------------------|---------------------------|--------------|
| 1  | append() | `a.append(x)`    | Add one item       | `a=[1]; a.append(2)`      | `[1,2]`      |
| 2  | extend() | `a.extend(list)` | Add multiple items | `a=[1]; a.extend([2,3])`  | `[1,2,3]`    |
| 3  | insert() | `a.insert(i,x)`  | Insert at position | `a=[1,3]; a.insert(1,2)`  | `[1,2,3]`    |
| 4  | remove() | `a.remove(x)`    | Remove by value    | `a=[1,2]; a.remove(2)`    | `[1]`        |
| 5  | pop()    | `a.pop()`        | Remove last item   | `a=[1,2]; a.pop()`        | `[1]`        |
| 6  | clear()  | `a.clear()`      | Remove all items   | `a=[1,2]; a.clear()`      | `[]`         |
| 7  | index()  | `a.index(x)`     | Get position       | `a=[1,2]; a.index(2)`     | `1`          |
| 8  | count()  | `a.count(x)`     | Count occurrences  | `a=[1,2,2]; a.count(2)`   | `2`          |
| 9  | reverse()| `a.reverse()`    | Reverse list       | `a=[1,2]; a.reverse()`    | `[2,1]`      |
| 10 | sort()   | `a.sort()`       | Sort ascending     | `a=[3,1]; a.sort()`       | `[1,3]`      |
| 11 | copy()   | `a.copy()`       | Duplicate list     | `a=[1,2]; b=a.copy()`     | `[1,2]`      |