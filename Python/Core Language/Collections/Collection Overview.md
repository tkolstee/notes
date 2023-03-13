
| Sequence Type     | Container/Flat | Mutability |
| ----------------- | -------------- | ---------- |
| list              | Container      | Mutable    |
| tuple             | Container      | Immutable  |
| collections.deque | Container      | Mutable    |
| str               | Flat           | Immutable  |
| bytes             | Flat           | Immutable  |
| bytearray         | Flat           | Mutable    |
| memoryview        | Flat           | Mutable    |
| array.array       | Flat           | Mutable           |





## Container vs. Flat Sequences
**Container** sequences hold references, so can hold items of different types.
`list`, `tuple`, `collections.deque`

**Flat** sequences store the value directly, so can only store one type:
`str`, `bytes`, `bytearray`, `memoryview`, `array.array`

## Mutable vs. Immutable Sequences
Mutable: 
