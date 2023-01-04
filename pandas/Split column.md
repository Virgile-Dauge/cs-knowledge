```python
import pandas as pd

df = pd.DataFrame(['coucou toi', 'à séparer'], columns=['name'])
df[['a', 'b']] = df.name.str.split(" ",expand=True)

print(df)
```