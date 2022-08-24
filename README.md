# Adult image validation

This is a simple PHP class that allows you to check if the image contains adult content or not. We experimented with a lot of images and find out that the image having score greater than 60 should be considered as an adult image in most cases.

# How to use ?

Support you have a simple HTML file that allows user to upload an image:

```html
<form method="POST" action="upload.php" enctype="multipart/form-data">
	<input type="file" name="file" />
	<input type="submit" />
</form>
```

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
```

1. First, we are simply including the class in our PHP file.
2. Then we save the image file as "image.png", you can set any name of your choice.
3. Then we are creating an instance of ```ImageFilter``` class.
4. Then we are getting the score of newly created image file. A score of 61 and above is considered to be contain nudity content.
5. Then we are removing the image file we saved.
6. And display the score to the user, you can remove this line if you do not want to show the scores to the user.
7. Finally, we are putting a condition that says "if score is greater than 60, then display an error message."

You can try with other images too and feel free to give feedback for improvements.
