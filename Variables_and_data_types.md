## Understanding Variables
Variables in PHP are containers for storing data values. They start with a `$` symbol followed by the variable name.

### Basic Syntax
```php
<?php
$name = "John";           // String
$age = 25;               // Integer
$price = 19.99;          // Float
$is_student = true;      // Boolean
?>
```

### Data Types
1. **String**: Text data
2. **Integer**: Whole numbers
3. **Float**: Decimal numbers
4. **Boolean**: True/False values
5. **Array**: Ordered collection
6. **Object**: Instances of classes

### Example: Working with Variables
```php
<?php
$first_name = "Jane";
$last_name = "Doe";
$full_name = $first_name . " " . $last_name; // Concatenation
echo "Welcome, $full_name!";
?>
```
*Output: Welcome, Jane Doe!*

> **Tip:** Use `var_dump($variable)` to inspect a variable's type and value.

---

<div style="display: flex; justify-content: space-between; padding: 20px; background: #f5f5f5; border-radius: 8px;">
  <a href="Introduction.md" style="padding: 10px 20px; background: #007bff; color: white; text-decoration: none; border-radius: 5px;">← Previous</a>
  <a href="Operators_and_expressions.md" style="padding: 10px 20px; background: #007bff; color: white; text-decoration: none; border-radius: 5px;">Next →</a>
</div>