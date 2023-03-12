[Source](https://codingsans.com/blog/node-config-best-practices)
**config.js**
```javascript
const config = {
	app: { port: 3000 },
	db:  {
		host: 'localhost',
		port: 2787,
		name: 'db',
	}
};

module.exports = config;
```

**db.js**
```javascript
const config = require('./config');
// ...
const { db: { host, port, name } } = config;
const connStr = `mongodb://${host}:${port}/${name}`;
```

**app.js**
```javascript
const config = require('./config');
// ...
app.listen(config.app.port);
```