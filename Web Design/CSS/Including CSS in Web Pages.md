
```html
<!-- link tag to include from URL -->
<link rel="stylesheet" href="mystyle.css">

<!-- Internal between <style> tags -->
<style>
h1 {
	color: maroon;
	margin-left: 40px;
}
</style>

<!-- Inline in HTML attributes -->
<p style=”font-weight: bold; font-size: 20px; color: blue;”>
```

Applied in order (highest to lowest priority)

1.  Inline style (inside HTML attribute)
2.  External and internal stylesheets (link or style tags in HEAD, last one defined wins)
3.  Browser default
