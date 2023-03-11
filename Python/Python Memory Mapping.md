## Bitwise Operators

```toc
```

| Operator | Meaning     |
| -------- | ----------- |
| &        | Bitwise AND |
| \|       | Bitwise OR  |
| ^        | Bitwise XOR |
| ~        | Negation    |
| <<       | Left Shift  |
| >>       | Right Shift |

## Masking
To find the value of bit `bit_number` in a bitfield
```python
mask = 1 << bit_number
result = bool(bitfield & mask)
```

To clear a bit in the bitfield
```python
mask = ~(1 << bit_number)
bitfield &= mask
```


## Bytes
```
b1 = b"A literal byte string"   # 7-bit ASCII
b2 = b"Norwegian characters \xc5 and \xd8 are 8-bit ASCII"
b3 = bytes(5)                   # b"\x00\x00\x00\x00\x00"
b4 = bytes(range(65, 65+26))    # b'ABCDE...Z'
b5 = bytes('Norwegian characters Å and Ø', 'utf-16')
b6 = bytes.fromhex('deadbeef')
```

## Bytearray
Mutable complement to bytes object (bytearray:bytes::list:tuple)

Same constructor calls as with bytes, but no literal string prefix like with `b"..."`
```python
b1 = bytearray(b"A literal byte string")
b2 = bytearray(b"Norwegian characters \xc5 and \xd8 are 8-bit ASCII")
b3 = bytearray(5)                   # b"\x00\x00\x00\x00\x00"
b4 = bytearray(range(65, 65+26))    # b'ABCDE...Z'
b5 = bytearray('Norwegian characters Å and Ø', 'utf-16')
b6 = bytearray.fromhex('deadbeef')
```

### Modifying bytearray
```python
b1.extend(b" with 7-bit ASCII")
b2[33:38] = b"extended"
b4.lower()
b5.split()
```


## Reading a C Vector
````ad-example
title: Sample C code defining a vector
collapse: true
`create_vectors.c`
```c
#include <stdio.h>

struct Vector {
  float x;
  float y;
  float z;
};

struct Color {
  unsigned short int red;
  unsigned short int green;
  unsigned short int blue;
};

struct Vertex {
  struct Vector position;
  struct Color color;
};

int main(int argc, char** argv) {
  struct Vertex vertices[] = {
	  {
	    .position = {3323.176, 6562.231, 9351.231 },
	    .color = { 3040, 34423, 54321 }
	  },
	  {
	    .position = { 7623.982, 2542.231, 9823.121 },
	    .color = { 32736, 5342, 2321 }
	  },
	  {
	    .position = { 6729.862, 2347.212, 3421.322 },
	    .color = { 45263, 36921, 36701 }
	  },
	  {
	    .position = { 6352.121, 3432.111, 9763.232 },
	    .color = { 56222, 36612, 11214}
	  }
  };
  FILE* file = fopen("colors.bin", "wb");
  if (file == NULL) { return -1; }
  fwrite(vertices, sizeof(struct Vertex), 4, file);
  fclose(file);
  return 0;  
}
```

````


### Struct Module
Allows you to unpack a C struct in memory.

```python
import struct

# read data into 'buffer'

for fields in struct.iter_unpack("@3f3H2x", buffer):
  # 3 floats, 3 unsigned short ints, 2 padding bits
  pass # ...
```

Many C structs use padding bytes to align to 4-byte boundaries, including the above example. Often have to view hex dumps and look for the padding `\00` bytes at the end of the struct.

Prefix in unpack string (@ is default)
| Character | Byte Order           | Size     | Alignment |
|:---------:| -------------------- | -------- | --------- |
|     @     | native               | native   | native    |
|     =     | native               | standard | none      |
|     <     | little-endian        | standard | none      |
|     >     | big-endian           | standard | none      |
|     !     | network(=big-endian) | standard | none      |

| Format |       C Type       |   Python Type   | Size |
|:------:|:------------------|:---------------|:----:|
|   x    |      pad byte      |    no value     |      |
|   c    |        char        | bytes of len(1) |  1   |
|   b    |    signed char     |       int       |  1   |
|   B    |   unsigned char    |       int       |  1   |
|   ?    |       \_Bool       |      bool       |  1   |
|   h    |     short int      |       int       |  2   |
|   H    | unsigned short int |       int       |  2   |
|   i    |        int         |       int       |  4   |
|   I    |    unsigned int    |       int       |  4   |
|   f    |       float        |      float      |  4   |
|   d    |       double       |      float      |  8   |
|   s    |       char[]       |      bytes      |  8   |
|        |                    |                 |      |

````ad-example
title: Example code: Struct Module
collapse: true

`read_vectors_struct.py`
```python
import struct
from pprint import pprint
from dataclasses import dataclass

@dataclass(frozen=True)
class Vector:
  x: float
  y: float
  z: float

@dataclass(frozen=True)
class Color:
  red:   int
  green: int
  blue:  int

@dataclass(frozen=True)
class Vertex:
  vector: Vector
  color: Color

def make_colored_vertex(x, y, z, red, green, blue):
  return Vertex(
    Vector(x, y, z),
    Color(red, green, blue),
  )


def main():
  with open("./colors.bin", "rb") as f:
    buffer = f.read()

  vertices = []
  for fields in struct.iter_unpack("@3f3H2x", buffer):
    vertex = make_colored_vertex(*fields)
    vertices.append(vertex)
  pprint(vertices)

if __name__ == "__main__":
  main()

```
`````


### Memoryview
Uses C "Buffer Protocol" (internal CPython C-API)

Works like bytes array but is actually a view of the byte buffer. Native types bytes and bytearray support memory protocol

Supports indexing (returns byte), slicing (returns new memoryview object).

The cast function enables us to cast using the same format strings as with unpacking with the struct module.

```python
mem = memoryview(buffer)

print(hex(mem[21]))      # Copy of the byte
mem2 = mem[12:18]        # Memoryview of the slice
mem2.cast('H')           # View - not a copy - cast to integers
mem2.cast('H')[0]        # Access individual integers in the cast slice
mem2.cast('H').tolist()  # List of all integer values in the cast slice
print(mem2.format)
```

````ad-example
title: Example Code: MemoryView
collapse: true
```python
import struct
from pprint import pprint
from dataclasses import dataclass

class Vector:
  def __init__(self, memf):
    if memf.format not in "fd":
      raise TypeError("memoryview values must be binary floating-point numbers")
    if len(memf) != 3:
      raise ValueError("memoryview must contain three floats")
    self._mem = memf
  @property
  def x(self): return self._mem[0]
  @property
  def y(self): return self._mem[1]
  @property
  def z(self): return self._mem[2]
  def __repr__(self):
    return f"{type(self).__name__}({self.x}, {self.y}, {self.z})"

class Color:
  def __init__(self, memi):
    if memi.format not in "HILQ":
      raise TypeError("memoryview must be unsigned integers")
    if len(memi) != 3:
      raise ValueError("memoryview must contain three integers")
    self._mem = memi
  @property
  def red(self): return self._mem[0]
  @property
  def green(self): return self._mem[1]
  @property
  def blue(self): return self._mem[2]
  def __repr__(self):
    return f"{type(self).__name__}({self.red}, {self.green}, {self.blue})"
  

@dataclass(frozen=True)
class Vertex:
  vector: Vector
  color: Color

def make_colored_vertex(mem_vertex):
  mem_vector = mem_vertex[0:12].cast("f")
  mem_color  = mem_vertex[12:18].cast("H")
  return Vertex(
    Vector(mem_vector),
    Color(mem_color),
  )


def main():
  with open("./colors.bin", "rb") as f:
    buffer = f.read()

  mem = memoryview(buffer)
  ALIGNMENT = 4
  VERTEX_SIZE = 18
  PADDING = (ALIGNMENT - (VERTEX_SIZE % ALIGNMENT)) % ALIGNMENT
  VERTEX_STRIDE = VERTEX_SIZE + PADDING
  vertex_mems = (mem[i:i+VERTEX_SIZE] for i in range(0, len(mem), VERTEX_STRIDE))
  vertices = [make_colored_vertex(vertex_mem) for vertex_mem in vertex_mems]
  pprint(vertices)

if __name__ == "__main__":
  main()
```
````

### Memory-Mapped Files
Example: [[DEDUPED/Python/Code Samples/create_vectors.c]] and [[DEDUPED/Python/Code Samples/read_vectors_mmap.py]]

Provided by `mmap` module

```python
import mmap

with mmap.mmap(f.fileno(), 0, access=mmap.ACCESS_READ) as buffer:
	mem = memoryview(buffer)
```

Now mem is a regular memoryview but backed by a disk file via OS virtual memory.

Will not close properly unless dependent pointers (memoryview and slices) are closed.
Best practice is to delete these within a "finally" clause of a "try" block, to clean up references even if an error occurs.



````ad-example
title: Sample Code: Memory Mapped File
collapse: true
```python
import mmap
from pprint import pprint
from dataclasses import dataclass

class Vector:
  def __init__(self, memf):
    if memf.format not in "fd":
      raise TypeError("memoryview values must be binary floating-point numbers")
    if len(memf) != 3:
      raise ValueError("memoryview must contain three floats")
    self._mem = memf
  @property
  def x(self): return self._mem[0]
  @property
  def y(self): return self._mem[1]
  @property
  def z(self): return self._mem[2]
  def __repr__(self):
    return f"{type(self).__name__}({self.x}, {self.y}, {self.z})"

class Color:
  def __init__(self, memi):
    if memi.format not in "HILQ":
      raise TypeError("memoryview must be unsigned integers")
    if len(memi) != 3:
      raise ValueError("memoryview must contain three integers")
    self._mem = memi
  @property
  def red(self): return self._mem[0]
  @property
  def green(self): return self._mem[1]
  @property
  def blue(self): return self._mem[2]
  def __repr__(self):
    return f"{type(self).__name__}({self.red}, {self.green}, {self.blue})"
  

@dataclass(frozen=True)
class Vertex:
  vector: Vector
  color: Color

def make_colored_vertex(mem_vertex):
  mem_vector = mem_vertex[0:12].cast("f")
  mem_color  = mem_vertex[12:18].cast("H")
  return Vertex(
    Vector(mem_vector),
    Color(mem_color),
  )


def main():
  with open("./colors.bin", "rb") as f:
    with mmap.mmap(f.fileno(), 0, access=mmap.ACCESS_READ) as buffer:
      
      mem = memoryview(buffer)

      ALIGNMENT = 4
      VERTEX_SIZE = 18
      PADDING = (ALIGNMENT - (VERTEX_SIZE % ALIGNMENT)) % ALIGNMENT
      VERTEX_STRIDE = VERTEX_SIZE + PADDING
      
      vertex_mems = (mem[i:i+VERTEX_SIZE] for i in range(0, len(mem), VERTEX_STRIDE))

      # Try/finally and del statements are to prevent
      # "BufferError: cannot close exported pointers exist"
      # by memoryview objects that depend upon mmap below.
      try:
        vertices = [make_colored_vertex(vertex_mem) for vertex_mem in vertex_mems]
        pprint(vertices)
      finally:
        del(vertices)
        del(mem)



if __name__ == "__main__":
  main()

```
````