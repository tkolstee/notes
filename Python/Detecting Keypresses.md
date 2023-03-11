
Detecting a single keypress requires OS specific modules:
- Input() waits for return
- Windows: `msvcrt` module (MS Visual C Runtime)
- Linux/Mac: `tty`, `termios`, `sys`

```python
"""keypress - A module for detecting a single keypress."""

try:
	import msvcrt
	def getkey():
		"""Wait for a keypress and return a single character string."""
		return msvcrt.getch()
except ImportError:
	import sys
	import tty
	import termios
	def getkey():
		"""Wait for a keypress and return a single character string."""
		fd = sys.stdin.fileno()
		original_attributes = termios.tcgettr(fd)
		try:
			tty.setraw(sys.stdin.fileno())
			ch = sys.stdin.read(1)
		finally:
			termios.tcsetattr(fd, termios.TCSADRAIN, original_attributes)
		return ch

	# If either of the Unix-specific tty or termios are not found,
	# we allow the ImportError to propagate from here.		
	# Depending upon our use case, we might instead use input() and wait for a return.
```
