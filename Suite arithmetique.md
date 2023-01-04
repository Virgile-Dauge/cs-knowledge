
https://fr.wikipedia.org/wiki/Suite_arithm%C3%A9tique


$a_n = a + (n-1)d$

```python
a = 1
d = 5
n = 5
an = a + (n - 1)*d

print([a + (i - 1)*d for i in range(1, n+1)])
```