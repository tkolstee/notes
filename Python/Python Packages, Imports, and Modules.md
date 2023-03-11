
## Modules and Packages
**Modules** are python files that hold functions that can be `import`ed into other python programs.
**Packages** are special types of modules which may contains other modules or packages in a hierarchy.

### Importing and Namespaces
When using `import`, each module is imported into its own namespace.
We can use `from` to import things into the global namespace, and `as` to change the names.

Example: Package `foo` contains functions `bar` and `baz`, and submodule `sub`.
`sub` contains function `quux`

```python
import foo           # module foo; functions foo.bar, foo.baz
import foo.sub       # module foo.sub; functions foo.sub.quux

import foo as x      # module x; functions x.bar, x.baz
import foo.sub as y  # module y; function y.quux

from foo import bar  # function bar
from foo import *    # functions bar, baz
from foo import sub  # module sub, function sub.quux

from foo import sub as xyzzy   # module xyzzy
```

#### Relative Imports
`from ..module_name import name`

Single dot indicates current package, two dots indicates parent package, etc.
Import path can be just two dots.

#### Search Path
When using `import`, Python looks in `sys.path` to find the modules.
`sys.path` is initialized (in part) from the `PYTHONPATH` environment variable.
To add a directory to the search path:
- Add to `PYTHONPATH` before python is invoked, or
- Append to `sys.path` at runtime.

### Implementing Modules

Use a file to define a module. Functions defined within are callable when importing the module.

A file can be both executable and a module. 
To execute code (other than `def`) only when called but not imported, check for `__name__ == "__main__"`
```python
def main:
	print("Running standalone code")

if __name__ == "__main__":
	main()
```

### Implementing Packages
A package is usually a directory with an `__init__.py` file inside. The package name is the same as the directory.

[PEP 420](https://peps.python.org/pep-0420/)made `__init__.py` optional as of Python 3.3, but it is still useful and accepted by convention.
As "The Zen of Python" says: "Explicit is better than implicit".

The init file can be empty, but can also contain functions and definitions that are part of the main package.
The other files in the diretory make up submodules and subdirectories make up subpackages.

````ad-example
title: Package structure
collapse: true

- :luc_folder_minus: `foo`
	- :luc_file: `__init__.py`
		- :luc_function_square: `def bar()`
		- :luc_function_square: `def baz()`
	- :luc_file: `sub.py`
		- :luc_function_square: `def quux()`
````


