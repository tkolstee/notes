[Quickstart — Flask Documentation (2.2.x)](https://flask.palletsprojects.com/en/2.2.x/quickstart/)

## Hello World
Run with `flask --app=my_app.py run`

```python
#!/usr/bin/env python3
from flask import Flask
import markupsafe

app = Flask(__name__)

@app.route('/')
def greeting():
	return "<p>Hello, world!</p>"
```


[[Running Flask Apps]]
[[Flask Application Instance]]
[[Flask Routes]]
[[Flask Contexts]]
[[Flask Requests]]
[[Flask Responses]]
[[Flask Templates]]
[[Flask-Bootstrap]]
