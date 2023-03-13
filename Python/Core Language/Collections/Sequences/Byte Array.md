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
