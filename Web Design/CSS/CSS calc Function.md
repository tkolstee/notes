`calc()` is a CSS function that allows you to perform mathematical calculations to determine a value. 

It can be used with any of the CSS properties that accept a value, such as `width`, `height`, `padding`, `margin`, etc.

The syntax for `calc()` is straightforward: you simply write out your calculation within the parentheses. Here's an example:

```css
width: calc(100% - 20px);
height: calc(100vh - 2rem);
padding: calc(10px + 2%);
```

The operators `+`, `-`, `*`, and `/` can be used inside the calc function.

```ad-warning
Older versions of Internet Explorer (IE 8 and earlier) do not support `calc()`.
```
