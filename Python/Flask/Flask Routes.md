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

`app.url_map` contains Rule objects to map URLs to routes


### Route Parameters
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

## Error Handlers
```python
@app.errhandler(494)
def page_not_found(e):
	return render_template('404.html'), 404
```

## Reverse Mapping
Use function name (endpoint name for routes added with `app.add_url_route()`):

```python
url_for('index')                # = '/'
url_for('index', external=True) # http://localhost:5000/
url_for('user', name='john')    # /user/john
```

## Static Files
```python
url_for('static', filename='css/styles.css')
```