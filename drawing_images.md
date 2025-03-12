# 🎨 Drawing Images on the Server with PHP

![PHP Image Drawing](https://img.shields.io/badge/PHP-Image%20Drawing-blue?style=for-the-badge&logo=php)  
**Create visuals dynamically** - Use PHP to generate and manipulate images on the server!

---

## 🌟 Why Draw Images Server-Side?

PHP’s GD library lets you create and modify images programmatically—perfect for charts, captchas, or custom graphics without relying on client-side tools.

> **Prerequisite**: Ensure the GD extension is enabled (`phpinfo()` should show GD support).

---

## 🛠️ Image Drawing Techniques

### 1. Creating an Image
Start with a blank canvas using `imagecreate()` or `imagecreatetruecolor()`.

```php
$width = 200;
$height = 100;
$image = imagecreatetruecolor($width, $height); // True color image
```

---

### 2. Displaying Images in HTML Pages
Output the image with proper headers.

**`image.php`:**
```php
<?php
$image = imagecreatetruecolor(200, 100);
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
?>
```

**`index.html`:**
```html
<img src="image.php" alt="Dynamic Image">
```

---

### 3. Drawing Lines
Use `imageline()` to draw lines.

```php
$image = imagecreatetruecolor(200, 100);
$black = imagecolorallocate($image, 0, 0, 0); // RGB: Black
imageline($image, 10, 10, 190, 90, $black); // (x1, y1, x2, y2, color)
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 4. Setting Line Thickness
Adjust thickness with `imagesetthickness()`.

```php
$image = imagecreatetruecolor(200, 100);
$black = imagecolorallocate($image, 0, 0, 0);
imagesetthickness($image, 5); // 5 pixels thick
imageline($image, 10, 10, 190, 90, $black);
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 5. Drawing Rectangles
Use `imagerectangle()` for outlines.

```php
$image = imagecreatetruecolor(200, 100);
$red = imagecolorallocate($image, 255, 0, 0);
imagerectangle($image, 20, 20, 180, 80, $red); // (x1, y1, x2, y2, color)
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 6. Drawing Ellipses
Use `imageellipse()` for circles or ovals.

```php
$image = imagecreatetruecolor(200, 100);
$blue = imagecolorallocate($image, 0, 0, 255);
imageellipse($image, 100, 50, 80, 40, $blue); // (center_x, center_y, width, height, color)
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 7. Drawing Arcs
Use `imagearc()` for curved segments.

```php
$image = imagecreatetruecolor(200, 100);
$green = imagecolorallocate($image, 0, 255, 0);
imagearc($image, 100, 50, 80, 40, 0, 180, $green); // (center_x, center_y, width, height, start_angle, end_angle, color)
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 8. Drawing Polygons
Use `imagepolygon()` with point arrays.

```php
$image = imagecreatetruecolor(200, 100);
$yellow = imagecolorallocate($image, 255, 255, 0);
$points = [50, 20, 150, 20, 100, 80]; // [x1, y1, x2, y2, x3, y3]
imagepolygon($image, $points, 3, $yellow); // (points, num_points, color)
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 9. Filling in Figures
Use `imagefill()` or `imagefilled*()` functions.

```php
$image = imagecreatetruecolor(200, 100);
$red = imagecolorallocate($image, 255, 0, 0);
imagefilledrectangle($image, 20, 20, 180, 80, $red);
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 10. Drawing Individual Pixels
Set pixels with `imagesetpixel()`.

```php
$image = imagecreatetruecolor(200, 100);
$black = imagecolorallocate($image, 0, 0, 0);
imagesetpixel($image, 100, 50, $black); // (x, y, color)
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 11. Drawing Text
Add text with `imagettftext()` (requires TTF font).

```php
$image = imagecreatetruecolor(200, 100);
$white = imagecolorallocate($image, 255, 255, 255);
imagettftext($image, 20, 0, 10, 50, $white, "arial.ttf", "Hello, PHP!");
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 12. Drawing Vertical Text
Rotate text with angle in `imagettftext()`.

```php
$image = imagecreatetruecolor(200, 100);
$white = imagecolorallocate($image, 255, 255, 255);
imagettftext($image, 20, 90, 50, 90, $white, "arial.ttf", "Vertical"); // 90° angle
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 13. Working with Image Files
Load existing images with `imagecreatefrom*()`.

```php
$image = imagecreatefrompng("source.png");
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---

### 14. Tiling Images
Repeat an image with `imagesettile()` and `imagefill()`.

```php
$image = imagecreatetruecolor(200, 100);
$tile = imagecreatefrompng("tile.png");
imagesettile($image, $tile);
imagefill($image, 0, 0, IMG_COLOR_TILED);
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
imagedestroy($tile);
```

---

### 15. Copying Images
Copy parts with `imagecopy()`.

```php
$dest = imagecreatetruecolor(200, 100);
$src = imagecreatefrompng("source.png");
imagecopy($dest, $src, 0, 0, 50, 50, 100, 50); // (dest, src, dest_x, dest_y, src_x, src_y, width, height)
header("Content-Type: image/png");
imagepng($dest);
imagedestroy($dest);
imagedestroy($src);
```

---

## 🔥 Quick Reference

| Task             | Function                  | Example Use Case         |
|------------------|---------------------------|--------------------------|
| Create Image     | `imagecreatetruecolor()` | Blank canvas            |
| Draw Shapes      | `imagerectangle()`       | Graphics, charts         |
| Add Text         | `imagettftext()`         | Labels, captchas         |
| Work with Files  | `imagecreatefrompng()`   | Edit existing images     |

---

## 🎯 Best Practices
- **Cleanup**: Always use `imagedestroy()` to free memory.
- **Headers**: Set `Content-Type` before output.
- **Fonts**: Ensure TTF files are available for text.
- **Performance**: Cache generated images when possible.

**Full Example:**
```php
$image = imagecreatetruecolor(200, 100);
$bg = imagecolorallocate($image, 200, 200, 200); // Light gray
$red = imagecolorallocate($image, 255, 0, 0);
imagefill($image, 0, 0, $bg);
imagefilledellipse($image, 100, 50, 50, 50, $red);
header("Content-Type: image/png");
imagepng($image);
imagedestroy($image);
```

---
[➡️ Next: XML and RSS](xml_rss.md)
