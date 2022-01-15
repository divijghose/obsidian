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

4. Roundtripping and I/O
Converting pandas object to dataset
```
series.to_xarray()
```
Converting xarray object to series
```
ds.a.to_series()
```
To dataframe
```
ds.a.to_dataframe()
```

5. Reading and writing netCDF
```
ds.to_netcdf("set_name.nc") #dataset
ds.a.to_netcdf("array_name.nc") #dataarray
```

```
xr.open_dataset("set_name.nc")
xr.open_dataarray("aarray_name.nc")
```

6. Reading and writing Zarr
```
ds.to_zrr("ds.zarr",m)
```
_____________________________________________________
# Working with labeled data
1. Selecting data from Dataarray
```
arr =xr.DataArray(data,,
				  dims = ("x","y"))
arr.isel(x=1,y=3)
```

2. Data Slicing
```
ds = xr.Dataset(data_vars={"a"":(("x","y"),a_data),
						   "b":(("x","y"),b_data)})
ds.isel(x=slice(None,2),y=slice(1,None))
```

Here, `isel` means integer indices select

3. Coordinate labels and label based indexing
Use `sel` instead of `isel`
```
arr.sel(x=x_value,y=y_value)
```
or to select nearest
```
arr.sel(x=x_value,y=y_value, method="nearest")
```
or to select multiple
```
arr.sel(x=slice(x_value1,x_value2),y=slice(y_value1,y_value2))
```
or to drop data, use `drop_sel`
```
arr.drop_sel(x=x_value)
```

4. Interpolation
