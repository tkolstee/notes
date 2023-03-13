```python
b1 = b"A literal byte string"   # 7-bit ASCII
b2 = b"Norwegian characters \xc5 and \xd8 are 8-bit ASCII"
b3 = bytes(5)                   # b"\x00\x00\x00\x00\x00"
b4 = bytes(range(65, 65+26))    # b'ABCDE...Z'
b5 = bytes('Norwegian characters Å and Ø', 'utf-16')
b6 = bytes.fromhex('deadbeef')
```



