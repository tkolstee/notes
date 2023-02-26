```python
import re
```

| Method                                      | Deescription                                                         |
| ------------------------------------------- | -------------------------------------------------------------------- |
| `re.compile(pattern, flags=0)`              | Compile a re into a reusable object                                  |
| `re.search(patt, str, flags=0)`             | Scan through string looking for first match. Returns object or None. |
| `re.match(patt, str, flags=0)`              | Match from beginning of string. Returns object or None.              |
| `re.fullmatch(patt, str, flags=0)`          | Match only end-to-end. Returns match object or None.                 |
| `re.split(patt, str, maxsplit=0, flags=0)`  | Splits by regex match. Returns list of components.                   |
| `re.sub(patt, repl, str, count=0, flags=0)` | Substitute pattern matches for replacement string                    |

Other methods to document: `findall()`, `finditer()`, `subn`, `escape`, `purge`


---
# Sources
[re — Regular expression operations — Python 3.10.5 documentation](https://docs.python.org/3/library/re.html)