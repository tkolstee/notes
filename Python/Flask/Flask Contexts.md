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
