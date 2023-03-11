
## Testing for Existence
`os.path.exists(filename)`

## Enumerating Files in a Directory
```python
import os
path="/foo/bar"
dir_list = os.listdir(path)   # List of file and dir names
```
os.walk - recursive data structure of files and dirs
os.scandir - returns iterator of os.DirEntry object

## Opening Files
`open(file, mode, encoding)`
| arg      | Description                                                     |
| -------- | --------------------------------------------------------------- |
| file     | filename to open                                                |
| mode     | r/w/x/a, append 'b'inary or 't'ext, '+' for update (read/write) |
| encoding | 'utf-8' is common                                               |

### Binary vs. Text mode
Text mode uses universal newlines (platform dependent), and encodes/decodes during write/read.

### Encoding
Default is often but not always UTF-8. See `sys.getdefaultencoding()`

### Resource Manager syntax
```python
with open(file, mode) as f:
	do_stuff
```
Will automatically close file once done or if an exception is thrown.

## Closing
Explicit close (without resource manager):
```python
if not f.closed:   # bool whether file is already closed
	f.close()      # actual explicit close
```


## Writing
| Method             | Desc                                                          |
| ------------------ | ------------------------------------------------------------- |
| `f.write(string)`    | Returns number of code points (chars) written, not bytes      |
| `f.writelines(list)` | Writes all the list items as files. Need to add own newlines. |

## Reading
| Method         | Desc                                                                  |
| -------------- | --------------------------------------------------------------------- |
| `f.read(32)`   | Read number of characters. Advances file pointer.                     |
| `f.readline()` | Read to next newline. Includes newline if present (may not be at EOF) |
| `f.readlines()`  | Returns a list of strings containing lines, including newlines.                                                                      |

After EOF, subsequent calls return the empty string.

## Seek and Tell
| Method    | Desc                                                                                       |
| --------- | ------------------------------------------------------------------------------------------ |
| f.seek(0) | Seek to position as offset from start. For text only 0 and values from tell() are allowed. |
| f.tell()  | Find current position of file pointer.                                                                                           |

## Iteration
```python
with open(file, 'r') as f:
	for line in f:
		print(line.strip())
```

## File-Like Objects
Not a formal spec; includes things like urllib so that they can be treated like files and used in the same manner.

