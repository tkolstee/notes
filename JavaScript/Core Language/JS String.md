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

| Method                    | Description                                                                                                                   |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `.charAt(n)`              | Returns character at specific position                                                                                        |
| `.substring(start, stop)` | Returns characters from pos `start` to pos BEFORE `stop`. Omit `stop` for rest of string. Negative values are changed to `0`. |
| `.slice(start, stop)`     | As with substring, but negative values counted from end.                                                                      |
| `.substr(start, len)`     | Returns `len` characters starting at position `start`                                                                         |
| `.length`                 |                                                                                                                               |
| `.replace()`              |                                                                                                                               |
| `.replaceAll()`           |                                                                                                                               |
| `.toUpperCase()`          |                                                                                                                               |
| `.toLowerCase()`          |                                                                                                                               |
| `.concat()`               |                                                                                                                               |
| `.trim()`                 |                                                                                                                               |
| `.trimStart()`            |                                                                                                                               |
| `.trimEnd()`              |                                                                                                                               |
| `.padStart()`             |                                                                                                                               |
| `.padEnd()`               |                                                                                                                               |
| `.charCodeAt()`           |                                                                                                                               |
| `.split()`                          |                                                                                                                               |
````