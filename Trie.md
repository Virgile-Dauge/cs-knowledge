```python
from __future__ import annotations
from dataclasses import dataclass, field
from typing import List,  Tuple
@dataclass
class Trie:
	origin: str
	tree: List[Tuple[str, List[int], List[int]]] = field(default_factory=list)

	def __init__(self):
		...

	def add(self, i: int, s: int) -> Trie:
		if s[0] in tree[0]:
			...
t = Trie('abab')
print(t)
```