Install `dotenv` NPM module.

Require:
```javascript
require('dotenv').config();
```

Add `.env` to `.gitignore`

Create `.env` file with name/value pairs like:
```
APP_PORT=3000
DB_HOST=127.0.0.1
DB_NAME=wikiDB
```

Access values via `process.env.KEY_NAME`
