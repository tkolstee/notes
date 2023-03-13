## Classifying Sequences

### Container vs. Flat
Containers hold references to the objects they contain, and are able to hold different types of objects:  `list`, `tuple`
Flat sequences hold their values directly and can only contain one type: `str`, `bytes`

### Mutable vs. Immutable
Mutable sequences can be modified (reordered, added to, etc.) whereas immutable sequences are fixed.
The UML diagram describes (conceptually, not in implementation) the relationship between Mutable and Immutable sequences.

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
