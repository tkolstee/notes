
```javascript
var myObj = { foo: 1, bar: 2, baz: 4 }

myObj.foo         // 1
myObj.baz = 3     // Reassign current attribute 
myObj.quux = 4    // Assign new attribute
myObj[foo]        // Bracket notation works too, "World"

delete myObj.foo  // delete attribute
```

Take over for both "dict" and "object" type in most other languages - key-value pairs where value can be a function (method).


## Object Methods
```javascript
var user = { 
	fname: 'Joe', 
	lname: 'Jones',
	fullname: function() {
		return this.fname + " " + this.lname
	}
}
```

