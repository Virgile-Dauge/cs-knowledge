```python

tests = ['aaaa', 'aaaabbbb', 'abab']

def detect(s: str):

	ws=1
	serie = False
	d = [[]]
	i=0
	while i < len(s):
		if i + ws < len(s) and s[i:i+ws]==s[i+ws:i+2*ws]:
			serie = True
			print('if', s, i, ws)
			d[-1] += [s[i:i+ws]]
			i += ws
		else:
			print('else', s, i, ws)
			print(s)
			print(' '*i+'|')
			if serie:
				serie = False
				d += []
				i += 1
				ws=1
			else:
				ws+=1
	return d

for t in tests:
	print(detect(t))
```