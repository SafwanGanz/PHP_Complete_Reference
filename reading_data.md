# 🌐 Reading Data in Web Pages with PHP

![PHP Web Data](https://img.shields.io/badge/PHP-Web%20Data-blue?style=for-the-badge&logo=php)  
**Connect the web to PHP** - Capture and process user input from HTML forms effortlessly!

---

## 🌟 Why Read Data from Web Pages?

PHP shines in web development by processing data from HTML forms. Whether it’s text, selections, or files, PHP’s superglobals (`$_GET`, `$_POST`, etc.) make it easy to handle user input.

---

## 🛠️ Setting Up Web Pages to Communicate with PHP

### Basic Form Setup
Create an HTML form with a `method` (GET or POST) and an `action` pointing to a PHP file.

**`index.html`:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>PHP Form</title>
</head>
<body>
    <form method="post" action="process.php">
        <label>Name: <input type="text" name="username"></label>
        <button type="submit">Submit</button>
    </form>
</body>
</html>
```

**`process.php`:**
```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST["username"];
    echo "Hello, $name!";
}
?>
```

---

## 1. Handling Text Fields
Capture single-line text input.

```html
<input type="text" name="email">
```

```php
$email = $_POST["email"];
echo "Email: $email";
```

---

## 2. Handling Text Areas
Capture multi-line text.

```html
<textarea name="comments"></textarea>
```

```php
$comments = $_POST["comments"];
echo "Comments: $comments";
```

---

## 3. Handling Check Boxes
Capture multiple selections (returns value if checked, absent if not).

```html
<input type="checkbox" name="hobbies[]" value="reading"> Reading
<input type="checkbox" name="hobbies[]" value="gaming"> Gaming
```

```php
$hobbies = $_POST["hobbies"] ?? [];
foreach ($hobbies as $hobby) {
    echo "Hobby: $hobby<br>";
}
```

---

## 4. Handling Radio Buttons
Capture a single selection.

```html
<input type="radio" name="gender" value="male"> Male
<input type="radio" name="gender" value="female"> Female
```

```php
$gender = $_POST["gender"] ?? "Not specified";
echo "Gender: $gender";
```

---

## 5. Handling List Boxes
Capture selections from `<select>` (single or multiple).

```html
<select name="color">
    <option value="red">Red</option>
    <option value="blue">Blue</option>
</select>
```

```php
$color = $_POST["color"];
echo "Favorite color: $color";
```

For multiple:
```html
<select name="colors[]" multiple>
    <option value="red">Red</option>
    <option value="blue">Blue</option>
</select>
```

```php
$colors = $_POST["colors"] ?? [];
echo "Colors: " . implode(", ", $colors);
```

---

## 6. Handling Password Controls
Capture hidden text (e.g., passwords).

```html
<input type="password" name="pass">
```

```php
$password = $_POST["pass"];
echo "Password received (hashed): " . password_hash($password, PASSWORD_DEFAULT);
```

---

## 7. Handling Hidden Controls
Pass data invisibly.

```html
<input type="hidden" name="user_id" value="123">
```

```php
$userId = $_POST["user_id"];
echo "User ID: $userId";
```

---

## 8. Handling Image Maps
Capture coordinates from clickable images.

```html
<input type="image" name="coords" src="map.png" alt="Map">
```

```php
$x = $_POST["coords_x"] ?? 0;
$y = $_POST["coords_y"] ?? 0;
echo "Clicked at: ($x, $y)";
```

---

## 9. Handling File Uploads
Upload files with `enctype="multipart/form-data"`.

```html
<form method="post" enctype="multipart/form-data">
    <input type="file" name="upload">
    <button type="submit">Upload</button>
</form>
```

```php
if (isset($_FILES["upload"])) {
    $file = $_FILES["upload"];
    $destination = "uploads/" . $file["name"];
    move_uploaded_file($file["tmp_name"], $destination);
    echo "File uploaded: " . $file["name"];
}
```

---

## 10. Handling Buttons
Capture button clicks or values.

```html
<button type="submit" name="action" value="save">Save</button>
```

```php
$action = $_POST["action"] ?? "none";
echo "Action: $action"; // Outputs: Action: save
```

---

## 11. Making Button Data Persist
Use sessions to retain data across requests.

```php
session_start();
if (isset($_POST["action"])) {
    $_SESSION["last_action"] = $_POST["action"];
}
echo "Last action: " . ($_SESSION["last_action"] ?? "none");
```

---

## 12. Using Submit Buttons as HTML Buttons
Distinguish multiple submit buttons.

```html
<form method="post">
    <button type="submit" name="submit" value="yes">Yes</button>
    <button type="submit" name="submit" value="no">No</button>
</form>
```

```php
$choice = $_POST["submit"] ?? "undecided";
echo "You chose: $choice";
```

---

## 🔥 Quick Reference

| Control Type      | HTML Element            | PHP Access             |
|-------------------|-------------------------|------------------------|
| Text Field        | `<input type="text">`  | `$_POST["name"]`      |
| Check Box         | `<input type="checkbox">` | `$_POST["name"]` (array) |
| File Upload       | `<input type="file">`  | `$_FILES["name"]`     |
| Hidden            | `<input type="hidden">`| `$_POST["name"]`      |

---

## 🎯 Best Practices
- **Sanitize**: Use `htmlspecialchars()` to prevent XSS.
- **Validate**: Check input with `filter_var()` (e.g., emails).
- **Defaults**: Use `??` for unset values.
- **Security**: Hash passwords, restrict file uploads.

```php
$input = $_POST["username"] ?? "";
$safeInput = htmlspecialchars($input, ENT_QUOTES, "UTF-8");
echo "Safe input: $safeInput";
```

---
[➡️ Next: Browser Handling](browser_handling.md)
