# 🗄️ Working with Databases in PHP

![PHP Databases](https://img.shields.io/badge/PHP-Databases-blue?style=for-the-badge&logo=php)  
**Store and retrieve data** - Connect PHP to databases for dynamic, data-driven applications!

---

## 🌟 What Is a Database?

A database is an organized collection of data, typically stored and accessed electronically. Relational databases (e.g., MySQL) use tables with rows and columns to manage data efficiently.

---

## 🛠️ Database Basics with PHP

### 1. Some Essential SQL
SQL (Structured Query Language) is the language for interacting with databases.

| Command      | Purpose                  | Example                          |
|--------------|--------------------------|----------------------------------|
| `SELECT`     | Retrieve data           | `SELECT * FROM users;`          |
| `INSERT`     | Add data                | `INSERT INTO users (name) VALUES ('Alex');` |
| `UPDATE`     | Modify data             | `UPDATE users SET age = 25 WHERE id = 1;` |
| `DELETE`     | Remove data             | `DELETE FROM users WHERE id = 1;` |
| `CREATE`     | Create tables/databases | `CREATE TABLE users (id INT, name VARCHAR(50));` |

---

### 2. Creating a MySQL Database
Use MySQL to create a database (via command line or phpMyAdmin).

```sql
CREATE DATABASE mydb;
```

---

### 3. Creating a New Table
Define a table structure.

```sql
USE mydb;
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);
```

---

### 4. Putting Data into the New Database
Insert initial data.

```sql
INSERT INTO users (name, age) VALUES ('Alex', 25), ('Bella', 30);
```

---

### 5. Accessing the Database in PHP
Use `mysqli` or PDO (we’ll use `mysqli` here).

---

### 6. Connecting to the Database Server
Establish a server connection.

```php
$host = "localhost";
$user = "root";
$pass = "";
$conn = mysqli_connect($host, $user, $pass) or die("Connection failed: " . mysqli_connect_error());
```

---

### 7. Connecting to the Database
Select the database.

```php
$dbname = "mydb";
mysqli_select_db($conn, $dbname) or die("Database selection failed: " . mysqli_error($conn));
```

---

### 8. Reading the Table
Query the database.

```php
$query = "SELECT * FROM users";
$result = mysqli_query($conn, $query) or die("Query failed: " . mysqli_error($conn));
```

---

### 9. Displaying the Table Data
Fetch and display results.

```php
while ($row = mysqli_fetch_assoc($result)) {
    echo "ID: " . $row["id"] . ", Name: " . $row["name"] . ", Age: " . $row["age"] . "<br>";
}
// Outputs:
// ID: 1, Name: Alex, Age: 25
// ID: 2, Name: Bella, Age: 30
```

---

### 10. Closing the Connection
Free resources.

```php
mysqli_close($conn);
```

---

### 11. Updating Databases
Modify existing records.

```php
$query = "UPDATE users SET age = 26 WHERE name = 'Alex'";
mysqli_query($conn, $query) or die("Update failed: " . mysqli_error($conn));
```

---

### 12. Inserting New Data Items into a Database
Add new rows.

```php
$name = "Charlie";
$age = 22;
$query = "INSERT INTO users (name, age) VALUES ('$name', $age)";
mysqli_query($conn, $query) or die("Insert failed: " . mysqli_error($conn));
```

---

### 13. Deleting Records
Remove rows.

```php
$query = "DELETE FROM users WHERE id = 1";
mysqli_query($conn, $query) or die("Delete failed: " . mysqli_error($conn));
```

---

### 14. Creating New Tables
Add tables via PHP.

```php
$query = "CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    price DECIMAL(10,2)
)";
mysqli_query($conn, $query) or die("Table creation failed: " . mysqli_error($conn));
```

---

### 15. Creating a New Database
Create databases via PHP (requires privileges).

```php
$query = "CREATE DATABASE newdb";
mysqli_query($conn, $query) or die("Database creation failed: " . mysqli_error($conn));
```

---

### 16. Sorting Your Data
Order results with `ORDER BY`.

```php
$query = "SELECT * FROM users ORDER BY age ASC";
$result = mysqli_query($conn, $query);
while ($row = mysqli_fetch_assoc($result)) {
    echo $row["name"] . " (" . $row["age"] . ")<br>";
}
```

---

## 🔥 Full Example

```php
<?php
$conn = mysqli_connect("localhost", "root", "", "mydb") or die("Connection failed");
$query = "SELECT * FROM users";
$result = mysqli_query($conn, $query);
?>
<table border="1">
    <tr><th>ID</th><th>Name</th><th>Age</th></tr>
    <?php while ($row = mysqli_fetch_assoc($result)): ?>
        <tr>
            <td><?php echo $row["id"]; ?></td>
            <td><?php echo $row["name"]; ?></td>
            <td><?php echo $row["age"]; ?></td>
        </tr>
    <?php endwhile; ?>
</table>
<?php mysqli_close($conn); ?>
```

---

## 🎯 Best Practices
- **Security**: Use prepared statements to prevent SQL injection.
- **Error Handling**: Check for failures and log errors.
- **Connections**: Close connections when done.
- **Modernity**: Prefer PDO over `mysqli` for flexibility.

**Prepared Statement Example:**
```php
$stmt = mysqli_prepare($conn, "INSERT INTO users (name, age) VALUES (?, ?)");
mysqli_stmt_bind_param($stmt, "si", $name, $age);
$name = "Dana";
$age = 28;
mysqli_stmt_execute($stmt);
mysqli_stmt_close($stmt);
```

---
[➡️ Next: Sessions, Cookies And FTP](session_cookies_ftp.md)
