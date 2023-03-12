
## Array Destructuring

```javascript
let a, b, rest;

[a, b] = [10, 20];   // a=10, b=20
[a, b, ...rest] = [10, 20, 30, 40, 50]; // rest=[30,40,50]
```

## Object Destructuring
```javascript
cat = { name: "cat", sound: "meow" }

const { name, sound } = cat
	// Name and Sound are now accessible
	// as constants. name="cat" and sound="meow"

const { name: catName, sound: catSound } = cat
	// catName="cat", catSound="meow"

// Set default values.
// Overridden by cat object, but
// used if attrib doesn't exist.
const {
  name  = "fluffy", // Still "cat"
  sound = "purr",   // Still "meow"
  bed   = "lap"     // New velus: "lap"
} = cat;
```

### Nested Objects
```javascript
cat = {
	name: "cat",
	sound: "meow",
	feedingRequirements: {
		food: 2,
		water: 3,
	}
}


const { 
	name,
	sound,
	feedingRequirements: { food, water }
} = cat;

console.log(water);  // 3
```