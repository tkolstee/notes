
## Using sys.argv

`sys.argv` contains the tokenized command line arguments. `argv[0]` is the command itself.

```python
import sys

progname = sys.argv[0]

if len(sys.argv) != 2:
	print(f"{progname}: Must supply exactly one command line argument!")
else:
	print(f"You specified {sys.argv[1]}")
```

## Using getopt

See [getopt — C-style parser for command line options — Python 3.11.0 documentation](https://docs.python.org/3/library/getopt.html)


