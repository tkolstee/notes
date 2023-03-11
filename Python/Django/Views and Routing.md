
## Views
Edit `appname/views.py` with a function representing the view.
```python
from django.http import HttpResponse

def index(request):
	return HttpResponse("<h1>Hi there</h1>")
```

The function should take a `request` object and return a `HttpResponse` object or throw an Exception (via `abort`).

## Routes
Edit `projectname/urls.py` directly for toplevel routing, or to include app-specific routes.
Edit `appname/urls.py` to create app-specific routes inherited from project:


```python
""" In Project URLs file """
from django.urls import path

urlpatterns = [
	path('', view.index, name='index'),         # Toplevel route
	path('appname/', include('appname.urls')),  # Delegate to app namespace
]


""" In app URLs file """
from django.urls import path
from . import views

urlpatterns = [
	path('', view.index, name='index'),  # app name is removed from delegated URL
]
```

### Path function
`path(route, view, kwargs, name=optional)`
| Parameter | Description                       |
| --------- | --------------------------------- |
| `route`   | URL pattern/prefix to match       |
| `view`    | Function to call to render view   |
| `kwargs`  | Arguments to pass to view as dict |
| `name`    | Symbolic name used to refer to URL/route from elsewhere                                  |

