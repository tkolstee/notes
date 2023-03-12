
Mixed types okay, extending okay
```javascript
var myArray = ["Hello", 45, true];
myArray[1];  // = 45
myArray[1] = 42;
```

## Methods

| Method              | Purpose |
| ------------------- | ------- |
| `.toString()`       | Convert to string        |
| `.join(separator)`  | Join elements to string        |
| `.pop()`            | remove and return last element         |
| `.push(element)`    | add element to end        |
| `.shift()`          | Remove and return first element        |
| `.unshift(element)` | Add as first element        |
| `.length`           | Number of elements        |
|`.slice(start, stop)`|Range in array from `start` to BEFORE `stop`|
|`.splice(pos, len, val1, ...)`|Remove `len` elements starting from index `pos`. Insert values there and return removed elements|
| Object.keys(arr)    |         |
| Object.values(arr)  |         |
| Object.entries(arr) |         |

```javascript
//Map -Create a new array by doing something with each item in an array.
arr.map( (x) => {} )  

//Filter - Create a new array by keeping the items that return true.
arr.filter( (x) => {} )

//Reduce - Accumulate a value by doing something to each item in an array.
arr.reduce( (x, y) => {} )

//Find - find the first item that matches from an array.
arr.find( (x) => {} )

//FindIndex - find the index of the first item that matches.
arr.findIndex( (x) => {} )
```


![[JS Array Methods Cheat Sheet.png]]