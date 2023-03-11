

## `requirements.txt`
```
flask
flask-sqlalchemy
```

## `app.py`
```python
from flask import Flask, render_template, request, redirect
from flask_sqlalchemy import SQLAlchemy
from datetime import datetime

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///test.db'

with app.app_context():
    db = SQLAlchemy(app)

# Create a model for a task object
class Todo(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    content = db.Column(db.String(200), nullable=False)
    date_created = db.Column(db.DateTime, default=datetime.utcnow)

    def __repr__(self):
        return '<Task %r>' % self.id

# Index route create with route decorator
@app.route("/", methods=['POST', 'GET'])
def index():
    if request.method == 'POST':
	    # Form submitted. Take in new task content
        task_content = request.form['content']
        new_task = Todo(content=task_content)
        try:
            db.session.add(new_task)
            db.session.commit()
            # Redirect to invoke GET method.
            return redirect('/')
        except:
            return "There was an error adding your task."
    else:
	    # GET method. Render page.
        tasks = Todo.query.order_by(Todo.date_created).all()
        return render_template('index.html', tasks=tasks)

# URL placeholder for task ID is passed into function
@app.route('/delete/<int:id>')
def delete_task(id):
	# Gets one entry or returns 404.
    task_to_delete = Todo.query.get_or_404(id)
    try:
        db.session.delete(task_to_delete)
        db.session.commit()
        return redirect('/')
    except:
        return "There was an error deleting the task."

# URL placeholder with GET and POST
@app.route('/update/<int:id>', methods=['GET', 'POST'])
def update_task(id):
    if request.method == 'POST':
	    # Form submitted. Update task and redirect to index
        task_to_update = Todo.query.get_or_404(id)
        task_to_update.content = request.form['content']
        # db.session.(task_to_update)
        db.session.commit()
        return redirect('/')
    else:
	    # GET method. render form.
        task_to_update = Todo.query.get_or_404(id)
        return render_template('update.html', task=task_to_update)

if __name__ == "__main__":
    app.run(debug=True)
```

## `templates/base.html`
This form is inherited by other forms that fill out the delimited blocks below
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <link rel="stylesheet" href="{{ url_for('static', filename='css/main.css') }}">
        {% block head %}{% endblock %}
    </head>
    <body>
        {% block body %}{% endblock %}
    </body>
</html>
```

## `templates/index.html`
`extends` keyword says these render within the base form by blocks.
Jinja syntax:
- Python logic embedded in `{%  ...  %}` tags
- Variable values embedded in `{{ }}` tags
```html
{% extends 'base.html' %}

{% block head %}
<title>TaskMaster</title>
{% endblock %}

{% block body %}
<div class="content">
    <h1>Task Master</h1>
    {% if tasks | length < 1 %}
		<h4>No tasks. Create one below!</h4>
	{% else %}
		<table>
	        <tr>
	            <th>Task</th>
	            <th>Added</th>
	            <th>Actions</th>
	        </tr>
	        {% for task in tasks %}
	            <tr>
	                <td>{{task.content}}</td>
	                <td>{{task.date_created.date()}}</td>
	                <td>
	                    <a href="/delete/{{task.id}}">Delete</a>
	                    <a href="/update/{{task.id}}">Update</a>
	                </td>
	            </tr>
	        {% endfor %}
	    </table>
	{% endif %}
    <form action="/" method="POST">
        <input type="text" name="content" id="content">
        <input type="submit" value="Add Task">
    </form>
</div>
{% endblock %}
```

## `update.html`
```html
{% extends 'base.html' %}

{% block head %}
<title>TaskMaster</title>
{% endblock %}

{% block body %}
<div class="content">
    <h1>Task Master</h1>
    <form action="/update/{{task.id}}" method="POST">
        <input type="text" name="content" id="content" value="{{task.content}}">
        <input type="submit" value="Update Task">
    </form>
</div>
{% endblock %}
```

(not depicted: static content in `static/css/main.css`).

To create database, run in REPL:
```python
from app import db
app.app_context().push()
db.create_all()
```

