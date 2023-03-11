
## General Design Principles
### Exceptions as Normal Signalling
In Python, exceptions are a normal, expected part of program flow. Some languages only use exceptions for error conditions. For example, when iterating over a collection the end is signalled using a `StopIteration` exception.

### Easier to Ask Forgiveness than Permission
Some languages (like C) favor a lot of pre- and post- error checking. This code is harder to read and adds very little to the process in many cases. It also leads to inconsistent error checking based upon what was anticipated vs. truly unexpected.

Pythonic design prefers code mainly follow the "happy path". Re-raising errors that will happen further down the line adds nothing to the process, and requires that you anticipate all the places errors might happen. It also makes the code harder to read.

## Exceptions are Objects
Exceptions are Objects which are all subclasses of the `Exception` type (which in turn inherits from `BaseException`)

They are arranged in hierarchical inheritance groups for dealing with similar types together.

The exception hierarchy for Python 3.8 is listed below. This can be examined through `__mro__`

![[Exception Hierarchy 1.png]]

## Raising Exceptions
Use `raise ExceptionObject(params)` to create an exception object and raise it on the spot.
> [!Example]- Example: Raising an Exception
> ```python
> def square_root(x):
> 	if x < 0:
> 		raise ValueError("value for square root must be positive.")
> 	# ...
> ```

[[Python Assertions|Assertions]] can also raise exceptions.

## Catching Exceptions
Code which may raise exceptions can be run in a `try` block, which is capable of handling them.

### Try block syntax
> [!Example]- Example: try block with except, else, finally clauses
> ```python
> try:
> 	do_a_dangerous_thing()
> 	do_other_dangerous_thing()                # If line above throws an error, we never get here
> except FileNotFoundError:
> 	handle_file_not_found()
> except (KeyError, TypeError):
> 	handle_key_or_type_error()
> except ValueError:
> 	raise                                     # Re-raise same error.
> except ZeroDivisionError as e:
> 	print(f"Error: {e!r}", file=sys.stderr)   # Print e.__repr__() to stderr
> except:
> 	handle_other_exception()
> finally:
> 	stuff_that_should_always_happen()
> ```

#### try block
The try block executes until it encounters an exception.
Execution is then handed off to the first listed `except` block that handles exceptions of the type raised.

#### except block
A bare `except` block will handle ANY exception of ANY type.
The `except` block can list a type (or tuple of types) of exceptions. It will handle these exceptions or any of their descendants.
If listing a type or types, an `as` statement provides the exception object as a variable within the block.

> [!Note] To use `as` with a catch-all, use `Exception` as the exception type, which is the parent of most exceptions.

> [!Warning]- Pitfall: overly broad or long-running exception handlers
> The dangers of catch-alls
> Some exceptions represent conditions that should not be handled by the program but should terminate it. 
> These include coding errors, OS error conditions, or conditions like user exit through `^C`.
> Some examples are `SystemExit`, `KeyboardInterrupt`, `AssertionError`, and `ImportError`.
> An overly broad or long exception handler might catch these where undesired. 

> [!Warning]- Pitfall: Keep exceptions inside the block where they are handled.
> Exceptions can be quite large in terms of memory usage, containing code and state from the context in which they were raised. When handling exceptions in a `try...except` block, it's generally not a good idea to copy them to a higher-scoped variable that will exist outside the `except` clause.

#### else block
An `else` block will execute if the `try` block completes with no exception raised.
Code should be placed here and not at the end of the `try` block if it is not expected to raise exceptions.

#### finally block
The `finally` block runs after any exception handlers or else blocks, and runs whether or not an exception is raised or even caught.
It is generally used for cleanup of resources, e.g. closing open files, connections, and transactions.

## Uncaught Exceptions
Exceptions which are not caught in a `try` block propagate up to the calling function. 
This propagation continues until either the exception is caught or the main program is reached.
If the main program receives an uncaught exception, the program terminates with a stack trace.

## Exception Payloads
Exceptions can carry payload data.
In a `try...except` block, `e.args` contains a tuple of the arguments.
`str` and `repr` representations of the object should also contain the string.

Most accept a string carrying an error message that is printed in the traceback.
[PEP352](https://peps.python.org/pep-0352/) recommends, but does not require, that exceptions only take a string argument.

You can store more data in other attributes of the exception.
For example `UnicodeError` carries `encoding`, `reason`, `object`, `start`, and `end` attributes.

## User-defined Exceptions
Domain-specific error classes can be be created. Often an empty class is enough:

`class MyCustomError(Exception): pass`

You can also choose to implement more complex exceptions, such as those that override `__init__`, `__str__`, and `__repr__`.

Custom exceptions should genearlly be implemented as immutable for safety.

## Chaining Exceptions
Chaining exceptions associates one exception with another.

### Implicit Chaining
This happens when one exception is raised while processing another (in the `except` block).
The original exception is stored in the new exception's `__context__` attribute.

The stack trace will show both errors.
> [!Example]- Example: Traceback message showing implicit exception chaining
> ```
> Traceback (most recent call last):
> [...]
> __main__.TriangleError: Invalid Triangle!
> 
> During handling of the above exception, another exception occurred:
> 
> Traceback (most recent call last):
> [...]
> io.UnsupportedOperation: not writable
> ```

### Explicit Chaining
Implicitly called, like `raise ExceptionType(message) from other_exception`
The original exception is stored in the new exception's `__cause__` attribute.

The stack trace will show both errors.
> [!Example]- Example: Code to generate an explicit exception
> ```python
> try:
> 	return a / b
> except ZeroDivisionError as e:
> 	raise InclinationError("Slope cannot be vertical") from e
> ```

> [!Example]- Example: Traceback message showing explicit exception chaining
> ```
> Traceback (most recent call last):
> [...]
> ZeroDivisionError: division by zero
> 
> The above exception was the direct cause of the following exception:
> 
> Traceback (most recent call last):
> [...]
> __main__.InclinationError: Slope cannot be vertical
> ```

## Compile-Time Exceptions
Exceptions involving syntax such as `IndentationError`, `SyntaxError`, and `NameError` are often raised at compile time instead of runtime, so are almost never caught by `try` blocks.

