## Number
One type for integer and floating-point.
```javascript
5;
7.6;
```

````ad-info
title: Special Values: NaN and Infinity
collapse: true
`NaN`: "Not a Number"  ([MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN))
- Produced from `0/0`, failed `parseInt()`, `Math.sqrt(-1)`, etc.
- Propagates through most mathematical operations
- Always false in comparisons - even compared to itself
- Detect with `isNaN(x)` (will coerce) or `Number.isNaN(x)` (if already `NaN`)

`Infinity` and `-Infinity` ([MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity))
- Equivalent to `Number.POSITIVE_INFINITY` and `Number.NEGATIVE_INFINITY`
````
