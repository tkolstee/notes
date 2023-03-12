#TODO: Flexbox, Grid, Box Model, positioning


`display: (block|inline|inline-block|none)`
Inline elements' width can't be modified
Block elements take up the entire width by default
inline-block elements can be on the same line but width can be modified
`display: none` removes an element and reflows the other elements.
To keep the spacing but hide the element, use `visibility: hidden` instead.

## Positioning
`position: (static|relative|absolute|fixed)`

### Static
All elements are static by default

### Relative
Relative to where it would've been positioned if it were static
Combined with `top`, `bottom`, `left`, or `right` - work like margins (e.g. left moves element right).
```css
img {
	postition: relative;
	left: 30px;
}
```
Move of a relative positioned element doesn't affect any other elements - as if old element was kept where its static positioning was. 

### Absolute
Take element out of flow of document and position relative to parent element. This is usually the `body` of the document.

`position: absolute; right: 30px;` 
positions an element 30px from the right of the parent container.


### Fixed
Positions element relative to viewport, not page. IOW it stays put when user scrolls.



---
# See Also
[A Complete Guide to Flexbox | CSS-Tricks - CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
[Flexbox Zombies 2.0](https://mastery.games/post/flexboxzombies2/)
[Flexbox Froggy - A game for learning CSS flexbox](https://flexboxfroggy.com/)
[Grid Garden - A game for learning CSS grid](https://codepip.com/games/grid-garden/)
