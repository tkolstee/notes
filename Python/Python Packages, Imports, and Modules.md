**Modules** are python files that hold functions that can be `import`ed into other python programs.
**Packages** are special types of modules which may contains other modules or packages in a hierarchy.

```toc
```
## Installing Packages

```r
pip install packagename
```

### Upgrading Packages

```r
pip list --outdated
pip list --outdated --pre    # List prerelease or release candidates

pip install -U packagename
```

### Requirements File
```R
# Record packages in environment
$ pip freeze > requirements.txt

# Install packages from exported file
$ pip install -r requirements.txt
```

## Importing and Namespaces
When using `import`, each module is imported into its own namespace.
We can use `from` to import things into the global namespace, and `as` to change the names.

````ad-example
title: Examples of `import`
collapse: true
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
````

### Relative Imports
`from ..module_name import name`

Single dot indicates current package, two dots indicates parent package, etc.
Import path can be just two dots.

### Search Path
When using `import`, Python looks in `sys.path` to find the modules.
`sys.path` is initialized (in part) from the `PYTHONPATH` environment variable.
To add a directory to the search path:
- Add to `PYTHONPATH` before python is invoked, or
- Append to `sys.path` at runtime.

## Implementing Modules

Use a file to define a module. Functions defined within are callable when importing the module.

A file can be both executable and a module. 
To execute code (other than `def`) only when called but not imported, check for `__name__ == "__main__"`
```python
def main:
	print("Running standalone code")

if __name__ == "__main__":
	main()
```

## Implementing Packages
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

## Special Variables
`__name__`: The original filename of the file or module being run, or `__main__` if this file repsresents the main program.
`__path__`: The path of a package. Not present in "regular" modules
`__file__`: The file of the module or package.
`__all__`: Controls `from...import` behavior. List everything `*` should import.

## Namespace Packages
Package split across multiple directories with no `__init__.py`
Defined in [PEP420](https://python.org/dev/peps/pep-0420/)
No package-level initialization code. Avoids complex questions of init order.

Namespace Package Discovery Algorithm
- Scan each dir in `sys.path`
- Import standard package if found
- Import standard module if found
- Otherwise, all matching dirs contribute to a namespace package.

````ad-example
title: Example Namespace Package Layout
collapse: false

- :luc_folder_minus: `path1`
	- :far_folder: `demo_reader`
		- :luc_folder_open: `util`
			- :luc_file: `__init__.py`
			- :luc_file: `writer.py`
		- :luc_file: `multireader.py`
- :luc_folder_open: `path2`
	- :far_folder: `demo_reader`
		- :luc_folder_open: `compressed`
			- :luc_file: `__init__.py`
			- :luc_file: `bzipped.py`
			- :luc_file: `gzipped.py`

```python
import sys
sys.path.extend(['./path1', './path2'])

import demo_reader
print(demo_reader.__path__)
# _NamespacePath(['./path1/demo_reader', './path2/demo_reader'])

import demo_reader.util
print(demo_reader.util.__path__)       # ['./path1/demo_reader/util']

import demo_reader.compressed
print(demo_reader.compressed.__path__) # ['./path2/demo_reader/compressed']
```
````

## Distribution Packages

- :luc_folder_open: `project_name`
	- :luc_file: `README.rst `  # documentation (ReStructuredText format)
	- :luc_folder_open: `docs`                # many forms (e.g. Sphinx)
	- :luc_folder_open: `src`                   # not directly importable 
		- :luc_folder_open: `package_name`
			- :luc_file: `__init__.py`
			- :luc_file: `more_source.py`
			- :luc_folder_open: `subpackage1`
				- :luc_file: `__init__.py`
	- :luc_folder_open: `tests`
		- :luc_file: `test_code.py`
	- :luc_file: `setup.py`

## Source Package
- Contains everything needed to build the package
- Cannot be placed directly into installation dir, must be built

To build source packages that use `setuptools`:
```
import setuptools
setuptools.setup(
	name="demo_reader",
	version="1.0.0",
	description="Tools for reading various file formats",
	packages=setuptools.find_packages('src'),
	package_dir={'': 'src'}
)
```
`python setup.py sdist`

Writes `dist` dir with a `tar.gz` file - installable with `pip`

## Built Package
- placed directly into installation directory
- build results are included in the package
- can be platform-specific
- Use the *wheel* format defined in PEP 427

`pip install wheel`
`python setup.py bdist_wheel`

Writes file in `dist/` with `.whl` extension
can install with `pip`
name like `packagename-version-py3-none-any.whl`
- py3 = python version
- none = ABI requirements (if binary constraints)
- any = Platform requirements (oses)

## Uploading Packages to PyPi

Register for account at [PyPi](https://pypi.org)
`python -m pip install --user --upgrade twine`
`$ twine upload dist/demo_reader-1.0.0-py3-none-any.whl`

Use PyPi user/pass
People can now install package using pip from remote


## Plugins

### With Namespace Packages
Core package designates subpackages as extension points
Core package scans subpackages at runtime to discover plugins
Devs can augment the namespace package's extension subpackages

```
demo_reader/
	compressed/
	util/
		__init__.py
		writer.py
	__main__.py
	multireader.py
```

Note `compressed` subdir is empty.
In multireader.py we can define:
```python
import importlib
import os
import pkgutil
import demo_reader.compressed

def iter_namespace(ns_pkg):
  return pkgutil.iter_modules(
	  ns_pkg.__path__,
	  ns_pkg.__name__ + "."
  )

compression_plugins = {
  importlib.import_module(module_name)
  for _, module_name, _ in iter_namespace(demo_reader.compressed)
}

extension_map = {
  module.extension: module.opener
  for module in compression_plugins
}
```

`pkgutil.iter_modules` knows how to find all sub packages.
First argument is where to find subpackages
Second argument is a prefix that it returns before package names.

Set comprehension builds `compression_plugins` set
Build `extension_map` dict with module-level attributes from `compression_plugins`.

`compressed/bzipped.py`
```python
import bz2
from ..util import writer
extension = '.bz2'
opener = bz2.open

if __name__ == '__main__':
  writer.main(opener)
```

`compressed/gzipped.py`
```python
import gzip
from ..util import writer
extension = '.gz'
opener = gzip.open

if __name__ == '__main__':
  writer.main(opener)
```


### With setuptools
Define extension points using `setuptools`
Plugins add to extension points in `setup.py`
Core package iterates over plugins added to extension points

```
demo_reader/
	src/
		demo_reader/
			util/
				__init__.py
				writer.py
			__init__.py       - empty
			__main__.py
			multireader.py
	tests/
		test_multireader.py
	README.rst
	setup.py
```

`multireader.py`
```python
import os
import pkg_resources

# ...

compression_plugins = {
	entry_point.load()
	for entry_point
	in pkg_resources.iter_entry_points('demo_reader.compression_plugins')
}

# Maps file exts to corresponding open methods
extension_map = {
	module.extension: module.opener
	for module in compression_plugins
}
```

`src/demo_reader_bz2/bzipped.py`
```python
import bz2
from demo_reader.util import writer
extension = '.bz2'
opener = bz2.open

if __name__ == '__main__':
  writer.main(bz2.open)
```

`setup.py`
```python
import setuptools

setuptools.setup(
	name="demo_reader_bz2_plugin",
	version="0.0.0",
	description="demo_reader plugin for reading bz2 files",
	packages=setuptools.find_packages ('src'),
	package_dir={'':: 'src'},
	entry_points={
		'demo_reader.compression_plugins': [
			'bz2 = demo_reader_bz2.bzipped'
		]
	}
)
```

`entry_points` defines entry point name (key) and extension name and object (value separated with =)

