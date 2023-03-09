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
