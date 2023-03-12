

`npm` module that renders templates with embedded JavaScript to text.

## Installation
```shell
npm install ejs
```

## Using with ExpressJS
```javascript
const ejs = require('ejs')
// ...
app.set('view engine', 'ejs');
// ...
app.get('/', function(req, res) {
	res.render('list', { day: day, tasks: tasks });
}
```

Will look for files under `views` folder, e.g. `views/list.ejs` in the example above.

## Templates

## Syntax

### Template Tags
| Tag            | Purpose                                    |
	| -------------- | ------------------------------------------ |
	| `<%` ... `%>`  | Execute line of JS code                    |
	| `<%_` ... `%>` | Execute JS, strip whitespace before tag    |
	| `<%=` ... `%>` | Interpolate escaped value of expression    |
	| `<%-` ... `%>` | Interpolate unescaped value of expression  |
	| `<%#` ... `%>` | Comment                                    |
	| `<%%` or `%%>` | Literal `<%` or `%>`                       |
	| `-%>`          | Ending tag that trims following newline    |
	| `_%>`          | Ending tag that trims whitespace after tag |



## Example
```ejs
<!-- Print a list item for each item in the array -->
<ul>
	<% for (item of listitems) { %>
		<li><%= item %>
	<% } %>
</ul>
```

## Includes
`<%- include('user/show', {user: user}) %>`

Include a layout header and footer with `include`:

```EJS
<%- include('header'); -%>

<h1>page title</h1>
<p>page content</p>

<%- include('footer'); -%>
```

Included template will get variables from parent file.
