# 🔗 Sessions, Cookies, and FTP in PHP

![PHP Sessions & Cookies](https://img.shields.io/badge/PHP-Sessions%20Cookies%20FTP-blue?style=for-the-badge&logo=php)  
**Manage state and transfers** - Use sessions, cookies, and FTP to handle user data and file operations!

---

## 🌟 Why Sessions, Cookies, and FTP?

- **Sessions**: Track user data across pages server-side.
- **Cookies**: Store data client-side for persistence.
- **FTP**: Transfer files between servers or clients.

---

## 🛠️ Techniques for State and File Management

### 1. Working with Sessions
Start a session to store data.

```php
session_start();
$_SESSION["username"] = "Alex";
echo "Welcome, " . $_SESSION["username"];
```

End a session:
```php
session_start();
session_destroy();
```

---

### 2. Setting a Cookie
Store data in the browser with `setcookie()`.

```php
setcookie("user", "Alex", time() + 3600, "/"); // Expires in 1 hour
echo "Cookie set!";
```

---

### 3. Reading a Cookie
Access cookies via `$_COOKIE`.

```php
if (isset($_COOKIE["user"])) {
    echo "User: " . $_COOKIE["user"];
} else {
    echo "No user cookie found.";
}
```

---

### 4. Setting Cookies’ Expiration
Control cookie lifespan.

```php
setcookie("theme", "dark", time() + (86400 * 30), "/"); // 30 days
// time() + seconds (e.g., 86400 = 1 day)
```

---

### 5. Deleting Cookies
Remove by setting an expired time.

```php
setcookie("user", "", time() - 3600, "/"); // Past time deletes it
echo "Cookie deleted!";
```

---

### 6. Working with FTP
Connect to an FTP server.

```php
$ftp = ftp_connect("ftp.example.com") or die("FTP connection failed!");
ftp_login($ftp, "username", "password") or die("FTP login failed!");
```

---

### 7. Downloading Files with FTP
Retrieve files with `ftp_get()`.

```php
$ftp = ftp_connect("ftp.example.com");
ftp_login($ftp, "username", "password");
ftp_get($ftp, "localfile.txt", "remotefile.txt", FTP_ASCII) or die("Download failed!");
ftp_close($ftp);
echo "File downloaded!";
```

---

### 8. Uploading Files with FTP
Send files with `ftp_put()`.

```php
$ftp = ftp_connect("ftp.example.com");
ftp_login($ftp, "username", "password");
ftp_put($ftp, "remotefile.txt", "localfile.txt", FTP_ASCII) or die("Upload failed!");
ftp_close($ftp);
echo "File uploaded!";
```

---

### 9. Deleting a File with FTP
Remove files with `ftp_delete()`.

```php
$ftp = ftp_connect("ftp.example.com");
ftp_login($ftp, "username", "password");
ftp_delete($ftp, "remotefile.txt") or die("Delete failed!");
ftp_close($ftp);
echo "File deleted!";
```

---

### 10. Creating and Removing Directories with FTP
Manage directories.

```php
$ftp = ftp_connect("ftp.example.com");
ftp_login($ftp, "username", "password");

// Create
ftp_mkdir($ftp, "newdir") or die("Directory creation failed!");
echo "Directory created!";

// Remove
ftp_rmdir($ftp, "newdir") or die("Directory removal failed!");
echo "Directory removed!";
ftp_close($ftp);
```

---

### 11. Sending E-mail
Send emails with `mail()`.

```php
$to = "recipient@example.com";
$subject = "Test Email";
$body = "Hello from PHP!";
$headers = "From: sender@example.com";
if (mail($to, $subject, $body, $headers)) {
    echo "Email sent!";
} else {
    echo "Email failed.";
}
```

> **Note**: `mail()` requires a configured mail server (e.g., SMTP via php.ini or a library like PHPMailer).

---

## 🔥 Quick Reference

| Feature            | Tool                  | Example Use Case         |
|--------------------|-----------------------|--------------------------|
| Sessions           | `session_start()`    | User login tracking     |
| Cookies            | `setcookie()`        | Remember preferences    |
| FTP Download       | `ftp_get()`          | Fetch remote files      |
| FTP Upload         | `ftp_put()`          | Backup to server        |
| Email              | `mail()`             | Notifications           |

---

## 🎯 Best Practices
- **Sessions**: Use `session_regenerate_id()` for security.
- **Cookies**: Set `HttpOnly` and `Secure` flags (`setcookie("name", "value", ["httponly" => true, "secure" => true]);`).
- **FTP**: Use SFTP/FTPS for secure transfers when possible.
- **Email**: Use libraries (e.g., PHPMailer) for complex emails.
- **Error Handling**: Check return values and log failures.

**Secure Cookie Example:**
```php
setcookie("session", "id123", [
    "expires" => time() + 3600,
    "path" => "/",
    "secure" => true,
    "httponly" => true
]);
```

---
[➡️ Next: Ajax](ajax.md)
