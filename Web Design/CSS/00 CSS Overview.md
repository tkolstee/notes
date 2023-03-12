

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

## Declarations

### Display

| Setting              | Description                          |
| -------------------- | ------------------------------------ |
| display: block;        | Display as block element (width 100%)             |
| display: inline;       | Display as inline element (width minimized)            |
| display: inline-block; | Hybrid inline/block element (like images)         |
| display: none;         | Removed from page flow and not shown |

### Visibility
| Declaration         | Description                    |
| ------------------- | ------------------------------ |
| visibility: visible; | Element is displayed as normal |
| visibility: hidden;  | Element is hidden from view but place is held                               |

### Positioning and Layout
| Declaration         | Description                                   |
| ------------------- | --------------------------------------------- |
| position: static;   | Default positioning                           |
| position: relative; | Relative to where 'static' would be.          |
| position: absolute; | Relative to nearest parent that is positional |
| position: fixed;    | Fixed relative to viewport, not page.         |


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




