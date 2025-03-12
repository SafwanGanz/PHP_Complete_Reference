## Working with Operators
Operators are symbols that perform operations on variables and values.

### Arithmetic Operators
```php
<?php
$a = 10;
$b = 5;

$sum = $a + $b;      // Addition: 15
$diff = $a - $b;     // Subtraction: 5
$prod = $a * $b;     // Multiplication: 50
$quot = $a / $b;     // Division: 2
$mod = $a % $b;      // Modulus: 0
?>
```

### Comparison Operators
```php
<?php
$x = 10;
$y = "10";

var_dump($x == $y);   // Equal: true
var_dump($x === $y);  // Identical: false
var_dump($x != $y);   // Not equal: false
?>
```

> **Pro Tip:** Use `===` for strict type comparison to avoid type juggling issues.

---

<div style="display: flex; justify-content: space-between; padding: 20px; background: #f5f5f5; border-radius: 8px;">
  <a href="Variables_and_data_types.md" style="padding: 10px 20px; background: #007bff; color: white; text-decoration: none; border-radius: 5px;">← Previous</a>
  <a href="Control_structures.md" style="padding: 10px 20px; background: #007bff; color: white; text-decoration: none; border-radius: 5px;">Next →</a>
</div>