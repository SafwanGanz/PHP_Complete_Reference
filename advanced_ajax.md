# 🚀 Advanced Ajax in PHP

![PHP Advanced Ajax](https://img.shields.io/badge/PHP-Advanced%20Ajax-blue?style=for-the-badge&logo=php)  
**Push Ajax further** - Master concurrent requests, cross-domain calls, and advanced integrations with PHP!

---

## 🌟 Why Advanced Ajax?

Advanced Ajax techniques handle multiple requests, fetch diverse content, and connect to external services, all while leveraging PHP for server-side logic.

---

## 🛠️ Advanced Ajax Techniques

### 1. Handling Concurrent Ajax Requests
Manage multiple requests simultaneously.

```javascript
function fetchMultiple() {
    let xhr1 = new XMLHttpRequest();
    let xhr2 = new XMLHttpRequest();

    xhr1.open("GET", "data1.php", true);
    xhr1.onreadystatechange = function () {
        if (xhr1.readyState == 4 && xhr1.status == 200) {
            console.log("Data 1: " + xhr1.responseText);
        }
    };
    xhr1.send();

    xhr2.open("GET", "data2.php", true);
    xhr2.onreadystatechange = function () {
        if (xhr2.readyState == 4 && xhr2.status == 200) {
            console.log("Data 2: " + xhr2.responseText);
        }
    };
    xhr2.send();
}
```

**`data1.php`:**
```php
<?php echo "First response"; ?>
```

**`data2.php`:**
```php
<?php echo "Second response"; ?>
```

---

### 2. Handling Multiple XMLHttpRequest Objects
Track requests with an array.

```javascript
let requests = [];
function fetchData(url, callback) {
    let xhr = new XMLHttpRequest();
    requests.push(xhr);
    xhr.open("GET", url, true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            callback(xhr.responseText);
        }
    };
    xhr.send();
}
fetchData("data1.php", data => console.log(data));
fetchData("data2.php", data => console.log(data));
```

---

### 3. Handling Concurrent Ajax Requests with JavaScript Inner Functions
Use closures for request-specific logic.

```javascript
function fetchWithClosure(id) {
    return function () {
        let xhr = new XMLHttpRequest();
        xhr.open("GET", "data.php?id=" + id, true);
        xhr.onreadystatechange = function () {
            if (xhr.readyState == 4 && xhr.status == 200) {
                console.log("Response for " + id + ": " + xhr.responseText);
            }
        };
        xhr.send();
    };
}
let req1 = fetchWithClosure(1);
let req2 = fetchWithClosure(2);
req1(); req2();
```

**`data.php`:**
```php
<?php
$id = $_GET["id"] ?? 0;
echo "Data for ID $id";
?>
```

---

### 4. Downloading Images Using Ajax
Fetch images as blobs.

```javascript
function loadImage() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "image.php", true);
    xhr.responseType = "blob";
    xhr.onload = function () {
        if (xhr.status == 200) {
            let img = document.createElement("img");
            img.src = URL.createObjectURL(xhr.response);
            document.body.appendChild(img);
        }
    };
    xhr.send();
}
```

**`image.php`:**
```php
<?php
header("Content-Type: image/png");
readfile("sample.png");
?>
```

---

### 5. Downloading JavaScript with Ajax
Fetch and execute JS code.

```javascript
function loadScript() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "script.php", true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            eval(xhr.responseText); // Caution: Security risk
        }
    };
    xhr.send();
}
```

**`script.php`:**
```php
<?php
header("Content-Type: application/javascript");
echo "console.log('Script loaded!');";
?>
```

> **Warning**: Use `eval()` cautiously—prefer safer methods like appending `<script>` tags.

---

### 6. Connecting to Google Suggest
Use a PHP proxy for cross-domain requests (pre-CORS workaround).

**`proxy.php`:**
```php
<?php
header("Content-Type: application/json");
$query = $_GET["q"] ?? "";
echo file_get_contents("http://suggestqueries.google.com/complete/search?output=firefox&q=" . urlencode($query));
?>
```

```javascript
function getSuggestions(query) {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "proxy.php?q=" + encodeURIComponent(query), true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            let suggestions = JSON.parse(xhr.responseText)[1];
            console.log(suggestions);
        }
    };
    xhr.send();
}
getSuggestions("php");
```

> **Modern Note**: Use CORS or fetch API with proper headers today.

---

### 7. Connecting to Other Domains Using Ajax
Handle cross-origin requests with PHP proxy.

**`crossdomain.php`:**
```php
<?php
header("Content-Type: text/plain");
echo file_get_contents("https://api.example.com/data");
?>
```

```javascript
function fetchCrossDomain() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "crossdomain.php", true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            console.log(xhr.responseText);
        }
    };
    xhr.send();
}
```

---

### 8. Logging in with Ajax and PHP
Authenticate users dynamically.

**`login.html`:**
```html
<form onsubmit="login(event)">
    <input type="text" id="username" name="username">
    <input type="password" id="password" name="password">
    <button type="submit">Login</button>
</form>
<div id="result"></div>
```

```javascript
function login(event) {
    event.preventDefault();
    let xhr = new XMLHttpRequest();
    xhr.open("POST", "login.php", true);
    xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };
    let data = "username=" + encodeURIComponent(document.getElementById("username").value) +
               "&password=" + encodeURIComponent(document.getElementById("password").value);
    xhr.send(data);
}
```

**`login.php`:**
```php
<?php
session_start();
$username = $_POST["username"] ?? "";
$password = $_POST["password"] ?? "";
if ($username === "admin" && $password === "secret") {
    $_SESSION["loggedin"] = true;
    echo "Login successful!";
} else {
    echo "Login failed.";
}
?>
```

---

### 9. Getting Data with Head Requests and Ajax
Fetch metadata with `HEAD`.

```javascript
function checkResource() {
    let xhr = new XMLHttpRequest();
    xhr.open("HEAD", "data.php", true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            let size = xhr.getResponseHeader("Content-Length");
            console.log("Size: " + size + " bytes");
        }
    };
    xhr.send();
}
```

**`data.php`:**
```php
<?php
header("Content-Length: " . filesize("sample.txt"));
?>
```

---

## 🔥 Quick Reference

| Technique            | Tool                   | Example Use Case          |
|----------------------|------------------------|---------------------------|
| Concurrent Requests  | Multiple XHRs         | Parallel data fetching    |
| Image Download       | `responseType: blob`  | Dynamic image loading     |
| Cross-Domain         | PHP Proxy             | External API access       |
| HEAD Requests        | `xhr.open("HEAD")`    | Metadata retrieval        |

---

## 🎯 Best Practices
- **Concurrency**: Track requests to avoid race conditions.
- **Security**: Use CORS properly, avoid `eval()` for JS.
- **Error Handling**: Handle timeouts and failures.
- **Modernity**: Consider `fetch()` with Promises for cleaner code.

**Fetch Alternative:**
```javascript
fetch("data.php")
    .then(response => response.text())
    .then(data => console.log(data))
    .catch(error => console.error("Error:", error));
```

---

[➡️ Next: Drawing Images On The Server](drawing_images.md)
