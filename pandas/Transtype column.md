```python
import pandas as pd

df = pd.DataFrame(['1', '2'], columns=['val'])
df['val'] = df['val'].astype(int)

print(df.info())
```