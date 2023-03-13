`collections.deque` is a thread-safe, double-ended queue.

Can be created with a maximum length, and will discard oldest items when it reaches that length.



```python
>>> dq = deque(
...   range(10), maxlen=10
... )                               # deque([0, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10)
>>> dq.rotate(3)                    # deque([7, 8, 9, 0, 1, 2, 3, 4, 5, 6], maxlen=10)
>>> dq.rotate(-4)                   # deque([1, 2, 3, 4, 5, 6, 7, 8, 9, 0], maxlen=10)
>>> dq.appendleft(-1)               # deque([-1, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10)
>>> dq.extend([11, 22, 33])         # deque([3, 4, 5, 6, 7, 8, 9, 11, 22, 33], maxlen=10)
>>> dq.extendleft([10, 20, 30, 40]) # deque([40, 30, 20, 10, 3, 4, 5, 6, 7, 8], maxlen=10)
```
`.rotate(n)` rotates the entire queue right (positive n) or left (negative n) with wraparound: