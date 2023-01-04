```python
import numpy as np

A, B = np.array([0, 0]), np.array([1, 1])
dist = np.linalg.norm(A-B)

print(dist)
```