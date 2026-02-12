#  Python Lists – Simple Explanation

##  What is a List?

A **list** is like a box that can store many values in one place.

Example:

```python
numbers = [1, 2, 3, 4, 5]
```

This list stores 5 numbers.

You can store:

* Numbers - `[1, 2, 3]`
* Strings - `["apple", "banana"]`
* Mixed - `[1, "apple", 3.5]` (not recommended but possible)

---

#  Index (Position Number)

Every item in a list has a **position number**.

**Important:** 
Python starts counting from **0**, not 1.

Example:

```python
sampleList = [1, 2, 3, 4, 5, 6, 7, 8]

print(sampleList[0])   # First item
print(sampleList[1])   # Second item
```

Output:

```
1
2
```

`sampleList[1]` means:

* Go to position **1**
* That is the **second value**
* Result = `2`

---

# Common List Methods :

Methods are actions you can perform on a list.

---

## 1. append() - Add item at end

```python
numbers = [1, 2, 3]
numbers.append(4)

print(numbers)
```

Output:

```
[1, 2, 3, 4]
```
Adds value to the **end**.

---

## 2. extend(iterable)

Adds multiple values (from another list) to the end.

This is different from append().
```
numbers = [1, 2]
numbers.extend([3, 4])

print(numbers)
```

Output:

```
[1, 2, 3, 4]
```

## 3. insert(position, value) - Add at specific position

```python
numbers = [1, 2, 4]
numbers.insert(2, 3)

print(numbers)
```

Output:

```
[1, 2, 3, 4]
```

Insert `3` at position `2`.

---

## 4. pop() - Remove last item

```python
numbers = [1, 2, 3]
numbers.pop()

print(numbers)
```

Output:

```
[1, 2]
```

Removes the last item.

---

## 5. remove(value) - Remove by value

```python
numbers = [1, 2, 3, 2]
numbers.remove(2)

print(numbers)
```

Output:

```
[1, 3, 2]
```

Removes the **first 2** it finds.

---

## 6. count(value) - Count how many times value appears

```python
numbers = [1, 2, 2, 3]
print(numbers.count(2))
```

Output:

```
2
```

Number 2 appears **2 times**.

---

## 7. index(value) - Find position

```python
numbers = [10, 20, 30]
print(numbers.index(20))
```

Output:

```
1
```

20 is at position 1.

---

## 8. reverse() - Reverse the list

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

## 9. sort() - Sort in ascending order

```python
numbers = [5, 1, 4, 2]
numbers.sort()

print(numbers)
```

Output:

```
[1, 2, 4, 5]
```

---


# Quick Memory Trick

| Method     | Purpose                    | Example Code              | Result              |
|------------|----------------------------|---------------------------|---------------------|
| append()   | Add one item at end        | `[1,2].append(3)`         | `[1,2,3]`           |
| extend()   | Add multiple items at end  | `[1,2].extend([3,4])`     | `[1,2,3,4]`         |
| insert()   | Insert at position         | `[1,3].insert(1,2)`       | `[1,2,3]`           |
| pop()      | Remove last item           | `[1,2,3].pop()`           | `[1,2]`             |
| remove()   | Remove by value            | `[1,2,2].remove(2)`       | `[1,2]`             |
| count()    | Count occurrences          | `[1,2,2].count(2)`        | `2`                 |
| index()    | Find index                 | `[10,20].index(20)`       | `1`                 |
| reverse()  | Reverse list               | `[1,2,3].reverse()`       | `[3,2,1]`           |
| sort()     | Sort ascending             | `[3,1,2].sort()`          | `[1,2,3]`           |

