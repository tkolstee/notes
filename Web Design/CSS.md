## General Syntax
```CSS
# Comment
selector {
	name: value;    # aka declaration
	name: value;
}
```

## Selectors
```css
### By tag
h2 { color: black }

### By ID
#myid { color: black }

### Class
.myclass { color: black }

### Attribute
input[type="checkbox"] { color: black }

### Pseudo-element
::placeholder { color: black }

### Combinations with comma
p.bodytext { color: black }       # p tag with class bodytext
h1#title { color: black }         # h1 tag with ID title
.article.callout { color: black } # tag with both classes

### Inner tag
.box .quotation { color: black }  # quotation inside box element
span p                            # p tag inside span tag

### Multiple Selectors:
h1,p,span,a                       # any of the comma-separated tags

### States
.btn:hover                        # class btn when mouse hovers over it

### Ordering
.item:last-child                  # Last element of parent with class item

### Preceding element
input:checked+p                   # p immediately after checked element
```


## Media Queries
```css
@media print {}                              # when printed
@media speech {}                             # screen reader
@media only screen and (max-width: 600px) {} # Screen <= 600px wide
@media screen and (min-width: 900px) {}      # Screen >= 900px wide
```

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
| flexbox:                     |                                               |



```css
border: 5px;
border: 5px 2px 5px 2px;   // top, right, bottom, left
color: gray;
margin: 5px;
width: 500px;
```



## Layout

### Flexbox
flex container and flex items

Container properties
```css
display: flex;
flex-direction: column;
flex-wrap
flex-flow
justify-content
align-items
align-content
```

Flex item properties:
```css
order
flex-grow
flex-shrink
flex-basis
flex
align-self
```


### Grid
grid-based layout system


