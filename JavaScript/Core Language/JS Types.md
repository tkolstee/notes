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

## Boolean
`true` or `false` value.
`false`, `null`, `undefined`, `NaN`, `0`, and empty strings are all falsy. Everything else is truthy.
NB: `0` is falsy but `"0"` is truthy, even though `0 == "0"`.

## Strings
Strings in single and double quotes are equivalent.
```javascript
"String in double quotes"
'String in single quotes'
"This is a \
Multiline String"
```

````ad-info
title: String escape sequences
collapse: true

| Escape Sequence | Literal Characters |
| --------------- | ------------------ |
| `\\`            | `\`                |
| `\"`, `\'`      | `"`, `'`           |
| `\b`            | Backspace          |
| `\f`            | Form Feed          |
| `\n`            | Newline            |
| `\r`            | Carriage Return    |
| `\t`            | Horizontal Tab     |
| `\v`            | Vertical Tab                   |
````

````ad-info
title: String Methods
collapse: true

| Method | Description |
| --- | --- |
| `str.charAt(n)` | Returns character at specific position |
| `str.substring(start, stop)` | Returns characters from pos `start` to pos BEFORE `stop`. Omit `stop` for rest of string. Negative values are changed to `0`. |
| `str.slice(start, stop)` | As with substring, but negative values counted from end. |
| `str.substr(start, len)` | Returns `len` characters starting at position `start` |

`````

## Special Types
- `null`: Used to indicate a deliberate non-value
- `undefined`: Value not currently present

## Arrays
[[JS Arrays]]

## Object
[[JS Objects]]
Dictionaries/Hashes and Objects are the same in JavaScript. Some key/value pairs point at data (properties) whereas others point to functions (methods).

