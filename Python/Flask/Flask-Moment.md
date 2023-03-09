Allows server to work in UTC time and have browser present localizations.
`pip install flask-moment`

```python
from flask_moment import Moment

moment = Moment(app)
```

jQuery and Moment should be included in HTML doc

```jinja2
{% block scripts %}
{{ super() }}
{{ moment.include_moment() }}
{% endblock %}
```

```python
@app.route('/')
def index():
	return render_template('index.html', current_time=datetime.utcnow())
```

```jinja2
<p>The local date and time is {{ moment(current_time).format('LLL') }}</p>
<p>That was {{ moment(current_time).fromNow(refresh=True) }}</p>
```

```
The local date and time is July 18, 2017 10:32 AM.
That was a few seconds ago.
```

Implements `format()`, `fromNow()`, `fromTime()`, `calendar()`, `valueOf()` and `unix()` methods from Moment.js

See also [Moment.js Docs](http://momentjs.com/docs/#/displaying/)

