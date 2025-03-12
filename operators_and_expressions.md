# ⚙️ Operators and Expressions in PHP

![PHP Operators](https://img.shields.io/badge/PHP-Operators%20&%20Expressions-blue?style=for-the-badge&logo=php)  
**Power up your PHP skills** - Operators and Expressions let you manipulate data and build logic dynamically!

---

## 🌟 What Are Operators and Expressions?

- **Operators**: Symbols that perform operations on variables and values (e.g., `+`, `-`, `*`).
- **Expressions**: Combinations of operators, variables, and values that produce a result (e.g., `$x + 5`).

PHP operators are your toolkit for arithmetic, comparison, logic, and more!

---

## 🛠️ Types of Operators

PHP offers a wide range of operators. Let’s explore the main categories with examples!

### 1. Arithmetic Operators
Perform basic math operations.

| Operator | Description          | Example             | Result  |
|----------|----------------------|---------------------|---------|
| `+`      | Addition            | `$a = 5 + 3;`      | `8`     |
| `-`      | Subtraction         | `$b = 10 - 4;`     | `6`     |
| `*`      | Multiplication      | `$c = 2 * 6;`      | `12`    |
| `/`      | Division            | `$d = 15 / 3;`     | `5`     |
| `%`      | Modulus (remainder) | `$e = 10 % 3;`     | `1`     |
| `**`     | Exponentiation      | `$f = 2 ** 3;`     | `8`     |

```php
$x = 10;
$y = 4;
echo $x + $y; // Outputs: 14
echo $x % $y; // Outputs: 2
```

---

### 2. Assignment Operators
Assign values to variables, often with a twist.

| Operator | Description                | Example             | Equivalent       |
|----------|----------------------------|---------------------|------------------|
| `=`      | Assign                    | `$x = 5;`          | -               |
| `+=`     | Add and assign            | `$x += 3;`         | `$x = $x + 3;` |
| `-=`     | Subtract and assign       | `$x -= 2;`         | `$x = $x - 2;` |
| `*=`     | Multiply and assign       | `$x *= 4;`         | `$x = $x * 4;` |
| `/=`     | Divide and assign         | `$x /= 2;`         | `$x = $x / 2;` |

```php
$total = 10;
$total += 5; // $total is now 15
echo $total; // Outputs: 15
```

---

### 3. Comparison Operators
Compare values and return `true` or `false`.

| Operator | Description            | Example             | Result  |
|----------|------------------------|---------------------|---------|
| `==`     | Equal (loose)         | `5 == "5";`        | `true`  |
| `===`    | Identical (strict)    | `5 === "5";`       | `false` |
| `!=`     | Not equal             | `5 != 3;`          | `true`  |
| `<>`     | Not equal (alt)       | `5 <> 3;`          | `true`  |
| `>`      | Greater than          | `10 > 5;`          | `true`  |
| `<`      | Less than             | `3 < 7;`           | `true`  |
| `>=`     | Greater or equal      | `5 >= 5;`          | `true`  |
| `<=`     | Less or equal         | `4 <= 6;`          | `true`  |

```php
$a = 10;
$b = "10";
var_dump($a == $b);  // Outputs: bool(true)
var_dump($a === $b); // Outputs: bool(false)
```

---

### 4. Logical Operators
Combine conditions for decision-making.

| Operator | Description    | Example                 | Result  |
|----------|----------------|-------------------------|---------|
| `&&`     | AND            | `true && false;`       | `false` |
| `||`     | OR             | `true || false;`       | `true`  |
| `!`      | NOT            | `!true;`               | `false` |

```php
$age = 25;
$hasID = true;
$canEnter = ($age >= 18 && $hasID);
echo $canEnter ? "Welcome!" : "Denied"; // Outputs: Welcome!
```

---

### 5. Increment/Decrement Operators
Adjust numeric values by 1.

| Operator | Description           | Example             | Result  |
|----------|-----------------------|---------------------|---------|
| `++`     | Increment (pre/post) | `$x = 5; $x++;`    | `6`     |
| `--`     | Decrement (pre/post) | `$y = 5; $y--;`    | `4`     |

```php
$count = 10;
$count++; // Now 11
echo $count; // Outputs: 11
```

---

## 🔥 Expressions in Action
An expression is anything that evaluates to a value. Combine operators creatively!

```php
$price = 20;
$discount = 0.1;
$finalPrice = $price - ($price * $discount); // Expression
echo $finalPrice; // Outputs: 18
```

---

## 🎯 Best Practices
- **Clarity**: Use parentheses `()` to group expressions (e.g., `$x + ($y * $z)`).
- **Strict Comparison**: Prefer `===` over `==` to avoid type juggling surprises.
- **Test**: Use `var_dump()` to verify results during debugging.

```php
$x = 5;
$y = "5";
$result = ($x === $y) ? "Identical" : "Different";
echo $result; // Outputs: Different
```

---

## 🌐 Try It Out!
Play with operators and expressions to manipulate data. Next, explore how to control flow with them!

[➡️ Next: Control Structures](control-structures.md)

---
