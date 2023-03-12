
## if... else if... else
```javascript
if (cond1) {
	action1
} else if (cond2) {
	action2
} else {
	action3
}
```


## Ternary Operator
```javascript
state = (dbConnected) ? "Connected" : "Offline";
```


## Switch
Allows fall through.
```javascript
switch(species) {
	case 'dog':
	case 'cat':
		console.log('household');
		// fall-through
	case 'chicken':
	case 'cow':
		console.log('domestic');
		break;
	default:
		console.log('wild');
}
```

For ranges, make condition true and put the real condition in the case statements.
```javascript
switch (true) {
	case (age >= 21): return "Can drink and vote"); break;
	case (age >= 18): return ("Can vote, not drink"); break;
	default: return("Cannot drink or vote"); break;
}
```
