## Running Apps
### Development Web Server
```bash
$ export FLASK_APP=hello.py
$ flask run
* Serving Flask app "hello"
* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```
or in code...
```python
if __name__ == '__main__':
	app.run()
```

#### Debug Mode
Debug mode reloads the app on code changes, and displays full stack trace error messages in the browser.
```bash
export FLASK_DEBUG=1
```

```python
app.run(debug=True)
```
