# 🌍 PHP Browser-Handling Power

![PHP Browser Handling](https://img.shields.io/badge/PHP-Browser%20Handling-blue?style=for-the-badge&logo=php)  
**Master the browser** - Use PHP to interact with clients, handle data, and control the web experience!

---

## 🌟 Why Browser Handling?

PHP’s server-side power lets you tap into browser details, manage requests, and tailor responses. From server variables to headers, PHP gives you control over the client-server dance.

---

## 🛠️ Browser-Handling Techniques

### 1. Using PHP's Server Variables
Access server info via `$_SERVER`.

```php
echo "IP Address: " . $_SERVER["REMOTE_ADDR"] . "<br>";
echo "Request Method: " . $_SERVER["REQUEST_METHOD"] . "<br>";
echo "User Agent: " . $_SERVER["HTTP_USER_AGENT"];
```

---

### 2. Using HTTP Headers
Set headers with `header()`.

```php
header("Content-Type: text/plain");
echo "This is plain text!";
```

---

### 3. Getting the User's Browser Type
Parse `$_SERVER["HTTP_USER_AGENT"]`.

```php
$browser = $_SERVER["HTTP_USER_AGENT"];
if (strpos($browser, "Chrome") !== false) {
    echo "You’re using Chrome!";
} elseif (strpos($browser, "Firefox") !== false) {
    echo "You’re using Firefox!";
} else {
    echo "Unknown browser.";
}
```

---

### 4. Redirecting Browsers with HTTP Headers
Send users elsewhere with `header()`.

```php
header("Location: https://example.com");
exit; // Stop further execution
```

---

### 5. Dumping a Form’s Data All at Once
Use `print_r()` or `var_dump()`.

```html
<form method="post">
    <input type="text" name="username">
    <button type="submit">Submit</button>
</form>
```

```php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    echo "<pre>";
    print_r($_POST);
    echo "</pre>";
}
// Outputs: Array ( [username] => value )
```

---

### 6. Handling Form Data with Custom Arrays
Organize data with array notation.

```html
<input type="text" name="user[firstname]">
<input type="text" name="user[lastname]">
```

```php
$user = $_POST["user"] ?? [];
echo "First: " . $user["firstname"] . ", Last: " . $user["lastname"];
```

---

### 7. Putting It All in One Page
Combine form and processing.

```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST["name"] ?? "Guest";
    echo "Hello, $name!";
}
?>
<form method="post">
    <input type="text" name="name">
    <button type="submit">Go</button>
</form>
```

---

### 8. Performing Data Validation
Check input integrity.

```php
$email = $_POST["email"] ?? "";
if (filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Valid email!";
} else {
    echo "Invalid email.";
}
```

---

### 9. Checking if the User Entered Required Data
Ensure fields aren’t empty.

```php
$required = ["name", "age"];
$errors = [];
foreach ($required as $field) {
    if (empty($_POST[$field])) {
        $errors[] = "$field is required.";
    }
}
if (empty($errors)) {
    echo "All good!";
} else {
    echo implode("<br>", $errors);
}
```

---

### 10. Requiring Numbers
Validate numeric input.

```php
$age = $_POST["age"] ?? "";
if (is_numeric($age) && $age > 0) {
    echo "Age: $age";
} else {
    echo "Please enter a valid age.";
}
```

---

### 11. Requiring Text
Ensure text-only input.

```php
$name = $_POST["name"] ?? "";
if (ctype_alpha(str_replace(" ", "", $name))) {
    echo "Valid name: $name";
} else {
    echo "Name must contain only letters.";
}
```

---

### 12. Persisting User Data
Use sessions for persistence.

```php
session_start();
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $_SESSION["username"] = $_POST["username"] ?? "";
}
echo "Saved: " . ($_SESSION["username"] ?? "None");
```

---

### 13. Client-Side Data Validation
Add HTML5 validation (PHP as backup).

```html
<input type="email" name="email" required>
<input type="number" name="age" min="1" required>
```

```php
$email = $_POST["email"] ?? "";
if (filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Email passed server check!";
}
```

---

### 14. Handling HTML Tags in User Input
Sanitize or allow specific tags.

```php
$input = $_POST["comment"] ?? "";
$safeInput = htmlspecialchars($input, ENT_QUOTES, "UTF-8");
echo "Safe: $safeInput"; // <b> becomes &lt;b&gt;

$allowedInput = strip_tags($input, "<b><i>"); // Allow <b>, <i>
echo "Allowed: $allowedInput";
```

---

## 🔥 Quick Reference

| Technique             | Tool                   | Example Use Case         |
|-----------------------|------------------------|--------------------------|
| Server Variables      | `$_SERVER`            | Log user details        |
| HTTP Headers          | `header()`            | Redirects, content type |
| Form Dumping          | `print_r()`           | Debugging               |
| Validation            | `filter_var()`        | Secure input            |
| Persistence           | `session_start()`     | Retain user state       |

---

## 🎯 Best Practices
- **Security**: Always sanitize input (`htmlspecialchars()`, `filter_var()`).
- **Headers**: Call `header()` before any output.
- **Validation**: Combine client-side (HTML5) and server-side checks.
- **Errors**: Provide clear feedback to users.

```php
$input = $_POST["data"] ?? "";
$safe = filter_var($input, FILTER_SANITIZE_STRING);
if ($safe) {
    echo "Processed: $safe";
} else {
    echo "Invalid input!";
}
```

---
[➡️ Next: Object-Oriented Programming](object_oriented.md)
