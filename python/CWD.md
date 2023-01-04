---
tags: python
---

# Default cwd

Obtenir le répertoire depuis lequel le script est exécuté :
```run-python
import os
print(os.getcwd())
```


```run-python
print(__file__)
```



Change _cwd_

```run-python
import os
print(os.getcwd())
os.chdir('..')
print(os.getcwd())
```

Set cwd to script location

```run-python
import os
os.chdir(os.path.abspath(os.path.dirname(__file__)))
```