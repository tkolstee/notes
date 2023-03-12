
```javascript
var myObj = { foo: 1, bar: 2, baz: 4 }

myObj.foo         // 1
myObj.baz = 3     // Reassign current attribute 
myObj.quux = 4    // Assign new attribute
myObj[foo]        // Bracket notation works too, "World"

delete myObj.foo  // delete attribute
```

Take over for both "dict" and "object" type in most other languages - key-value pairs where value can be a function (method).

## Instantiating

When you call a function with the `new` keyword, a new object is created, and made available to the function via the `this` keyword. Functions designed to be called like that are called constructors.

```javascript
var MyConstructor = function(){
    this.myNumber = 5;
};
myNewObj = new MyConstructor(); // = {myNumber: 5}
myNewObj.myNumber; // = 5
```

Instead of a 'class' and 'instance', JS combines instantiation and inheritance into a "prototype". These prototypes can be bound, modified, inherited, etc. at runtime after the object is created. Attributes and methods are searched from object to parent to grandparent prototypes.

```javascript
var myObj = {
	myString: "Hello, world!"
};

var myPrototype = {
	meaningOfLife: 42,
	myFunc: function() { return this.myString.toLowerCase(); }
};

myObj.__proto__ = myPrototype;
console.log(myObj.meaningOfLife); // 42

myPrototype.meaningOfLife = 43;
console.log(myObj.meaningOfLife); // 43

myObj.myFunc();  // "Hello, world!"

myPrototype.__proto__ = {
	myBoolean: true
};
console.log(myObj.myBoolean); // true
```


There are two ways to create an object "from" a prototype rather than modifying at runtime.
```javascript
var myObj = Object.create(myPrototype);

// or...

MyConstructor.prototype = {
	myNumber: 5,
	getMyNumber: () => { return this.myNumber; }
}
var myNewObj2 = new MyConstructor();
```


````ad-warning
title: Creating wrapper objects around builtins
```javascript
var myNumber = 12;
var myNumberObj = new Number(12);
myNumber == myNumberObj; // = true

// Except, they aren't exactly equivalent.
typeof myNumber; // = 'number'
typeof myNumberObj; // = 'object'
myNumber === myNumberObj; // = false
if (0){
    // This code won't execute, because 0 is falsy.
}
if (new Number(0)){
   // This code will execute, because wrapped numbers are objects, and objects are always truthy.
}
```
````

````ad-note
title: Modifying the prototypes of builtins

Extending String:
```javascript
String.prototype.firstCharacter = () => this.charAt(0);
console.log("abc".firstCharacter());  // "a"
```
````


## Iterating over Properties and Methods

Iteration can be done with a `for...of` loop or other such method.
`obj.hasOwnProperty(x)` will indicate whether that property belongs to the object or a prototype.



---
# Sources
[Learn javascript in Y Minutes](https://learnxinyminutes.com/docs/javascript/)
