
```python
mod = n - math.floor(n/base) * base
```



In mathematics, we choose inward jumps, i.e. forward direction for a positive number and backward direction for negative numbers.

But in Python, we have a forward direction for all positive modulo operations. 

```python
5 % 4 
```

```python
-5 % 4 
```