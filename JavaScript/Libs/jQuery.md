JS framework for manipulating DOM

## Including
Using CDN Link:
```html
<script
  src="https://code.jquery.com/jquery-3.6.3.min.js"
  integrity="sha256-pvPw+upLPUjgMXY0G+8O0xUf+/Im1MZjXxxgOcBQBXU="
  crossorigin="anonymous"
></script>
```

[Hosted Libraries  |  Google Developers](https://developers.google.com/speed/libraries/devguide#jquery)

## jQuery IntelliSense in VSCode
If you use npm and list jQuery in `package.json` this should happen automatically. ([Source](https://stackoverflow.com/questions/41777327/jquery-intellisense-in-vs-code))

Add file `jsconfig.json` to project folder ([Source](https://medium.com/@vibhoragrawal/turning-on-the-auto-complete-for-jquery-in-vscode-1e047738beae)):
```json
{
  "typeAcquisition": {
    "include": [
	  "jquery"
    ]
  }
}
```

## Selecting Elements
Selectors work as with CSS
The following are equivalent.
```javascript
// Select one - first occurrence
document.querySelector("h1")

// Select all at once
jquery("h1")
$("h1")
```

Selectors are as with CSS.
- By Element: `$("h1")`
- By Class: `$(".btn")`
- Nested: `$(".article p")

## Manipulating Elements

### Styles
```javascript
// get - returns first if >1 match
$("h1").css("color");

// set
$("h1").css("font-size", "3rem");
```

### Classes
```javascript
$("h1").addClass("classOne");
$("h1").removeClass("classOne");
$("h1").addClass("classOne classTwo");

// True if ANY matches are true
var xyz = $("h1").hasClass("classOne")  

// True if ANY matches have ALL of the classes listed.
var xyz = $("h1").hasClass("classOne classTwo")
```

### Inner Text
```javascript
$("button").text("foo")
$("p").html("<b>foo</b>bar")
```

### Attributes
```javascript
var oldsrc = $("img").attr("src")
$("img").attr("src", "http://...")
```


## Waiting until document is ready
```javascript
$(document).ready(callback_fn);
```

## Adding before/after
- `elem.before(htmltext)` - Add before element's opening tag
- `elem.after(htmltext)` - Add after element's closing tag
- `elem.prepend(htmltext)` - Add after element's opening tag
- `elem.append(htmltext)` - Add before element's closing tag

## Removing Elements
- `elem.remove()`

## Hiding and Showing Elements
- `.hide()`, `.show()`, `.toggle()` appear/disappear
- `.fadeOut()`, `.fadeIn()`, `fadeToggle()` fade in/out
- `.slideUp()`, `.slideDown()`, `.slideToggle()` slide in/out of view
- `.animate({ fontSize: 90, width: 100 })` animate limited style changes
- Chaining: `elem.slideUp().slideDown().animate({ opacity: 0.5 })`
