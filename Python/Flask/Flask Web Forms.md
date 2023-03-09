
Using [Flask-WTF](http://pythonhosted.org/Flask-WTF/), a wrapper around [WTForms](http://wtforms.simplecodes.com/)

`pip install flask-wtf`

Must configure secret key:
```python
app = Flask(__name__)
app.config['SECRET_KEY'] = 'Some secret string'
```

