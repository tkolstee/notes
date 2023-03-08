
```toc
```

## Dependencies
- Werkzeug - routing, debugging, WSGI Interface
- Jinja2 - Templating
- Click - Command-line integration

## Running Apps
### Development Web Server
```bash
$ export FLASK_APP=hello.py
$ flask run
* Serving Flask app "hello"
* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```
or in code...
```python
if __name__ == '__main__':
	app.run()
```


## Application Instance
```python
from flask import Flask
app = Flask(__name__)
```

The argument is the name of the main module or package; for most applications the `__name__` built-in gives the correct value.

## Routes
Routes are given with a decorator:
```python
@app.route('/')
def index():
	return '<h1>Hello, world!</h1>'
```

...or by using the `app.add_url_rule` function:
```python
def index():
	return '<h1>Hello, world!</h1>'

app.add_url_rule('/', 'index', index)
```

## Route Parameters
Delimited by angle brackets, and passed as named arguments:
```python
@app.route('/user/<name>')
def user(name):
	return f"<h1>Hello, {name}!</h1>"

@app.route('/user/<int:id>')
def user(id):
	user = lookup_user(id)
	return f"<h1>Hello, {user.id}!</h1>"
```

Types `string`, `int`, `float`, and `path` are supported.
`Path` is distinct from `string` in that it can include slashes.



