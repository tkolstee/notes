A *project* (site) consists of one or more *apps* (features).

## Create project
`django-admin startproject mysite .`

## Create app
`./manage.py startapp myapp`

Edit `mysite/settings.py`, adding `myapp` to `INSTALLED_APPS`.

## Configure Basic App
Create directory `myapp/templates/myapp`

Create `myapp/templates/myapp/index.html`:
```html
<h1>Hello World from myapp</h1>
```

Edit `myapp/views.py:`
```python
def index(request):
	return render(request, 'myapp/index.html')
```

Edit `mysite/urls.py`: 
NB: site/project file, not app/feature file.
```python
from myapp import views as myapp_views

urlpatterns = [
	# ...preexisting pattern here
	path('', myapp_views.index, name='index'),
]
```

## Run Development Server
`python manage.py runserver`

[View App](http://localhost:8000)


## Provide a Human-Readable App Name
`myapp/apps.py`
```python
from django.apps import AppConfig

class MyConfig(AppConfig):
	verbose_name = "My Great App"
```


## Database Settings

`project/settings.py`
```python
""" sqlite default config """
DATABASES = {
	'default': {
		'ENGINE': 'django.db.backends.sqlite3',
		'NAME': os.path.join(BASE_DIR, 'db.sqlite3')
	}
}

""" PostgreSQL config """
DATABASES = {
	'default': {
		'ENGINE': 'django.db.backends.postgresql_psycopg2',
		'NAME': 'mysitedb',
		'USER': 'username',
		'PASSWORD': 'password',
		'HOST': 'localhost',
		'PORT': '',
	}
}
```

`project/urls.py`
