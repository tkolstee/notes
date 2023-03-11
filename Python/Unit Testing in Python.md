
```toc
```
## Using unittest
### Test File Framework
```python
import unittest
from myfile import MyClass

# Tests can be grouped by class
class test_construct_object(unittest.TestCase):

	# Setup, run before each test
	def setUp(self):
		self.x = MyClass('foo', 'bar')

	# Individual Unit Test
	def test_construct_empty
		x = MyClass()

if __name__ == "__main__":
	unittest.main()
```

### Running Tests from CLI:
`python test_my_stuff.py` (or use IDE)

### setUp and tearDown:
A method called setUp within a unittest.TestCase class will be run automatically before each test. This can assign to instance methods so that other tests can access the objects initialized:
```python
class test_basic(unittest.TestCase):

	def setUp(self):
		self.o = MyObject('a', 'b', 'c')	
```

The tearDown() method can be used to clean up after tests are run as well, and will be run regardless of the status of the test.

`setUpClass()` and `tearDownClass()` run once per class.

### Tests
Tests are implemented as methods within the class.
```python
class test_basic(unittest.TestCase):

	def test_object_creation(self):
		self.o = MyObject('a', 'b', 'c')
```

Without assertions, the code will execute and pass the test unless an exception is raised, in which case it will fail.

#### Assertions
Within the unittest.TestCase class there are a number of functions that support test assertions:
|Assertion|Tests that|
|---|:---:|
|assertEqual(a, b)|`a == b`|
|assertNotEqual(a, b)|`a != b`
|assertTrue(x)|`bool(x) is True`|
|assertFalse(x)|`bool(x) is False`|
|assertIs(a, b)|`a is b`|
|assertIsNot(a, b)|`a is not b`|
|assertIsNone(x)|`x is None`|
|assertIsNotNone(x)|`x is not None`|
|assertIn(a, b)|`a in b`|
|assertNotIn(a, b)|`a not in b`|
|assertIsInstance(a, b)|`isinstance(a, b)`|
|assertNotIsInstance(a, b)|`not isinstance(a, b)`|
|assertRaises(exc, fun, \*args, \*\*kwargs)|`fun(*args, **kwargs)` raises exc|
|assertRaisesRegex(exc, r, fun, \*args, \*\*kwargs)|`fun(*args, **kwargs)` raises exc and the message matches regex r|
|assertWarns(warn, fun, \*args, \*\*kwargs)|`fun(*args, **kwargs)` raises warn|
|assertWarnsRegex(warn, r, fun, \*args, \*\*kwargs)|`fun(*args, **kwargs)` raises warn and the message matches regex r|
|assertLogs(logger, level)|The `with` block logs on `logger` with minimum `level`|
|assertNoLogs(logger, level)|The `with` block does not log on `logger` with minimum `level`
|assertAlmostEqual(a, b)|`round(a-b, 7) == 0`|
|assertNotAlmostEqual(a, b)|`round(a-b, 7) != 0`|
|assertGreater(a, b)|`a > b`|
|assertGreaterEquals(a, b)|`a >= b`|
|assertLess(a, b)|`a < b`|
|assertLessEqual(a, b)|`a <= b`|
|assertRegex(s, r)|`r.search(s)`|
|assertNotRegex(s, r)|`not r.search(s)`|
|assertCountEqual(a, b)|*a* and *b* have the same elements in the same number, regardless of order|
|assertMultiLineEqual(a, b)|Multiline strings a and b are equal, or display a diff|
|assertSequenceEqual(a, b)|Both sequences are equal|
|assertListEqual(a, b)|Both lists are equal|
|assertTupleEqual(a, b)|Both tuples are equal|
|assertSetEqual(a, b)|Both sets or frozensets are equal|
|assertDictEqual(a, b)|Both dicts are equal|

### Skipping Tests
#### Decorators
`@unittest.skip("demonstrating skipping")` will skip a test (or class of tests)
`@unittest.skipIf(condition, string)` will skip if condition is true.
`@unittest.skipUnless(condition, string)` will skip if condition is false.
`@unittest.expectedFailure` will mark the test as expecting to fail, reversing the success/fail status.

#### Within Test Bodies
call `self.skipTest(string)` or raise `unittest.SkipTest(string)`

## Using pytest
Create a file whose name matches `test_*.py`, and define functions also named starting with `test_`. Running `pytest` at the command line should autodiscover these files and run the tests.

```python
def inc(x):
	return x + 1

def test_inc():
	assert inc(3) == 5
```

Test raising an error
```python

def test_filenotfound():
	with pytest.raises(FileNotFoundError):
		open_data_file('/nonexistent')
```

Get a temporary directory for testing:
```python
def test_writefile(tmp_path):
	outfile = os.path.join(tmp_path, 'myfile.txt')
	with open(outfile, 'w') as out:
		pass
```

Fixtures:
Built in fixtures are documented [here](https://docs.pytest.org/en/7.2.x/reference/fixtures.html#fixtures)
```python
def db_connection():
	return connect_to_db('localhost', '3389')

def test_db_transation(db_connection):
	db_connection.run_transaction()
```

----

# See Also
[unittest — Unit testing framework — Python 3.11.0 documentation](https://docs.python.org/3/library/unittest.html)
[pytest: helps you write better programs — pytest documentation](https://docs.pytest.org/en/7.2.x/)

# Source
[[The Statistics and Calculus with Python Workshop]]
