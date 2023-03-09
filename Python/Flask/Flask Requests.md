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