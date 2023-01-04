
**N** points suffisent à définir une _courbe polynomiale_ de degré **N**, il est donc possible, avec **N** valeurs, de retrouver les coefficients grâce à un système d'équations linéaires en O(n^2).


https://numpy.org/doc/stable/reference/generated/numpy.polynomial.polynomial.Polynomial.fit.html#numpy.polynomial.polynomial.Polynomial.fit

```python
from numpy.polynomial import Polynomial

X = [1, 2, 6, 9]
Y = [2**x for x in X]

f = Polynomial.fit(X, Y, deg=len(X))
print(f, type(f))
print(f(X))
```