
```python
import base64

base64.b64encode(bytes_obj, altchars=None)

orig = base64.b64decode(base64_str, validate=False)
```

Converts to/from base64. 
Plaintext should be in a `bytes` object.
