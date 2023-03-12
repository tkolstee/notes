
## Naming
- Case-sensitive
- Can contain letters, digits, `$`, and `_`
- Cannot start with digit
- Should not start with underscore unless "special"
- Should start with lowercase letter (upper is for object constructors)
- Cannot match a reserved word
- Convention is to use camelCase

## Declaring
- Declared with `var` (function scope) or `let` (block scope)
- Constants declared with `const`
- Bare without `var`, `let`, or `const` is automatically global

`let` is preferred to `var` in most cases.
Can also assign to global scope using `window` object

```javascript
// Numbers - integer or floating-point
const daysInYear = 365;
const pi = 3.1415;

// String
let greeting = "Hello, World!"

// boolean
let isReady = false

window.myGlobalVar = 10;
```
