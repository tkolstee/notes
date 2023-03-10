

```shell
cd projects

virtualenv ./.venv
. ./.venv/bin/activate
pip install django

django-admin startproject mysite .
runserver
```

- :luc_folder_open: `projects`
	- :luc_folder_open: `.venv`
	- :luc_folder_open: `mysite`
		- :luc_file_minus:  `manage.py`
		- :luc_folder_open: `mysite`
			- :luc_file_minus: `__init__.py`
			- :luc_file_minus: `asgi.py`
			- :luc_file_minus: `settings.py`
			- :luc_file_minus: `urls.py`
			- :luc_file_minus: `wsgi.py`

