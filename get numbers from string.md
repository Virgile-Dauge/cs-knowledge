```python
import re
s = "hello 42 I'm a 32 string 30"
l = re.findall(r'\d+', s)
print(l)
```