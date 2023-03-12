

## General Syntax
```css
/* General form: */
selector {
	property: value;  /* aka declaration */
	property: value;
}

/* Example */
h1 {
	color: white;
	text-align: center;
}
```

## Including CSS in Web Pages

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



[[CSS Selectors]]
[[CSS Media Queries]]
[[CSS Colors]]
[[CSS Sizing and Positioning Units]]
[[CSS calc Function]]
[[CSS Layout and Positioning]]


---
# See Also
W3Schools [Tutorial](https://www.w3schools.com/css/), [Reference](https://www.w3schools.com/cssref/)





