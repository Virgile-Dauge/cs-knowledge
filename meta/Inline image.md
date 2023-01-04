---
tags: [python, meta]
---

```run-python

import seaborn as sns
import matplotlib.pyplot as plt
sns.set_style("darkgrid")
iris = sns.load_dataset('iris')
sns.FacetGrid(iris, hue ="species", height = 5).map(plt.scatter, 'sepal_length', 'petal_length').add_legend()
plt.show()
```

