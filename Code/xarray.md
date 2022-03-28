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
`interp` to look at values between grid points 
```
arr.interp(x=new_x_values,y=new_y_values)
```
if object with desired coordinates for interpolation already exists, use `interp_like`

```
arr.interp_like(other_array)
```

# Computation with xarray
1. Applying operators
```
ds + const
np.log(ds)
ds**2
```
2. Applying user functions
```
xr.apply_ufunc(func,ds)
```

3. Reductions 
```
ds.mean(dim=dim1)
```

4. Weighted Reductions
First create a `DataArrayWeighted` object then apply reduction to it
```
ds_weighted = ds.weighted(weights)
ds_weighted.mean(dim=dim1)
```

5. Groupby
`DateTimeAccesor` -> `ds.time.dt.month`

Groupby dimesnion
```
gb = ds.grouypby(ds.time.dt.month)
```
Applying aggregration 
```
ds_mm = gb.mean(dim="time")
```

6. Mapping
Apply function to each dataset
```
gb.map(ds)
``` 
7. Transformations
Remove mean of group from grouped data 
```
gb = ds.groupby("time.month")
ds_var = gb - gb.mean(dim="time")
```

8. Resample 
```
resample_obj = ds.resample(time="5Y")
```

9. Rolling 
Performs rolling window calculation over given length `e.g. 7 day average,12 month average`
```
rolling_obj = ds.rolling(time=12,center=True)
```

10. Coarsen
Like `resample`, works on multiple dimesnions
```
coarsen_obj = ds.coarsen(time=12)
```

# Plotting and visualization
## Basic plotting

DataArray objects have a `plot` method. This method creates plots using `matplotlib` so all of your existing matplotlib knowledge carries over!

By default `.plot()` makes

1.  a line plot for 1-D arrays using `plt.plot()`
2.  a `pcolormesh` plot for 2-D arrays using `plt.pcolormesh()`
3.  a histogram for everything else using `plt.hist()`

# Dask
1. Set up simple LocalCluster
```
from dask.distributed import Client

client = Client()
```
3. Dask Arrays
```
import dask.array as da

ones=da.ones(shape)
```