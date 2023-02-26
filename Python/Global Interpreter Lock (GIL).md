---
aliases: [ GIL, Global Interpreter Lock ]
---

System-wide lock which prevents the Python interpreter from running more than one instruction at a time.

This is an intentional barrier to highly concurrent multithreaded Python programs.

There are C / C++ extensions that use native multithreading and can run code without being limited by the GIL, as long as they do not need to interact regularly with Python objects.
