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

#### Blocks
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

