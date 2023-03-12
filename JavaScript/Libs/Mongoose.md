NPM module for connecting with MongoDB from NodeJS

## Installation
	- `npm install mongoose`

## Usage
### Importing
```javascript
const mongoose = require('mongoose');   // NodeJS
import mongoose from 'mongoose';        // ES6
		  
mongoose.set('strictQuery', false);
```

## Connecting
```javascript
const mongoose = require('mongoose');

mongoose.set('strictQuery', false);
mongoose.connect('mongodb://localhost:27017/fruitsDB');

// ...
mongoose.connection.close();
```

## Defining Schemas and Models
Schema names and models should be singular. Mongoose will create a collection using the plural of the name (e.g. "People").
```javascript
// define schema (use singular)
const fruitSchema = new mongoose.Schema({
    name: String,
    rating: {
	    type: Number,
	    min: [0, 'Rating should be 0-10'],
	    max: [10, 'Rating should be 0-10'],
	    required: [true, 'need a rating here']
    },
    review: String
});

// define model (singular, uppercase)
const Fruit = mongoose.model("Fruit", fruitSchema);
```


## Creating Objects and Writing to DB
### Single Objects
```javascript
// Create new object based upon model
const fruit = new Fruit({
    name: "Apple",
    rating: 7,
    review: "Pretty solid as a fruit."
});
// Write new object to db
fruit.save()
```

### Multiple
```javascript
const kiwi = new Fruit({
	name: "Kiwi",
	score: 10, 
	review: "The best fruit!"
});

const orange = new Fruit({
	name: "Orange",
	score: 4,
	review: "Too sour for me"
});

const banana = new Fruit({ 
	name: "Banana", 
	score: 3, 
	review: "Weird texture"
});

Fruit.insertMany([ kiwi, orange, banana ], (err) => {
	// callback function
	// if error occurs, err will contain a message
	// otherwise, can be used to log/handle success.
});
```

### Schema relationships
```javascript
const personSchema = new mongoose.Schema({
	name: String,
	age: Number,
	favoriteFruit: fruitSchema
});
const Person = mongoose.model("Person", personSchema);

const pineapple = new Fruit({
	name: "Pineapple",
	rating: 8,
	review: "mmm..."
})
const person = new Person({
	name: "Amy",
	age: 12,
	favoriteFruit: pineapple // references a Fruit
});
```


## Reading from DB

```javascript
Fruit.find(function(err, fruits) {
	// if an error occurs, err will contain an error message.
	// if no error, fruits will be an array of objects.
}
```

## Updating Existing Records
```javascript
Fruit.updateOne(
    { name: 'Banana' },  // query
    { name: 'Banana (not the stupid minion meme!)' }, // change
    {}, // options
    (err, res) => { console.log(err); console.log(res); } // callback
);
```

## Encryption
Encrypts field contents with SHA
`npm install mongoose-encryption`

```javascript
const encrypt = require("mongoose-encryption");
// ....

// Define schema

userSchema.plugin(encrypt, {
    secret: secret,
    encryptedFields: ['password']
});

// Define model
```


---
# See Also
[NPM Page](https://www.npmjs.com/package/mongoose)
[Docs](http://mongoosejs.com/)