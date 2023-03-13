
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

**Containers vs. Flat**
Containers hold references and can handle different types of items.
Flat sequences hold item values directly and can handle only one type.

```mermaid
classDiagram
Container <|-- Sequence
Container : __contains__
Iterable <|-- Sequence
Iterable : __iter__
Sized <|-- Sequence
Sized : __len__
Sequence <|-- MutableSequence
Sequence : __getitem__
Sequence : __contains__
Sequence : __iter__
Sequence : __reversed__
Sequence : index
Sequence : count
MutableSequence : __setitem__
MutableSequence : __delitem__
MutableSequence : insert
MutableSequence : append
MutableSequence : reverse
MutableSequence : extend
MutableSequence : pop
MutableSequence : remove
MutableSequence : __iadd__
```


