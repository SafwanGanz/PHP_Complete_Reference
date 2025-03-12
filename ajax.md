# 🌐 Ajax in PHP

![PHP Ajax](https://img.shields.io/badge/PHP-Ajax-blue?style=for-the-badge&logo=php)  
**Make web apps dynamic** - Use Ajax with PHP to fetch and send data without page reloads!

---

## 🌟 What Is Ajax?

Ajax (Asynchronous JavaScript and XML) lets you communicate with a server asynchronously, updating parts of a web page without refreshing. Paired with PHP, it’s perfect for real-time features.

---

## 🛠️ Ajax Techniques with PHP

### 1. Getting Started with Ajax
Ajax requires JavaScript, an `XMLHttpRequest` object, and a server-side script (PHP).

---

### 2. Writing Ajax
Basic structure: create, open, send, and handle.

**`index.html`:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Ajax Example</title>
</head>
<body>
    <button onclick="loadData()">Load Data</button>
    <div id="result"></div>
    <script src="script.js"></script>
</body>
</html>
```

---

### 3. Creating the XMLHttpRequest Object
Instantiate `XMLHttpRequest`.

**`script.js`:**
```javascript
function loadData() {
    let xhr = new XMLHttpRequest();
    // Further setup...
}
```

---

### 4. Opening the XMLHttpRequest Object
Set the request method and URL.

```javascript
function loadData() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "data.php", true); // true = asynchronous
    // Send and handle...
}
```

---

### 5. Handling Downloaded Data
Process the server response.

```javascript
function loadData() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "data.php", true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };
    // Start download...
}
```

---

### 6. Starting the Download
Send the request.

```javascript
function loadData() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "data.php", true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };
    xhr.send();
}
```

**`data.php`:**
```php
<?php
echo "Hello from PHP!";
?>
```

---

### 7. Creating XMLHttpRequest Objects (Cross-Browser)
Handle older browsers (rarely needed today).

```javascript
function createXHR() {
    try {
        return new XMLHttpRequest();
    } catch (e) {
        try {
            return new ActiveXObject("Microsoft.XMLHTTP"); // IE6
        } catch (e) {
            return null;
        }
    }
}
let xhr = createXHR();
```

---

### 8. Ajax with Some PHP
Combine client and server.

**`data.php`:**
```php
<?php
$name = "User";
echo "Welcome, $name!";
?>
```

**`script.js`:**
```javascript
function loadData() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "data.php", true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };
    xhr.send();
}
```

---

### 9. Passing Data to the Server with GET
Send parameters in the URL.

```javascript
function sendData() {
    let xhr = new XMLHttpRequest();
    let value = "test";
    xhr.open("GET", "process.php?data=" + encodeURIComponent(value), true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };
    xhr.send();
}
```

**`process.php`:**
```php
<?php
$data = $_GET["data"] ?? "No data";
echo "Received: $data";
?>
```

---

### 10. Passing Data to the Server with POST
Send data in the request body.

```javascript
function sendPost() {
    let xhr = new XMLHttpRequest();
    xhr.open("POST", "process.php", true);
    xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };
    let data = "name=Alex";
    xhr.send(data);
}
```

**`process.php`:**
```php
<?php
$name = $_POST["name"] ?? "Guest";
echo "Hello, $name!";
?>
```

---

### 11. Handling XML
Return and parse XML data.

**`xml.php`:**
```php
<?php
header("Content-Type: text/xml");
echo '<?xml version="1.0" encoding="UTF-8"?>
<user>
    <name>Alex</name>
    <age>25</age>
</user>';
?>
```

```javascript
function loadXML() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "xml.php", true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            let xml = xhr.responseXML;
            let name = xml.getElementsByTagName("name")[0].textContent;
            document.getElementById("result").innerHTML = "Name: " . name;
        }
    };
    xhr.send();
}
```

---

### 12. Handling XML with PHP
Generate and process XML.

**`xml-process.php`:**
```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $xml = simplexml_load_string(file_get_contents("php://input"));
    $name = (string)$xml->name;
    echo "Processed: $name";
}
?>
```

```javascript
function sendXML() {
    let xhr = new XMLHttpRequest();
    xhr.open("POST", "xml-process.php", true);
    xhr.setRequestHeader("Content-Type", "text/xml");
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };
    let xml = '<?xml version="1.0"?><user><name>Bella</name></user>';
    xhr.send(xml);
}
```

---

## 🔥 Quick Reference

| Task                | Tool                   | Example Use Case         |
|---------------------|------------------------|--------------------------|
| Create XHR          | `new XMLHttpRequest()`| Start Ajax               |
| GET Data            | `xhr.open("GET")`     | Fetch simple data        |
| POST Data           | `xhr.open("POST")`    | Send form data           |
| Handle XML          | `responseXML`         | Structured responses     |

---

## 🎯 Best Practices
- **Async**: Use `true` for non-blocking requests.
- **Security**: Validate and sanitize server-side data.
- **Error Handling**: Check `xhr.status` (e.g., 404, 500).
- **Modernity**: Consider `fetch()` API for newer projects.

**Error Handling Example:**
```javascript
xhr.onreadystatechange = function () {
    if (xhr.readyState == 4) {
        if (xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        } else {
            document.getElementById("result").innerHTML = "Error: " + xhr.status;
        }
    }
};
```

---
[➡️ Next: Advanced Ajax](advanced_ajax.md)
