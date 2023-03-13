
```python
>>> b"A literal byte string"          # b'A literal byte string'
>>> b"\xc5 and \xd8 are 8-bit ASCII"  # b'\xc5 and \xd8 are 8-bit ASCII'
>>> bytes(5)                          # b'\x00\x00\x00\x00\x00'
>>> bytes(range(65, 65+26))           # b'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
>>> bytes('Å and Ø', 'utf-16')        # b'\xff\xfe\xc5\x00 \x00a\x00n\x00d\x00 \x00\xd8\x00'
>>> bytes.fromhex('deadbeef')         # b'\xde\xad\xbe\xef'
```