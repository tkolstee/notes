Bcrypt takes passwords through multiple rounds of salting.
It can be finicky with particular versions of node and OS libraries.
Most effective when used with database encryption as well (e.g. [[BEFORE/Information/Programming/JavaScript/JavaScript Libraries and Modules/Mongoose#Encryption|Mongoose Encryption Plugin]]).

Require:
```javascript
const bcrypt = require('bcrypt');
```

Encrypt password when storing:
```javascript
const saltRounds = 10;
bcrypt.hash(password, saltRounds, (err, hash) => {
	// store hash in DB here
});
```

Compare when user enters password:
```javascript
bcrypt.compare(plaintextEnteredPassword, hashedRetrievedPassword, function(err, result) {
	// err is set if an error occurs
	// result is true if passwords are same, false if not.
});
```

