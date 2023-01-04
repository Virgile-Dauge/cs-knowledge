---
tags: [algo/python]
---


```python
from typing import Iterable, Any
from dataclasses import dataclass

@dataclass
class Ring(List):
	l: Iterable[Any]
	i: int = 0

	def turn(self, d: int) -> int:
		self.i = (self.i+d)%len(self.l)
		return self.i
	def next(self, d: int) -> Any:
		return self.l[self.turn(d)]

r1 = Ring('abcd')
print(r1)
print(r1.next(5))
print(r1)
print(r1.next(-7))
print(r1)
```