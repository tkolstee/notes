

## General Syntax
```css
/* General form: */
selector {
	property: value;
	property: value;
}

/* Example */
h1 {
	color: white;
	text-align: center;
}
```

[[Including CSS in Web Pages]]
[[CSS Selectors]]
[[CSS Media Queries]]
[[CSS Colors]]

-   `px`: pixels
-   `em`: relative to the font-size of the element (1em is equal to the font-size of the parent element)
-   `rem`: relative to the font-size of the root element (which is usually the `<html>` element)
-   `%`: percentage of the parent element's size
-   `vh`: viewport height (1vh is equal to 1% of the viewport height)
-   `vw`: viewport width (1vw is equal to 1% of the viewport width)
-   `vmin`: viewport minimum (1vmin is equal to the smaller of 1vw or 1vh)
-   `vmax`: viewport maximum (1vmax is equal to the larger of 1vw or 1vh)

There are other less common sizing units as well, such as `ex`, `ch`, `fr`, `calc()`, etc., but the ones listed above are the most commonly used.



`calc()` is a CSS function that allows you to perform mathematical calculations to determine a value. It can be used with any of the CSS properties that accept a value, such as `width`, `height`, `padding`, `margin`, etc.

The syntax for `calc()` is straightforward: you simply write out your calculation within the parentheses. Here's an example:

cssCopy code

`width: calc(100% - 20px);`

In this example, the `width` of the element will be set to `100%` of its parent container's width, minus `20px`. So if the parent container is `500px` wide, the element's `width` will be `480px`.

You can use any mathematical operator inside `calc()`, including `+`, `-`, `*`, and `/`. You can also use other units within your calculation, as long as they're compatible with the other units involved. For example:

cssCopy code

`height: calc(100vh - 2rem); padding: calc(10px + 2%);`

Note that `calc()` is supported in all modern browsers, but older versions of Internet Explorer (IE 8 and earlier) do not support it. If you need to support older browsers, you may need to use alternative techniques to achieve the same effect.




### Flexbox
[[Cheat Sheet]]
flexible container and flexible items:
```css
display: flex;
flex-direction: column;
flex-wrap
flex-flow
justify-content
align-items
align-content

# Flex item properties
order
flex-grow
flex-shrink
flex-basis
flex
align-self
```




#TODO: Expand on Flexbox, Grid Layout, Box Model

---
# See Also
W3Schools [Tutorial](https://www.w3schools.com/css/), [Reference](https://www.w3schools.com/cssref/)
[A Complete Guide to Flexbox | CSS-Tricks - CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
[Flexbox Zombies 2.0](https://mastery.games/post/flexboxzombies2/)
[Flexbox Froggy - A game for learning CSS flexbox](https://flexboxfroggy.com/)
[Grid Garden - A game for learning CSS grid](https://codepip.com/games/grid-garden/)
[CSS Selectors Reference](https://www.w3schools.com/cssref/css_selectors.php)




