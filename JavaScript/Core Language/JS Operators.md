## Operators
| Type                       | Operator             | Meaning                                                     |
| -------------------------- | -------------------- | ----------------------------------------------------------- |
| Arithmetic                 | `+`, `-`, `*`, `/`   | Arithmetic. Division will produce fractional results.       |
| Modulo                     | `%`                  | Remainder / Modulo Division                                 |
| Bitwise                    | `<<`, `>>`           | Bit shift. Floats converted to signed int **up to** 32 bits |
| Unary Negation             | `!`                  | Negates Boolean value                                       |
| Value                      | `==`, `!=`           | Compares for equal/not equal. First converts to same type.  |
|                            | `>`, `<`, `>=`, `<=` | Compares for inequality. First converts to same type        |
| Identity                   | `===`, `!==`         | Compares for identity - values AND types equal              |
| Unary increment, decrement | `++`, `--`           |                                                             |
| Compound assignment        | `+= -= *= /=`        |                                                             |
| Logical AND, OR            | `&&`, $\vert\vert$   | Short circuit left-to-right and return "significant" value. |
|                            |                      |                                                             |
 
`=` assignment
Comparison with type conversion: `==`, `!=`
Comparison of value AND type: `===`, `!==`
