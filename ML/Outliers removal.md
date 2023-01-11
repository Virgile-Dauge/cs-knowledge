

# Sklearn

https://scikit-learn.org/stable/modules/outlier_detection.html

```python
import numpy as np
from sklearn.neighbors import LocalOutlierFactor
X = [[-1.1], [0.2], [101.1], [0.3]]
clf = LocalOutlierFactor(n_neighbors=2)
clf.fit_predict(X)
```