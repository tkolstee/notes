## Block Quotes
Prefix each line that is part of the blockquote with `>`.
Multiple levels can be given with multiple `>` signs.

## Callouts
Create a blockquote (prefix lines with `>`), then format the first line with:
```markdown
> [!TYPE]+ This is the title
```
- Type will determine the icon and style
	- note, abstract, summary, tldr, info, todo, tip, hint, important, success, check, done, question, help, faq, warning, caution, attention, failure, fail, missing, danger, error, bug, example, quote, cite
- `+` indicates the callout starts out expanded, `-` starts out collapsed
- Title will be displayed on the first line of the blockquote.
	- Can contain markdown

## Checkboxes
Use empty brackets after a bullet:
```markdown
- [ ] This is a checkbox that is not checked.
- [x] This is a checked checkbox.
- [q] Check with any character - may alter meanings.
```
Checkboxes marked with `x` will have their text struck through, other characters will not.

## Code

### Inline Code
Wrap code text in backticks (\`)
```Markdown
Use `self` to access instance variables.
```

### Code Blocks
Use multiple backticks (3 or more) plus the language name.
Will syntax highlight.
````markdown
```js
function fancyAlert(arg) {
	if (arg) {
		#.facebox({div:'#foo'})
	}
}
```
````

## Comments
Use `%%` to start and end comments. 
May be multiline or inline.
Will show in edit mode but not preview mode.

## Embedding
Embed a whole document: `![[Wikilink]]`
Embed a named section: `![[Wikilink^section]]`
Embed a heading: `![[Wikilink#heading]]`

## Inline Text Styling

### Italics
Enclose in asterisks or underscores like `_this_` or `*this*`.

### Bold
Enclose in double asterisks or underscores, like `__this__` or `**this**`.

### Strikethrough
Use double tildes like `~~this~~`

### Highlighting
Enclose in more than one equal sign like `==this==`

## Footnotes

### Simple Footnotes
Use `[^1]` at the footnote's location in the main text, and `[^1]: text here` to provide the actual footnote.

In place of `1` you can use text.

The footnote text will extend to all text indented underneath.

### Inline Footnotes
Inline footnotes are all in one and specified in place like this `^[this is the text of the inline footnote]`

## Headings
Use from 1 - 6 hash marks for heading levels from largest to smallest.
`# Title`
`## Section 1`
`### Subsection`
...
`###### Smallest subdivision`

## Horizontal Bar
Use `***`, `---`, or `___`

## Images
`![alt text](https://url.to/image/goes/here)`
`![[Wikilink to image file]]`

Resize with number indicating pixel width after title:
`![alt text|400](https://url.to/image/goes/here)`

## Links
### External links
`[title](url)`

Escape characters in the url with HTTP escapes or enclose the target in angle brackets:
`[mypage](http://example.com/my%20cool%20page)`
`[mypage](<http://example.com/my cool page>)`

### Internal Links
Wiki-style links: `[[Page title]]`
Alternate title: `[[Page Name|Title to use]]`

## Lists
### Bullets
```Markdown
- Item 1
- Item 2
	- item 2a
	- item 2b
- Item 3
```

### Numbered

Numbering will be "corrected" in preview mode.

```Markdown
1. Item 1
1. Item 2
	1. Item 2a
	1. Item 2b
1. Item 3
```

## Tables
```Markdown
| First Header | Second Header | Third Header |
| ------------ |:-------------:| ------------:|
| first cell   | second cell   | third cell   |
| fourth cell  | fifth cell    | sixth cell   |
```

Colons in the divider are used to indicate justification:
- Column 1 will be left-justified (default)
- Column 2 will be centered
- Column 3 will be right-justified

Escape pipes inside links with backslash.

