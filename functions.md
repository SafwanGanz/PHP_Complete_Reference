# 🧰 Functions in PHP

![PHP Functions](https://img.shields.io/badge/PHP-Functions-blue?style=for-the-badge&logo=php)  
**Unlock reusable code** - Functions organize logic, manage data, and streamline your PHP projects!

---

## 🌟 What Are Functions?

Functions are reusable blocks of code that perform specific tasks. They can take inputs (parameters), process them, and return outputs. PHP offers built-in functions and lets you create custom ones!

---

## 🛠️ Function Basics

### Defining a Function
Use the `function` keyword, a name, and optional parameters.

```php
function greet($name) {
    echo "Hello, $name!";
}
greet("User"); // Outputs: Hello, User!
```

---

## 1. Returning Data from Functions
Return a value using the `return` statement.

```php
function add($a, $b) {
    return $a + $b;
}
$result = add(5, 3);
echo $result; // Outputs: 8
```

---

## 2. Returning Arrays
Return multiple values as an array.

```php
function getStats() {
    return ["score" => 95, "level" => 3];
}
$stats = getStats();
echo $stats["score"]; // Outputs: 95
```

---

## 3. Returning Lists
Use `list()` to unpack array returns (older style).

```php
function getCoordinates() {
    return [10, 20];
}
list($x, $y) = getCoordinates();
echo "X: $x, Y: $y"; // Outputs: X: 10, Y: 20
```

> **Note**: Modern PHP favors array destructuring: `[$x, $y] = getCoordinates();`

---

## 4. Returning References
Return a variable by reference with `&`.

```php
function &getValue() {
    static $value = 42;
    return $value;
}
$ref = &getValue();
$ref = 100;
echo getValue(); // Outputs: 100
```

---

## 5. Introducing Variable Scope in PHP
Variables have **scope**—local by default.

```php
$globalVar = "Outside";
function testScope() {
    $localVar = "Inside";
    echo $localVar; // Outputs: Inside
}
testScope();
echo $globalVar; // Outputs: Outside
// echo $localVar; // Error: Undefined
```

---

## 6. Accessing Global Data
Use `global` or the `$GLOBALS` array.

```php
$count = 5;
function increment() {
    global $count;
    $count++;
}
increment();
echo $count; // Outputs: 6
```

With `$GLOBALS`:
```php
$count = 5;
function incrementGlobals() {
    $GLOBALS["count"]++;
}
incrementGlobals();
echo $count; // Outputs: 6
```

---

## 7. Working with Static Variables
Retain values between calls with `static`.

```php
function counter() {
    static $num = 0;
    $num++;
    return $num;
}
echo counter(); // Outputs: 1
echo counter(); // Outputs: 2
```

---

## 8. PHP Conditional Functions
Functions with conditional logic.

```php
function checkAge($age) {
    if ($age >= 18) {
        return "Adult";
    }
    return "Minor";
}
echo checkAge(20); // Outputs: Adult
```

---

## 9. PHP Variable Functions
Call functions dynamically by name.

```php
function sayHello() {
    echo "Hello!";
}
$funcName = "sayHello";
$funcName(); // Outputs: Hello!
```

---

## 10. Nesting Functions
Define functions inside others (rarely used).

```php
function outer() {
    function inner() {
        echo "Nested!";
    }
    inner();
}
outer(); // Outputs: Nested!
```

> **Caution**: Inner functions become global after `outer()` runs once.

---

## 11. Creating Include Files
Move functions to separate files.

**`helpers.php`:**
```php
function multiply($a, $b) {
    return $a * $b;
}
```

**Main file:**
```php
include "helpers.php";
echo multiply(4, 5); // Outputs: 20
```

---

## 12. Returning Errors from Functions
Return error indicators (e.g., `false`, exceptions).

```php
function divide($a, $b) {
    if ($b == 0) {
        return false; // Error indicator
    }
    return $a / $b;
}
$result = divide(10, 0);
if ($result === false) {
    echo "Error: Division by zero!";
} else {
    echo $result;
}
// Outputs: Error: Division by zero!
```

With exceptions:
```php
function safeDivide($a, $b) {
    if ($b == 0) {
        throw new Exception("Division by zero!");
    }
    return $a / $b;
}
try {
    echo safeDivide(10, 0);
} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
}
// Outputs: Error: Division by zero!
```

---

## 🔥 Quick Reference

| Topic                 | Key Feature                  | Example Use Case          |
|-----------------------|------------------------------|---------------------------|
| Returning Data        | Single value                | Calculations             |
| Arrays                | Multiple values             | Data bundles             |
| References            | Modify original data        | Memory optimization      |
| Static Variables      | Persist across calls        | Counters                 |
| Variable Functions    | Dynamic calls               | Callbacks                |
| Include Files         | Reuse across files          | Modular code             |

---

## 🎯 Best Practices
- **Naming**: Use clear, verb-based names (e.g., `calculateTotal`).
- **Scope**: Minimize `global` use—pass parameters instead.
- **Errors**: Prefer exceptions over `false` for modern code.
- **DRY**: Don’t Repeat Yourself—use functions to reuse logic.

```php
function formatName($first, $last) {
    return ucfirst($first) . " " . ucfirst($last);
}
echo formatName("john", "doe"); // Outputs: John Doe
```
[➡️ Next: Reading data](reading_data.md)
---
