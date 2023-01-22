# Convolution

## quèsaco ?

C'est une opération élémentaire de combinaison de fonctions, comme l'addition ou la multiplication des termes.

https://www.youtube.com/watch?v=KuXjwB4LzSA

## Utilisation

Combiner des distributionsde probabilités

## how to #python

En utilisant la méthode lente proposée par numpy

```python
import numpy as np
a1 = np.random.random(100000)
a2 = np.random.random(100000)

np.convolve(a1, a2)
```

En utilisant la méthode plus rapide (plusieurs ordres de grandeurs !)

```python
import scipy.signal
a1 = np.random.random(100000)
a2 = np.random.random(100000)

scipy.signal.fftconvolve(a1, a2)
```
