# Adult image validation

This is a simple PHP class that allows you to check if the image contains adult content or not. We experimented with a lot of images and find out that the image having score greater than 60 should be considered as an adult image in most cases.

# How to use ?

Support you have a simple HTML file that allows user to upload an image:

```html
<form method="POST" action="upload.php" enctype="multipart/form-data">
	<input type="file" name="file" />
	<input type="submit" />
</form>
```html

Then in your "upload.php", you can use this class in the following manner:

```php
<?php

require_once "class.ImageFilter.php";

move_uploaded_file($_FILES["file"]["tmp_name"], "image.png");

$filter = new ImageFilter();
$score = $filter->GetScore("image.png");

unlink("image.png");

echo $score;

if ($score > 60)
{
	echo "<p>Image contains adult content.</p>";
}
```php
