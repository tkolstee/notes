
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

#### Debug Mode
Debug mode reloads the app on code changes, and displays full stack trace error messages in the browser.
```bash
export FLASK_DEBUG=1
```

```python
app.run(debug=True)
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

`app.url_map` contains Rule objects to map URLs to routes


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

## Contexts
Flask `push`es or `pop`s contexts in the appropriate circumstance

| Variable      | Context     | Description                                   |
| ------------- | ----------- | --------------------------------------------- |
| `current_app` | Application | Application instance for current app          |
| `g`           | Application | Temporary storage, reset with each request    |
| `request`     | Request     | Client's HTTP request                         |
| `session`     | Request     | Persistent dict for each req from same client |

### Pushing and Popping Contexts

```python
from hello import app
from flask import current_app

app_ctx = app.app_context()
app_ctx.push()

print(current_app.name)
"""hello"""

app_ctx.pop()
```

## Requests

### Request Data
Part of the `request` context:
```python
from flask import request

@app.route('/')
def index():
	user_agent = request.headers.get('User-Agent')
	return f"<p>You are using {user_agent}</p>"
```

```ad-note
title: Request object attributes and methods
collapse: true
| Attribute / Method | Description                               |
| ------------------ | ----------------------------------------- |
| `form`             | Dict of form fields submitted             |
| `args`             | Arguments in the query string             |
| `values`           | Combines `form` and `args`                |
| `cookies`          | Cookies included in request               |
| `headers`          | Dict with all HTTP headers                |
| `files`            | File uploads in request                   |
| `get_data()`       | Returns buffered data from request body   |
| `get_json()`       | Returns request body parsed as JSON       |
| `blueprint`        | Flask blueprint handling the request      |
| `endpoint`         | Flask endpoint handling the request       |
| `method`           | HTTP request method (GET, POST, e.g.)     |
| `scheme`           | URL scheme (http, https, e.g.)            |
| `is_secure()`      | True if using secure (https) connection   |
| `host`             | Host and port # if given                  |
| `path`             | Path portion of URL                       |
| `query_string`     | Query string portion of URL as raw binary |
| `full_path`        | Path and query string portions of URL     |
| `url`              | Complete URL                              |
| `base_url`         | URL without query string                  |
| `remote_addr`      | IP address of client                      |
| `environ`          | Raw WSGI env dict for the request         |
```

### Request Hooks
| Function Decorator      | Purpose                                                |
| ----------------------- | ------------------------------------------------------ |
| `@before_request`       | Runs before each request                               |
| `@before_first_request` | Runs before first request (server init)                |
| `@after_request`        | Runs after request if no unhandled exceptions occurred |
| `@teardown_request`     | Runs after request whether or not exception thrown.                                                       |

It's common to use `g` for storage. `before_request` might load the user from the db and store it in `g.user`, and the view function might later retrieve it from there.

## Responses
Returns containing a string are sent back to the client as-is.
Add a status code if needed:
```python
""" Response containing HTML """
return "<p>Hello!</p>"

""" Response with status code """
return "<p>Not found.</p>", 404

""" Status code and headers """
return "<p>Redirecting to home</p>", 302, { 'Location': '/' }

""" Complex response object """
response = make_response('<h1>Have a cookie!</h1>')
response.set_cookie('userid', '12')
return response

""" Redirect """
return redirect('http://www.example.org/foo.html')

""" Abort - exits function """
if not user:
	abort(404)
```

```ad-note
title: Response Object: Attributes and Methods
collapse: true
| Attribute or Method | Description                              |
| ------------------- | ---------------------------------------- |
| `status_code`       | Numeric HTTP status code                 |
| `headers`           | Dict-like object with headers to be sent |
| `set_cookie()`      | Adds a cookie to the response            |
| `delete_cookie()`   | Removes a cookie                         |
| `content_length`    | Length of the response body              |
| `content_type`      | MIME type of response                    |
| `set_data()`        | Set response body as string or bytes     |
| `get_data()`        | Gets the response body                   |
```

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
