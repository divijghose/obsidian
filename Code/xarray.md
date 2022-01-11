# Data structures and I/O
Two datastructures - `DataArray` and `Dataset`
```
import xarray as xr
```
1. Display DataArray
```
display(da)
```
`xr.set_options(display_style="text")` or `xr.set_options(display_style="text")`

2. Data within a DataArray
```
da = xr.DataArray(
#data,
#dims-tuple or list
#coords- dict like mapping -> another DataArray object, tuple of form (dims,data,attrs) or a numpy array
#attrs - metadata
)

#Access
da.data
da.dims
da.coords
da.attrs
```

3. Dataset objects
Three parameters
`data_vars` : dict-like mapping -> DataArray objects or tuples
`coords`  and `attrs` : same as for DataArray

4. 