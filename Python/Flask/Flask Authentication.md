
## For Web Pages:
[Flask-Login — Flask-Login 0.7.0 documentation](https://flask-login.readthedocs.io/en/latest/.)

```
pip install Flask-Login
```

```python
""" initialization """
from flask_login import LoginManager, login_required, login_user, logout_user, current_user
login_manager = LoginManager()
login_manager.init_app(app)


""" User Model """
from flask_login import UserMixin
class User(UserMixin):
   def __init__(self, id, username, password):
      self.id = id
      self.username = username
      self.password = password

   def get_id(self):
      return self.id

""" Load users, credentials """
users = [User(1, "user1", "password1"), User(2, "user2", "password2")]

""" Implement user loading function """
@login_manager.user_loader
def load_user(user_id):
   for user in users:
      if user.id == user_id:
         return user
   return None

""" Define Login View """
@app.route("/login", methods=["GET", "POST"])
def login():
   if request.method == "POST":
      username = request.form["username"]
      password = request.form["password"]
      for user in users:
         if user.username == username and user.password == password:
            login_user(user)
            return redirect(url_for("index"))
      return "Invalid username or password"

   return """
      <form action="" method="post">
         <input type="text" name="username">
         <input type="password" name="password">
         <input type="submit" value="Login">
      </form>
   """

""" Logout View """
@app.route("/logout")
@login_required
def logout():
   logout_user()
   return redirect(url_for("index"))

""" Protected view with @login_requred decorator"""
@app.route("/")
@login_required
def index():
   return "Welcome, {}!".format(current_user.username)

```

## For API Endpoints

[Flask-JWT — Flask-JWT 0.3.2 documentation](https://flask-jwt.readthedocs.io/en/latest/)

With JWT authentication, the client sends a JWT in the Authorization header with each request. The server verifies the token and extracts the user information from it, allowing it to authenticate the user for each request.

```
pip install Flask-JWT
```

```python
""" init """
from flask_jwt import JWT, jwt_required, current_identity
app.config['SECRET_KEY'] = 'super-secret'
jwt = JWT(app, authenticate, identity)

""" auth function """
def authenticate(username, password):
   user = User.query.filter_by(username=username).first()
   if user and user.password == password:
      return user

""" identity function """
def identity(payload):
   user_id = payload['identity']
   return User.query.filter_by(id=user_id).first()

""" Protect views with @jwt_required """
@app.route('/protected')
@jwt_required()
def protected():
   return '%s' % current_identity.username

```