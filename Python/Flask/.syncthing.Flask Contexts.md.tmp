
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

### Persistence

[Define and Access the Database — Flask Documentation (2.2.x)](https://flask.palletsprojects.com/en/2.2.x/tutorial/database/)
```python
import sqlite3

import click
from flask import current_app, g

def get_db():
    if 'db' not in g:
        g.db = sqlite3.connect(
            current_app.config['DATABASE'],
            detect_types=sqlite3.PARSE_DECLTYPES
        )
        g.db.row_factory = sqlite3.Row

    return g.db

def close_db(e=None):
    db = g.pop('db', None)

    if db is not None:
        db.close()
```

[`g`](https://flask.palletsprojects.com/en/2.2.x/api/#flask.g "flask.g") is a special object that is unique for each request. It is used to store data that might be accessed by multiple functions during the request. The connection is stored and reused instead of creating a new connection if `get_db` is called a second time in the same request.

[`current_app`](https://flask.palletsprojects.com/en/2.2.x/api/#flask.current_app "flask.current_app") is another special object that points to the Flask application handling the request. Since you used an application factory, there is no application object when writing the rest of your code. `get_db` will be called when the application has been created and is handling a request, so [`current_app`](https://flask.palletsprojects.com/en/2.2.x/api/#flask.current_app "flask.current_app") can be used.

[`sqlite3.connect()`](https://docs.python.org/3/library/sqlite3.html#sqlite3.connect "(in Python v3.11)") establishes a connection to the file pointed at by the `DATABASE` configuration key. This file doesn’t have to exist yet, and won’t until you initialize the database later.

[`sqlite3.Row`](https://docs.python.org/3/library/sqlite3.html#sqlite3.Row "(in Python v3.11)") tells the connection to return rows that behave like dicts. This allows accessing the columns by name.

`close_db` checks if a connection was created by checking if `g.db` was set. If the connection exists, it is closed. Further down you will tell your application about the `close_db` function in the application factory so that it is called after each request.
