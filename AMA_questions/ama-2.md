# AMA Questions and Answers
## 1. What is SQL?

SQL stands for **Structured Query Language**.\
It is used to **store, manage, and retrieve data from a database**.

Example:

``` sql
SELECT * FROM students;
```

------------------------------------------------------------------------

## 2. DROP in SQL

`DROP` is used to **delete a table or database completely**.\
Both the **structure and data are removed permanently**.

Example:

``` sql
DROP TABLE students;
```

------------------------------------------------------------------------

## 3. TRUNCATE in SQL

`TRUNCATE` is used to **delete all rows from a table**, but the **table
structure remains**.

Example:

``` sql
TRUNCATE TABLE students;
```

------------------------------------------------------------------------

## 4. Difference between Class and ID

  Class                        |ID
  ---------------------------- |-------------------------
  Used for multiple elements   |Used for one element
  Written with `.` in CSS      |Written with `#` in CSS

Example:

``` html
<p class="text"></p>
<p id="title"></p>
```

------------------------------------------------------------------------

## 5. Inline and Block Elements

**Inline Elements** - Do not start on a new line - Take only required
width

Examples: `span`, `a`, `strong`

**Block Elements** - Start on a new line - Take full width

Examples: `div`, `p`, `section`

------------------------------------------------------------------------

## 6. Add new column in existing table

Example:

``` sql
ALTER TABLE students
ADD age INT;
```

------------------------------------------------------------------------

## 7. Change column name

Example:

``` sql
ALTER TABLE students
RENAME COLUMN name TO student_name;
```

------------------------------------------------------------------------

## 8. Difference between Link Tag and Anchor Tag

  Link Tag                   | Anchor Tag
  -------------------------- |-------------------------
  Used in `<head>`           | Used in `<body>`
  Links external resources   | Creates clickable links

Example:

``` html
<link rel="stylesheet" href="style.css">
<a href="https://example.com">Visit Website</a>
```

------------------------------------------------------------------------

## 9. Link Tag in HTML

The `<link>` tag connects **external resources like CSS** to the HTML
document.

Example:

``` html
<link rel="stylesheet" href="style.css">
```

------------------------------------------------------------------------

## 10. Opacity Property

`opacity` controls the **transparency of an element**.

Values: - `0` → fully transparent - `1` → fully visible

Example:

``` css
img {
  opacity: 0.5;
}
```

------------------------------------------------------------------------

## 11. TRUNCATE vs DELETE

  TRUNCATE           |DELETE
  ------------------ |-----------------------
  Removes all rows   |Removes selected rows
  Faster             |Slower
  Cannot use WHERE   |Can use WHERE

Example:

``` sql
DELETE FROM students WHERE id = 1;
```

------------------------------------------------------------------------

## 12. Create Table in SQL

Example:

``` sql
CREATE TABLE students (
  id INT,
  name VARCHAR(50),
  age INT
);
```

------------------------------------------------------------------------

## 13. Margin

`margin` is the **space outside an element**.

Example:

``` css
div {
  margin: 20px;
}
```

------------------------------------------------------------------------

## 14. Padding and Margin

  Padding                    |Margin
  -------------------------- |---------------------------
  Space inside the element   |Space outside the element
                             
Example:

``` css
div {
  padding: 10px;
  margin: 20px;
}
```