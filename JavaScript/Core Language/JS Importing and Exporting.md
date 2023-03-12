

Variable exported by `default` statement can be imported as any name.
Variable exported by other statements must be named the same.
Name can be transformed when exported or imported using `as`

````ad-example
title: Example: Importing and exporting constants
collapse: true

`exporter.js`
```javascript
const foo = "FOO";
const bar = "BAR";
const baz = "BAZ";
const blah = "QUUX";

export default foo;
export { bar, baz, blah as quux };
```

`client.js`
```javascript
import "./styles.css";

import boop from "./exporter.js";
import { bar, baz, quux as greeble } from "./exporter.js";

// Also valid:
// import boop, { bar, baz, quux } from "./exporter.js";

document.getElementById("app").innerHTML = `
<ul>
  <li>${boop}</li>
  <li>${bar}</li>
  <li>${baz}</li>
  <li>${greeble}</li>
</ul>
`
```

Output:
- FOO
- BAR
- BAZ
- QUUX
````


## Exporting one function

Module Code
```javascript
function ping() { return "PONG!"; }
```
            
Client Code
```javascript
const foo = require(__dirname + '/ping.js');
// ...
console.log(foo())   // "PONG!"
```

## Exporting multiple functions

Module Code
```javascript
function ping() { return "PONG!"; }
module.exports.ping = ping;

// shorter version below
module.exports.marco = function() { return "POLO!"; }
```

Client Code
```javascript
const pinger = require(__dirname + '/ping.js');
console.log(pinger.ping());  // PONG!
console.log(pinger.marco()); // POLO!
```

Shortened form
"exports" is aliased to "module.exports" and is an object too, so:
```javascript
exports = {
	ping:  function() { return "PING!"; },
	marco: function() { return "POLO!"; }
}
```

## Wildcard
```javascript
import * as x from "./exporter.js";

// x will be an object where named exports are keys.
// default export is key "default".
```

## Name
```javascript
export const name = 'value'

import { name } from '...'
```

## Default 
```javascript
export default 'value'

import anyName from '...'
```

## Rename
```javascript
export { name as newName }

import { newName } from '...'
```

## List + Rename
```javascript
export {
	name1,
	name2 as newName2
}

import {
	name1 as newName1,
	newName2
	} from '...'
}
```

