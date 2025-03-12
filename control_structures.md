# 🎛️ Control Structures in PHP

![PHP Control Structures](https://img.shields.io/badge/PHP-Control%20Structures-blue?style=for-the-badge&logo=php)  
**Take charge of your code** - Control Structures direct the flow of execution in PHP!

---

## 🌟 What Are Control Structures?

Control structures let you dictate how and when code runs. They include **conditionals** (e.g., `if`) for decisions and **loops** (e.g., `for`) for repetition—essential for dynamic programs!

---

## 🛠️ Types of Control Structures

Let’s dive into PHP’s key control structures with examples!

### 1. Conditional Statements
Make decisions based on conditions.

#### `if`, `else if`, `else`
Execute code if a condition is true.

```php
$age = 20;
if ($age >= 18) {
    echo "You’re an adult!";
} else if ($age >= 13) {
    echo "You’re a teen!";
} else {
    echo "You’re a kid!";
}
// Outputs: You’re an adult!
```

#### `switch`
Handle multiple cases efficiently.

```php
$day = 3;
switch ($day) {
    case 1:
        echo "Monday";
        break;
    case 2:
        echo "Tuesday";
        break;
    case 3:
        echo "Wednesday";
        break;
    default:
        echo "Unknown day";
}
// Outputs: Wednesday
```

| Feature         | `if`                  | `switch`             |
|-----------------|-----------------------|----------------------|
| **Use Case**    | Flexible conditions  | Multiple fixed values |
| **Syntax**      | More verbose         | Cleaner for cases    |
| **Break Needed**| No                   | Yes (or fall-through)|

---

### 2. Looping Structures
Repeat code as needed.

#### `for`
Run a block a specific number of times.

```php
for ($i = 1; $i <= 5; $i++) {
    echo "Count: $i<br>";
}
// Outputs:
// Count: 1
// Count: 2
// Count: 3
// Count: 4
// Count: 5
```

#### `while`
Loop while a condition is true.

```php
$count = 0;
while ($count < 3) {
    echo "Tick: $count<br>";
    $count++;
}
// Outputs:
// Tick: 0
// Tick: 1
// Tick: 2
```

#### `do-while`
Loop at least once, then check the condition.

```php
$num = 5;
do {
    echo "Number: $num<br>";
    $num--;
} while ($num > 0);
// Outputs:
// Number: 5
// Number: 4
// Number: 3
// Number: 2
// Number: 1
```

#### `foreach`
Iterate over arrays or objects.

```php
$colors = ["red", "blue", "green"];
foreach ($colors as $color) {
    echo "Color: $color<br>";
}
// Outputs:
// Color: red
// Color: blue
// Color: green
```

| Loop Type   | Best For                       | Condition Checked |
|-------------|--------------------------------|-------------------|
| `for`       | Known iterations              | Before each       |
| `while`     | Unknown iterations            | Before each       |
| `do-while`  | At least one run              | After each        |
| `foreach`   | Arrays/iterables              | N/A               |

---

### 3. Control Flow Modifiers
Alter loop or conditional behavior.

#### `break`
Exit a loop or switch early.

```php
for ($i = 0; $i < 10; $i++) {
    if ($i == 4) {
        break;
    }
    echo "$i ";
}
// Outputs: 0 1 2 3
```

#### `continue`
Skip to the next loop iteration.

```php
for ($i = 0; $i < 5; $i++) {
    if ($i == 2) {
        continue;
    }
    echo "$i ";
}
// Outputs: 0 1 3 4
```

---

## 🔥 Combining Operators with Control Structures
Use operators (e.g., `&&`, `>`) to craft powerful logic.

```php
$score = 85;
if ($score >= 90) {
    echo "Grade: A";
} elseif ($score >= 80 && $score < 90) {
    echo "Grade: B";
} else {
    echo "Grade: C";
}
// Outputs: Grade: B
```

---

## 🎯 Best Practices
- **Readability**: Use braces `{}` even for single-line blocks.
- **Nesting**: Avoid deep nesting—keep it simple.
- **Comments**: Explain complex logic with `//` or `/* */`.

```php
$items = ["apple", "banana", "orange"];
foreach ($items as $index => $item) {
    // Skip banana
    if ($item === "banana") {
        continue;
    }
    echo "$index: $item<br>";
}
// Outputs:
// 0: apple
// 2: orange
```

---

## 🌐 Try It Out!
Control structures are your key to dynamic PHP code. Experiment with conditions and loops to see the magic unfold!

[➡️ Next: Functions](#functions)

---
