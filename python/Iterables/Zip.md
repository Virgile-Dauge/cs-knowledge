---
tags: [python/iter]
---

```python
a = 'abc'
A = 'abc'.upper() + 'RAB'

for l, L in zip(a, A):
	print(l, L)
```
Zip permet d'iterer sur plusieurs itérables en paralléle. La fonction build-in coupe la liste la plus longue des deux listes.

**itertools** propose une version qui permet d'alonger la plus petuite des listes avec une valeur.
```python
import itertools

a = 'abc'
A = 'abc'.upper() + 'RAB'

for l, L in itertools.zip_longest(a, A, fillvalue='-'):
	print(l, L)
```