# 🏗️ Object-Oriented Programming in PHP

![PHP OOP](https://img.shields.io/badge/PHP-OOP-blue?style=for-the-badge&logo=php)  
**Build structured code** - OOP in PHP brings organization, reusability, and power to your projects!

---

## 🌟 Why OOP?

Object-Oriented Programming (OOP) lets you model real-world concepts with **classes** and **objects**, using principles like encapsulation, inheritance, and polymorphism. PHP’s OOP features make code modular and maintainable.

---

## 🛠️ OOP Fundamentals

### 1. Creating Classes
Define a blueprint with the `class` keyword.

```php
class Car {
    public $brand = "Toyota";
    public function drive() {
        echo "Vroom!";
    }
}
```

---

### 2. Creating Objects
Instantiate a class with `new`.

```php
$myCar = new Car();
echo $myCar->brand; // Outputs: Toyota
$myCar->drive();    // Outputs: Vroom!
```

---

### 3. Setting Access to Properties and Methods
Control visibility with access modifiers.

| Modifier   | Access Scope          |
|------------|-----------------------|
| `public`   | Anywhere             |
| `private`  | Class only           |
| `protected`| Class and subclasses |

---

### 4. Public Access
Accessible everywhere.

```php
class Dog {
    public $name = "Buddy";
}
$dog = new Dog();
echo $dog->name; // Outputs: Buddy
```

---

### 5. Private Access
Restricted to the class.

```php
class Cat {
    private $age = 5;
    public function getAge() {
        return $this->age;
    }
}
$cat = new Cat();
echo $cat->getAge(); // Outputs: 5
// echo $cat->age; // Error: Cannot access private property
```

---

### 6. Using Constructors to Initialize Objects
Run setup code with `__construct()`.

```php
class Person {
    public $name;
    public function __construct($name) {
        $this->name = $name;
    }
}
$person = new Person("Alex");
echo $person->name; // Outputs: Alex
```

---

### 7. Using Destructors to Clean Up after Objects
Run cleanup with `__destruct()`.

```php
class FileHandler {
    public function __destruct() {
        echo "Cleaning up...";
    }
}
$file = new FileHandler();
unset($file); // Outputs: Cleaning up...
```

---

### 8. Basing One Class on Another with Inheritance
Extend a class with `extends`.

```php
class Animal {
    public function eat() {
        echo "Yum!";
    }
}
class Bird extends Animal {
    public function fly() {
        echo "Soaring!";
    }
}
$bird = new Bird();
$bird->eat(); // Outputs: Yum!
$bird->fly(); // Outputs: Soaring!
```

---

### 9. Protected Access
Accessible in class and subclasses.

```php
class Vehicle {
    protected $speed = 60;
}
class Bike extends Vehicle {
    public function getSpeed() {
        return $this->speed;
    }
}
$bike = new Bike();
echo $bike->getSpeed(); // Outputs: 60
```

---

### 10. Constructors and Inheritance
Call parent constructors with `parent::__construct()`.

```php
class ParentClass {
    public $value;
    public function __construct($value) {
        $this->value = $value;
    }
}
class ChildClass extends ParentClass {
    public function __construct($value) {
        parent::__construct($value);
    }
}
$child = new ChildClass(42);
echo $child->value; // Outputs: 42
```

---

### 11. Calling Base Class Methods
Use `parent::` to access overridden methods.

```php
class Base {
    public function say() {
        echo "Base!";
    }
}
class Derived extends Base {
    public function say() {
        parent::say();
        echo " Derived!";
    }
}
$obj = new Derived();
$obj->say(); // Outputs: Base! Derived!
```

---

### 12. Overriding Methods
Redefine a parent method.

```php
class Shape {
    public function area() {
        return 0;
    }
}
class Circle extends Shape {
    public $radius;
    public function area() {
        return pi() * $this->radius * $this->radius;
    }
}
$circle = new Circle();
$circle->radius = 5;
echo $circle->area(); // Outputs: ~78.54
```

---

### 13. Overloading Methods
PHP doesn’t support true overloading, but use optional parameters or magic methods like `__call()`.

```php
class Calculator {
    public function add($a, $b = 0, $c = 0) {
        return $a + $b + $c;
    }
}
$calc = new Calculator();
echo $calc->add(1);     // Outputs: 1
echo $calc->add(1, 2);  // Outputs: 3
echo $calc->add(1, 2, 3); // Outputs: 6
```

With `__call()`:
```php
class Magic {
    public function __call($name, $args) {
        echo "Called $name with " . count($args) . " args!";
    }
}
$magic = new Magic();
$magic->test(1, 2); // Outputs: Called test with 2 args!
```

---

### 14. Autoloading Classes
Load classes automatically with `spl_autoload_register()`.

```php
spl_autoload_register(function ($className) {
    include "$className.php";
});
$car = new Car(); // Loads Car.php automatically
```

**`Car.php`:**
```php
class Car {
    public function honk() {
        echo "Beep!";
    }
}
```

---

## 🔥 Quick Reference

| Concept           | Key Feature                  | Example Use Case          |
|-------------------|------------------------------|---------------------------|
| Classes/Objects   | Encapsulation               | Model entities            |
| Inheritance       | Code reuse                  | Extend functionality      |
| Access Modifiers  | Control visibility          | Protect data              |
| Autoloading       | Dynamic loading             | Simplify includes         |

---

## 🎯 Best Practices
- **Encapsulation**: Use `private`/`protected` for sensitive data.
- **Single Responsibility**: One class, one purpose.
- **Naming**: Use clear, PascalCase class names (e.g., `UserProfile`).
- **Autoloading**: Prefer modern autoloaders (e.g., Composer).

```php
class User {
    private $id;
    public function __construct($id) {
        $this->id = $id;
    }
    public function getId() {
        return $this->id;
    }
}
$user = new User(123);
echo $user->getId(); // Outputs: 123
```

---
[➡️ Next: Advanced Object-Oriented Programming](advanced_object_oriented.md)
