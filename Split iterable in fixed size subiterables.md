---
tags: python
---


```python
a = 'abcdefghijklmnopqrstuvwxyz'
n = 3
l = [a[i:i+n] for i in range(0, len(a), n)]
print(l)
```
