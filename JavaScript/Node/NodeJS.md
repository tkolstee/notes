Server-side Javascript CLI interpreter
Enter REPL by running `node` alone on command line


Simple listener (using express as well)
`server.js`
```javascript
// Import express function and create express application
const express = require('express');
const app = express();

// Start a server
app.listen(3000, function {
  console.log("App listening on port 3000")
})
```

Start with `node `:
`node ./server.js`

## Adding Static Content
```javascript
app.use('/', express.static(__dirname + '/public/'))
```

## Adding Middleware
```javascript
const bodyParser = require('body-parser')
app.use(bodyParser.json())
```
body-parser parses the body so we can get the POST vars, e.g.

## Routing

### GET/POST
`app.get(route, callback)` or 
`app.post(route, callback)`

```javascript
app.get( '/about', (req, res) => { 
	res.send("About me...");
} );


app.post('/save-task', function(req, res) {
	const taskObj = req.body
	// do stuff
	res.send({ savedTask: taskObj.task })
})
```
            
### URL Parameters
```javascript
app.get('/posts/:postId', (req, res) => {
	// req.params.postId contains value in postID param
});
```

### Redirection
```javascript
(req, res) => {
	res.redirect('/');
}
```


## Filesystem Access
```javascript
const fs = require('fs');

// copy files
fs.copyFileSync('./file1.txt', './file2.txt');
```


----
# See Also
[API Docs](https://nodejs.org/api/)
