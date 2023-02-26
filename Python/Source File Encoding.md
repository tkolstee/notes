## Default
Per [PEP 3120](https://peps.python.org/pep-3120/), the default encoding for Python files is UTF-8.

## Declarations

[PEP 263](https://peps.python.org/pep-0263/) defines encoding declarations that can be used with alternate encodings.

Common Examples:
```python
# coding=<encoding name>

or...

#!/usr/bin/python
# -*- coding: <encoding name> -*-

or...

#!/usr/bin/python
# vim: set fileencoding=<encoding name> :
```

More precisely, the first or second line must match the regex:
```regex
^[ \t\f]*#.*?coding[:=][ \t]*([-_.a-zA-Z0-9]+)
```

The first group is then used as the encoding name.

UTF-8 can also be specified by starting the file with the UTF-8 byte-order mark `b'\xef\xbb\xbf`
