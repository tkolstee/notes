## Named
```javascript
function saveInvoice(record, db) {
	db.write(record);
	return true;
}
saveInvoice(myRecord, myDBConn);
```

## Anonymous
```javascript
var myFunction = function(record, db) { db.write(record); return true; }
var myFunction = (record, db) => { db.write(record); return true; }
```

## Object Methods
```javascript
myObj = { 
	myString: "Hello, world!",
	myFunc: () => { return this.myString; }
}
myObj.myFunc();  // Hello, world!
```

### Specifying context for use with `this`:
```javascript
funcToCall.call( myObj, arg1, arg2, ... )
funcToCall.apply( myObj, [ arg1, arg2 ] )

// Make permanent
var boundFunc = funcToCall.bind(myObj);
boundFunc();

// Prepopulate arguments
var squarefunc = () => Math.pow(this, 2);

var product = function(a, b) { return a*b; }
var doubler = product.bind(this, 2);
```

````ad-example
title: Example: using call
collapse: true
```javascript
var foo = { name: "foo" }
var bar = { 
	name: "bar", 
	myFunc: function () { 
		console.log("Hello from " + this.name);
	}
}

bar.myFunc();          // "Hello from bar"
bar.myFunc.call(foo);  // "Hello from foo"
```
````
