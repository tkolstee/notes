
`pip install flask_bootstrap`


```python
from flask_bootstrap import Bootstrap

bootstrap = Bootstrap(app)
```


Reference boostrap/base.html in your templates.

```jinja2
{% extends "bootstrap/base.html" %}

{% block title %}My app{% endblock %}
{% block navbar %}
<div class="navbar navbar-inverse" role="navigation">
	...
</div>
{% endblock %}
{% block content %}
<div class="container">
  ....
</div>
{% endblock %}
```


| Block Name     | Description                    |
| -------------- | ------------------------------ |
| `doc`          | Entire HTML doc                |
| `html_attribs` | Attributes inside `<html>` tag |
| `html`         | Contents of `<html>` tag       |
| `head`         | Contents of `<head>` tag       |
| `title`        | Contents of `<title>` tag      |
| `metas`        | List of `<meta>` tags          |
| `styles`       | CSS definitions                |
| `body_attribs` | Attributes inside `<body>` tag |
| `body`         | Contents of `<body>` tag       |
| `navbar`       | User-defined navigation bar    |
| `content`      | User-defined page content      |
| `scripts`      | JS definitions at bottom of page                               |

Many of these tags are used by Flask-Bootstrap, so make sure to call `super()`.

