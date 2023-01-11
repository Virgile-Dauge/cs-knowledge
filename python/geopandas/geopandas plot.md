# Documentation
Generate a plot of a GeoDataFrame with matplotlib. If a column is specified, the plot coloring will be based on values in that column.

https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.plot.html

# Example 
```python
import matplotlib.pyplot as plt
df.plot("pop_est", cmap="Blues")
plt.plot()
```

Dans IPython
```python
%matplotlib inline
df.plot("pop_est", cmap="Blues")
```

