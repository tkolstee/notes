### Templates
```python
from flask import Flask, render_template

@app.route('/')
def index():
	return render_template('index.html')

@app.route('/user/<name>')
def user(name):
	return render_template('user.html', name=name)
```

`user.html`
```jinja2
<html>
	<head><title>User Page</title></head>
	<body>
		<h1>Hello, {{ name | capitalize }}!</h1>
	</body>
</html>
```

```ad-note
title: Jinja2 filters
collapse: true
| Filter | Description |
| ----- | ----- |
| `safe` | Renders without applying escaping |
| `capitalize` | Coverts first character to upper, rest to lower |
| `lower` | Converts to lowercase | 
| `upper` | Converts to uppercase |
| `title` | Capitalize each word |
| `trim` | Removes leading/trailing whitespace |
| `striptags` | Removes any HTML tags from the value |
```


`render_template` uses templates from project root or app's `templates` directory.

They are referenced by name and path, so an app-specific directory should be uner `templates` to provide a unique namespace: `/projectroot/app/templates/app/mytemplate.html` can be accessed from anywhere with `render_template('app/mytemplate.html')`.

#### Jinja2 Constructs
```jinja2
<!-- For Loop -->
{% for x in y %}
	....
{% endfor %}

<!-- if/then/else -->
{% if condition %}
	...
{% else %}
	...
{% endif %}

<!-- Import -->
{% import 'macros.html' as macros %}

<!-- Macros -->
{{ macros.render_comment(comment) }}

<!-- Include -->
{% include 'common.html' %}
```

Available within template by default:
- `config`, `request`, `session`, and `g` objects
- `url_for()`, `get_flashed_messages()` methods
- Automatic escaping of vars is enabled. 
	- If it's known to be safe, use `markupsafe.Markup` or `|safe` filter in templates.

#### Blocks
This allows for template inheritance. For example you might create an app called `base` that contains your base (branded) templates, and then use them to wrap context-specific templates.

`base.html`
```jinja2
<html>
	<head>
		{% block head %}
		<title>{% block title %}{% endblock %} - myapp</title>
		{% endblock %}
	</head>
	<body>
		{% block body %}
		{% endblock %}
	</body>
</html>
```

```jinja2
{% extends "base.html" %}
{% block title %}Index{% endblock %}
{% block head %}
  {{ super() }}
  <style></style>
{% endblock %}
{% block body %}
<h1>Hello, world!</h1>
{% endblock %}
```


