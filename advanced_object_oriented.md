# 🚀 Advanced Object-Oriented Programming in PHP

![PHP Advanced OOP](https://img.shields.io/badge/PHP-Advanced%20OOP-blue?style=for-the-badge&logo=php)  
**Elevate your OOP skills** - Dive into advanced techniques for powerful, flexible PHP code!

---

## 🌟 Why Advanced OOP?

Advanced OOP in PHP builds on the basics, offering tools like static methods, abstract classes, and reflection to create robust, reusable, and maintainable applications.

---

## 🛠️ Advanced OOP Techniques

### 1. Creating Static Methods
Define methods callable without instantiation using `static`.

```php
class Math {
    public static function add($a, $b) {
        return $a + $b;
    }
}
echo Math::add(5, 3); // Outputs: 8
```

---

### 2. Creating a Static Method (Detailed Example)
A single static method in context.

```php
class Logger {
    public static function log($message) {
        echo "Log: $message";
    }
}
Logger::log("Error occurred"); // Outputs: Log: Error occurred
```

---

### 3. Passing Data to a Static Method
Pass arguments as usual.

```php
class Converter {
    public static function toCelsius($fahrenheit) {
        return ($fahrenheit - 32) * 5 / 9;
    }
}
echo Converter::toCelsius(98.6); // Outputs: 37
```

---

### 4. Using Properties in Static Methods
Use `static` properties, accessed with `self::`.

```php
class Counter {
    public static $count = 0;
    public static function increment() {
        self::$count++;
        return self::$count;
    }
}
echo Counter::increment(); // Outputs: 1
echo Counter::increment(); // Outputs: 2
```

---

### 5. Static Members and Inheritance
Static members are shared, but can be overridden.

```php
class ParentClass {
    public static $value = "Parent";
    public static function getValue() {
        return self::$value;
    }
}
class ChildClass extends ParentClass {
    public static $value = "Child";
}
echo ParentClass::getValue(); // Outputs: Parent
echo ChildClass::getValue();  // Outputs: Child
```

---

### 6. Creating Abstract Classes
Define a blueprint with `abstract`—cannot be instantiated.

```php
abstract class Shape {
    abstract public function area();
}
class Rectangle extends Shape {
    public $width, $height;
    public function area() {
        return $this->width * $this->height;
    }
}
$rect = new Rectangle();
$rect->width = 5;
$rect->height = 3;
echo $rect->area(); // Outputs: 15
```

---

### 7. Creating Interfaces
Specify contracts with `interface`.

```php
interface Printable {
    public function print();
}
class Document implements Printable {
    public function print() {
        echo "Printing document...";
    }
}
$doc = new Document();
$doc->print(); // Outputs: Printing document...
```

---

### 8. Supporting Object Iteration
Implement `Iterator` for custom looping.

```php
class MyList implements Iterator {
    private $items = [];
    private $position = 0;
    public function __construct($items) {
        $this->items = $items;
    }
    public function current() { return $this->items[$this->position]; }
    public function key() { return $this->position; }
    public function next() { $this->position++; }
    public function rewind() { $this->position = 0; }
    public function valid() { return isset($this->items[$this->position]); }
}
$list = new MyList(["a", "b", "c"]);
foreach ($list as $item) {
    echo "$item ";
} // Outputs: a b c
```

---

### 9. Comparing Objects
Use `==` (properties) or `===` (identity).

```php
class User {
    public $id;
    public function __construct($id) {
        $this->id = $id;
    }
}
$u1 = new User(1);
$u2 = new User(1);
echo $u1 == $u2 ? "Equal" : "Not equal";  // Outputs: Equal
echo $u1 === $u2 ? "Same" : "Not same";   // Outputs: Not same
```

---

### 10. Creating Class Constants
Define immutable values with `const`.

```php
class Config {
    const MAX_USERS = 100;
}
echo Config::MAX_USERS; // Outputs: 100
```

---

### 11. Using the final Keyword
Prevent overriding or extension.

```php
final class Immutable {
    final public function lock() {
        echo "Locked!";
    }
}
class Test extends Immutable {} // Error: Cannot extend final class
```

---

### 12. Cloning Objects
Duplicate with `clone`.

```php
class Item {
    public $name = "Book";
    public function __clone() {
        $this->name .= " (copy)";
    }
}
$original = new Item();
$copy = clone $original;
echo $copy->name; // Outputs: Book (copy)
```

---

### 13. Reflection
Inspect classes dynamically with `ReflectionClass`.

```php
class Sample {
    public $data = "Test";
    public function run() {}
}
$reflection = new ReflectionClass("Sample");
echo "Methods: " . implode(", ", $reflection->getMethods()) . "<br>";
echo "Properties: " . implode(", ", array_keys($reflection->getProperties()));
// Outputs: Methods: run, Properties: data
```

---

## 🔥 Quick Reference

| Technique          | Key Feature                  | Example Use Case          |
|--------------------|------------------------------|---------------------------|
| Static Methods     | No instantiation            | Utilities                 |
| Abstract Classes   | Enforce structure           | Base templates            |
| Interfaces         | Contract enforcement        | Multiple implementations  |
| Reflection         | Runtime inspection          | Debugging, frameworks     |

---

## 🎯 Best Practices
- **Static**: Use sparingly—prefer instance methods for state.
- **Abstraction**: Balance flexibility and enforcement.
- **Constants**: Use for fixed values (e.g., settings).
- **Cloning**: Handle deep copies with `__clone()`.

```php
abstract class Entity {
    protected $id;
    public function __construct($id) {
        $this->id = $id;
    }
    abstract public function describe();
}
class Product extends Entity {
    public function describe() {
        return "Product ID: $this->id";
    }
}
$prod = new Product(123);
echo $prod->describe(); // Outputs: Product ID: 123
```

---
[➡️ Next: File Handling(file_handling.md)
