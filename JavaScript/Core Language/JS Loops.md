## While
```javascript
while (cond) { ... }
```

## Do...While
```javascript
do { ... } while (!isValid(input)); }
```

## For
```javascript
for (initializer; condition; increment) { ... }
```

## for...in, for...of
**in** Iterates over indices (array) or key names (object)
**of** iterates over values (array).
```javascript
var a = [ "a", "b", "c" ]
for (var x in y) { console.log(x); } // 0, 1, 2
for (var x of y) { console.log(x); } // "a", "b", "c"
```

## Break and Continue
`break` breaks out of most inner loop,
`continue` restarts it from the top.

Breaking out of labeled loops
```javascript
outer:
for (var i = 0; i < 10; i++) {
	for (var j = 0; j < 10; j++) {
		if (i==5 && j==5) {
			break outer;
		}
	}
}
```
