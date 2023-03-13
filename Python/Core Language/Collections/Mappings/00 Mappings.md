
```mermaid
classDiagram
Container <|-- Mapping
Container : __contains__
Iterable <|-- Mapping
Iterable : __iter__
Sized <|-- Mapping
Sized : __len__
Mapping <|-- MutableMapping
Mapping : __getitem__
Mapping : __contains__
Mapping : __eq__
Mapping : __ne__
Mapping : get
Mapping : items
Mapping : keys
Mapping : values
MutableMapping : __setitem__
MutableMapping : __delitem__
MutableMapping : clear
MutableMapping : pop
MutableMapping : popitem
MutableMapping : setdefault
MutableMapping : update
```

Specialized mappings often extend `dict` or `collections.UserDict` instead of ABCs.
All mapping types in the standard library use the basic `dict`, so they all require that the keys be *hashable*.


