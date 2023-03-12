Frontend CSS/JS framework developed by Twitter
Open-Source and free on GitHub

## Installing

[Bootstrap Website](https://getbootstrap.com/)
Use CDN link


## Grid Layout

div class `row`
- div class `col` inside - evenly spaces across 100%
- div class `col-n` where n is 1/12 of the row width
- Responsive design with:
	- `col-lg-3` = 4 cols (of 3/12 width) on large screen
	- `col-md-4` = 3 cols (of 4/12) on medium screen
	- `col-sm-6` = 2 cols (of 6/12) on small screen
```html
<div class="row">
  <div class="col-lg-3 col-md-4 col-sm-6">foo</div>
  <div class="col-lg-3 col-md-4 col-sm-6">bar</div>
  <div class="col-lg-3 col-md-4 col-sm-6">baz</div>
  <div class="col-lg-3 col-md-4 col-sm-6">quux</div>
</div>
```

## Containers
Pad and center content.
Class `container` "jumps" at different breakpoints.
`container-fluid` adapts at every size and takes up 100% of width..

