https://en.wikipedia.org/wiki/NetCDF

**NetCDF** (**Network Common Data Form**) is a set of [software libraries](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)") and self-describing, machine-independent data formats that support the creation, access, and sharing of [array-oriented](https://en.wikipedia.org/wiki/Array_programming "Array programming") scientific data.

Filename extension: **.nc**
Type of format: **scientific binary data**

# How to open ?

With #xarray to #pandas
```python
import xarray as xr

ds = xr.open_dataset('/path/to/netcdf')
df = ds.to_dataframe()
```

