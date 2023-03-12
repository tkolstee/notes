Determine what elements the style rules are applied to.

```CSS
/* HTML Tag */
    tagname {...}

/* By Class */
    .classname {...}

/* By ID */
    #idname {...}

/* By Attribute */
    input[type="checkbox"] {...}

/* Pseudo Element */
    /* Targets "placeholder" attribute in text input */
    ::placeholder {...}

/* Combinations */
    /* Paragraph tag with class "bodytext" */
    p.bodytext {...}
    /* h1 tag with id "title" */
    h1#title {...}
    /* Paragraph tag with classes "bodytext" AND "quotation" */
    p.bodytext.quotation {...}

/* Inner Tags */
    /* Element with class="quotation" inside element with class "box" */
    .box .quotation {...}
    /* Paragraph inside span */
    span p { ... }

/* Multiple Selectors */
    /* Any of tags p, h1, or (h2 with class title) */
    p,h1,h2.title {...}

/* States */
    /* Button in hover state */
    btn:hover {...}
    /* Last element of parent with class "item" */
    .item:last-child {...}

/* By Preceding Element */
    /* P text immediately following a checked input. */
    /* (e.g. strike through checked items). */
    input:checked+p {...}
```

----
# See Also
[CSS Selectors Reference](https://www.w3schools.com/cssref/css_selectors.php)
