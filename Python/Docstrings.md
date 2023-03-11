Formatted comments that provide inline documentation.

```toc
```

## Specification
The formatting is specified in [PEP 257](https://peps.python.org/pep-0257/)

## Accessing from Python
These are accessible in the REPL using `help(classname)` or `help(classname.methodname)`.

Objects' docstrings are available via the `__doc__` attribute.

Use `inspect.getdoc(obj)` or `inspect.cleandoc(obj)` to get clean versions of the docs.

## Generating Documentation
The [Sphinx](https://www.sphinx-doc.org/en/master/) tool will create HTML documentation from Python docstrings.

## Example
```python
"""
Retrieve and print words from a URL.
Usage:
	python3 words.py URL
"""

def fetch_words(url):
    """Fetch a list of words from a URL.

		Args:
			url: The URL of a UTF-8 text document.

		Returns:
			A list of strings containing the words from
			the document.
	"""
    pass
```

