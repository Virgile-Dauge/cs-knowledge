---
tags: python
---


```python
a = 'abcdefghijklmnopqrstuvwxyz'
n = 3
l = [a[i:i+n] for i in range(0, len(a), n)]
print(l)
```


```python
import itertools

a = 'abcdefghijklmnopqrstuvwxyz'
n = 3

def batched(iterable, n):
    "Batch data into lists of length n. The last batch may be shorter."
    # batched('ABCDEFG', 3) --> ABC DEF G
    if n < 1:
        raise ValueError('n must be at least one')
    it = iter(iterable)
    while (batch := list(itertools.islice(it, n))):
        yield batch

for l in batched(a, n):
	print(l)
```