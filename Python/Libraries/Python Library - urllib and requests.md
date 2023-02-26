
## urllib

```python
from urllib.request import urlopen

w = urlopen(url)
for line in w:
	pass

"""Resource Manager Syntax"""
with urlopen(url) as w:
	for line in w:
		pass
```

## requests
```python
import requests

r = requests.get(url, auth=('user', 'pass'))
```

Attributes of the request object include
`status_code`
`headers['content-type']`
`encoding`
`text`
`json()`

