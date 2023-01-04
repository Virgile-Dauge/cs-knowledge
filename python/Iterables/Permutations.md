```python
from itertools import permutations
print(*permutations('ABXY', 2))
```


Ici, on utilise la fonction _str.join_ qui permet de concaténer un itérable dans une chaine de caractères, voir ici : [[Concat iterable into str]]

```python
from itertools import permutations
ps=[''.join(p) for p in permutations('ABCXYZ', 2)]
print(ps)
```