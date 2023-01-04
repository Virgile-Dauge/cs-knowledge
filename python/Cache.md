


```python
import sys
import math
from functools import lru_cache

#n, nb, g = [int(i) for i in input().split()]
n, nb, g = 1, 2, 2

@lru_cache(maxsize=32)
def pop(n, nb, g):
    print(n, nb, g, file=sys.stderr)
    if n==0:
        return nb
    return past*(1+g) if n < 3 else past*(1+g) - pop(n-3, nb, g) 
print(pop(n, nb, g))
#print(pop.cache_info())
```
