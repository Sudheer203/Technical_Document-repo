# SQL Triggers – Technical Documentation

## Understanding Database Trigger
---

## Introduction

A Trigger is a special type of stored procedure that automatically
executes in response to specific events on a table or view.

Triggers are commonly used for:

- Auditing changes
- Enforcing business rules
- Maintaining logs
- Validating data
- Synchronizing tables

---

# 1. Types of Triggers

## 🔹 Based on Timing

### BEFORE Trigger
Executes before INSERT, UPDATE, or DELETE operation.

### AFTER Trigger
Executes after the operation is completed.

### INSTEAD OF Trigger
Replaces the execution of INSERT, UPDATE, or DELETE.
Mostly used with views.

---

## 🔹 Based on Events

- INSERT Trigger
- UPDATE Trigger
- DELETE Trigger

---

# 2. Basic Trigger Syntax

## PostgreSQL Example

```
CREATE OR REPLACE FUNCTION log_update()
RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO audit_log(table_name, changed_at)
    VALUES ('employees', NOW());
    RETURN NEW;
END;
''

$$ LANGUAGE plpgsql;
```

```
CREATE TRIGGER employee_update_trigger
AFTER UPDATE ON employees
FOR EACH ROW
EXECUTE FUNCTION log_update();
```

---

# 3. Row-Level vs Statement-Level Triggers

## Row-Level Trigger
Executes once for each affected row.

``
    FOR EACH ROW
``

## Statement-Level Trigger
Executes once per SQL statement.

    FOR EACH STATEMENT

---

# 4. OLD and NEW Keywords

Inside triggers:

- NEW → New row data (INSERT/UPDATE)
- OLD → Previous row data (UPDATE/DELETE)

Example:

IF NEW.salary > 100000 THEN
    RAISE NOTICE 'High salary detected';
END IF;

---

# 5. Common Use Cases

- Audit logging  
- Data validation  
- Preventing invalid operations  
- Cascading updates  
- Automatic timestamps  

---

# 6. Advantages

- Automatic execution  
- Enforces data integrity  
- Centralized logic in database  

---

# 7. Disadvantages

- Hard to debug  
- Can reduce performance  
- Hidden logic complexity  

---

# 8. When NOT to Use Triggers

- For complex business logic (use application layer)
- When performance is critical
- When logic needs transparency

---

# 9. Conclusion

Triggers are powerful automation tools inside databases.
When used carefully, they help maintain integrity and consistency
without manual intervention.

However, misuse can lead to performance issues and maintenance complexity.

---
