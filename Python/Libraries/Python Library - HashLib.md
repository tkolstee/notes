
## Quick Start

Instantiate an object, write content to it with `update`, perhaps multiple times.
Digests can be obtained at intermediate points

```python
import hashlib
m = hashlib.sha256()

m.update(b"Nobody inspects")
m.update(b" the spammish repetition")

m.digest()
# b'\x03\x1e\xdd}Ae\x15\x93\xc5\xfe\\\x00o\xa5u+7\xfd\xdf\xf7\xbcN\x84:\xa6\xaf\x0c\x95\x0fK\x94\x06'

m.hexdigest()
# '031edd7d41651593c5fe5c006fa5752b37fddff7bc4e843aa6af0c950f4b9406'
```

## Condensed
```python
hashlib.sha256(bytes_obj).hexdigest()
```


----
# Source
[hashlib — Secure hashes and message digests — Python 3.11.0 documentation](https://docs.python.org/3/library/hashlib.html)
