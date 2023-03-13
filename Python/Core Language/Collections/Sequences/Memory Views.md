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

----