# 📂 File Handling in PHP

![PHP File Handling](https://img.shields.io/badge/PHP-File%20Handling-blue?style=for-the-badge&logo=php)  
**Master file operations** - Read, write, and manage files with PHP’s powerful tools!

---

## 🌟 Why File Handling?

PHP’s file handling functions let you interact with the filesystem—reading data, writing logs, parsing configs, and more. Whether it’s text or binary, PHP has you covered.

---

## 🛠️ File Handling Techniques

### 1. Opening Files Using fopen
Open a file with a mode (e.g., read, write).

```php
$file = fopen("data.txt", "r") or die("Cannot open file!");
// Use $file...
```

| Mode | Description            |
|------|------------------------|
| `r`  | Read only             |
| `w`  | Write only (overwrite)|
| `a`  | Append                |
| `r+` | Read and write        |

---

### 2. Looping over a File’s Contents with feof
Read until the end of file (EOF).

```php
$file = fopen("data.txt", "r");
while (!feof($file)) {
    echo fgets($file);
}
fclose($file);
```

---

### 3. Reading Text from a File Using fgets
Read line by line.

```php
$file = fopen("data.txt", "r");
$line = fgets($file); // First line
echo $line;
fclose($file);
```

---

### 4. Closing a File
Always close with `fclose()`.

```php
$file = fopen("data.txt", "r");
// Read/write operations...
fclose($file); // Clean up
```

---

### 5. Reading from a File Character by Character with fgetc
Read one character at a time.

```php
$file = fopen("data.txt", "r");
while (!feof($file)) {
    echo fgetc($file);
}
fclose($file);
```

---

### 6. Reading a Whole File at Once with file_get_contents
Get all content as a string.

```php
$content = file_get_contents("data.txt");
echo $content;
```

---

### 7. Reading a File into an Array with file
Load lines into an array.

```php
$lines = file("data.txt", FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);
print_r($lines);
```

---

### 8. Checking if a File Exists with file_exists
Verify file presence.

```php
if (file_exists("data.txt")) {
    echo "File found!";
} else {
    echo "File missing.";
}
```

---

### 9. Getting File Size with filesize
Measure file size in bytes.

```php
$size = filesize("data.txt");
echo "Size: $size bytes";
```

---

### 10. Reading Binary Reads with fread
Read a specific number of bytes.

```php
$file = fopen("image.bin", "rb");
$data = fread($file, 10); // First 10 bytes
fclose($file);
echo bin2hex($data);
```

---

### 11. Parsing Files with fscanf
Read formatted input.

```php
$file = fopen("scores.txt", "r");
fscanf($file, "%d %s", $score, $name);
echo "Score: $score, Name: $name";
fclose($file);
```

---

### 12. Parsing ini Files with parse_ini_file
Load `.ini` configurations.

**`config.ini`:**
```
[settings]
timeout = 30
```

```php
$config = parse_ini_file("config.ini");
echo "Timeout: " . $config["timeout"]; // Outputs: Timeout: 30
```

---

### 13. Getting File Info with stat
Retrieve file metadata.

```php
$info = stat("data.txt");
echo "Last modified: " . date("Y-m-d", $info["mtime"]);
```

---

### 14. Setting the File Pointer’s Location with fseek
Move to a specific position.

```php
$file = fopen("data.txt", "r");
fseek($file, 5); // Skip 5 bytes
echo fgets($file); // Read from there
fclose($file);
```

---

### 15. Copying Files with copy
Duplicate a file.

```php
if (copy("source.txt", "dest.txt")) {
    echo "File copied!";
} else {
    echo "Copy failed.";
}
```

---

### 16. Deleting Files with unlink
Remove a file.

```php
if (unlink("old.txt")) {
    echo "File deleted!";
} else {
    echo "Deletion failed.";
}
```

---

### 17. Writing to a File with fwrite
Write data to a file.

```php
$file = fopen("log.txt", "w");
fwrite($file, "Error at " . date("H:i"));
fclose($file);
```

---

### 18. Reading and Writing Binary Files
Handle binary data with `rb`/`wb`.

```php
$file = fopen("data.bin", "wb");
fwrite($file, pack("i", 123)); // Write integer
fclose($file);

$file = fopen("data.bin", "rb");
$num = unpack("i", fread($file, 4))["i"];
echo $num; // Outputs: 123
fclose($file);
```

---

### 19. Appending to Files with fwrite
Add to the end with `a` mode.

```php
$file = fopen("log.txt", "a");
fwrite($file, "\nNew entry");
fclose($file);
```

---

### 20. Writing a File All at Once with file_put_contents
Write easily without opening.

```php
file_put_contents("note.txt", "Quick note");
```

---

### 21. Locking Files
Prevent concurrent access with `flock`.

```php
$file = fopen("shared.txt", "w");
if (flock($file, LOCK_EX)) { // Exclusive lock
    fwrite($file, "Locked write");
    flock($file, LOCK_UN); // Release
} else {
    echo "Couldn’t lock file.";
}
fclose($file);
```

---

## 🔥 Quick Reference

| Function             | Purpose                   | Example Use Case         |
|----------------------|---------------------------|--------------------------|
| `fopen`/`fclose`     | Open/close files         | Basic I/O               |
| `file_get_contents`  | Read all at once         | Simple reads            |
| `fwrite`             | Write data               | Logging                 |
| `file_exists`        | Check existence          | Validation              |
| `flock`              | Lock files               | Multi-user apps         |

---

## 🎯 Best Practices
- **Error Handling**: Use `or die()` or exceptions for failures.
- **Close Files**: Always `fclose()` to free resources.
- **Permissions**: Check file permissions before operations.
- **Security**: Sanitize file paths to prevent traversal attacks.

```php
$file = @fopen("data.txt", "r");
if ($file === false) {
    throw new Exception("File not found!");
}
echo fgets($file);
fclose($file);
```

---
[➡️ Next: Working With Databases](databases.md)
