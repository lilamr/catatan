GeoPandas implements two main data structures, a [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") and a [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame"). These are subclasses of [`pandas.Series`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html#pandas.Series "(in pandas v2.2.2)") and [`pandas.DataFrame`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame "(in pandas v2.2.2)"), respectively.

## GeoSeries

A [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") is essentially a vector where each entry in the vector is a set of shapes corresponding to one observation. An entry may consist of only one shape (like a single polygon) or multiple shapes that are meant to be thought of as one observation (like the many polygons that make up the State of Hawaii or a country like Indonesia).

GeoPandas has three basic classes of geometric objects (which are actually _shapely_ objects):

- Points / Multi-Points
    
- Lines / Multi-Lines
    
- Polygons / Multi-Polygons
    

Note that all entries in a [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") need not be of the same geometric type, although certain export operations will fail if this is not the case.

### Overview of attributes and methods

The [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") class implements nearly all of the attributes and methods of Shapely objects. When applied to a [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries"), they will apply elementwise to all geometries in the series. Binary operations can be applied between two [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries"), in which case the operation is carried out elementwise. The two series will be aligned by matching indices. Binary operations can also be applied to a single geometry, in which case the operation is carried out for each element of the series with that geometry. In either case, a [`Series`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html#pandas.Series "(in pandas v2.2.2)") or a [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") will be returned, as appropriate.

A short summary of a few attributes and methods for GeoSeries is presented here, and a full list can be found in the [GeoSeries API reference](https://geopandas.org/en/stable/docs/reference/geoseries.html). There is also a family of methods for creating new shapes by expanding existing shapes or applying set-theoretic operations like “union” described in [Geometric manipulations](https://geopandas.org/en/stable/docs/user_guide/geometric_manipulations.html).

#### Attributes

- [`area`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.area.html#geopandas.GeoSeries.area "geopandas.GeoSeries.area"): shape area (units of projection – see [projections](https://geopandas.org/en/stable/docs/user_guide/projections.html))
    
- [`bounds`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.bounds.html#geopandas.GeoSeries.bounds "geopandas.GeoSeries.bounds"): tuple of max and min coordinates on each axis for each shape
    
- [`total_bounds`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.total_bounds.html#geopandas.GeoSeries.total_bounds "geopandas.GeoSeries.total_bounds"): tuple of max and min coordinates on each axis for entire GeoSeries
    
- [`geom_type`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.geom_type.html#geopandas.GeoSeries.geom_type "geopandas.GeoSeries.geom_type"): type of geometry.
    
- [`is_valid`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.is_valid.html#geopandas.GeoSeries.is_valid "geopandas.GeoSeries.is_valid"): tests if coordinates make a shape that is reasonable geometric shape according to the [Simple Feature Access](http://www.opengeospatial.org/standards/sfa) standard.
    

#### Basic methods

- [`distance()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.distance.html#geopandas.GeoSeries.distance "geopandas.GeoSeries.distance"): returns [`Series`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html#pandas.Series "(in pandas v2.2.2)") with minimum distance from each entry to `other`
    
- [`centroid`](https://geopandas.org/en/stable/docs/user_guide/geometric_manipulations.html#GeoSeries.centroid "GeoSeries.centroid"): returns [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") of centroids
    
- [`representative_point()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.representative_point.html#geopandas.GeoSeries.representative_point "geopandas.GeoSeries.representative_point"): returns [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") of points that are guaranteed to be within each geometry. It does **NOT** return centroids.
    
- [`to_crs()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.to_crs.html#geopandas.GeoSeries.to_crs "geopandas.GeoSeries.to_crs"): change coordinate reference system. See [projections](https://geopandas.org/en/stable/docs/user_guide/projections.html)
    
- [`plot()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.plot.html#geopandas.GeoSeries.plot "geopandas.GeoSeries.plot"): plot [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries"). See [mapping](https://geopandas.org/en/stable/docs/user_guide/mapping.html).
    

#### Relationship tests

- [`geom_equals_exact()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.geom_equals_exact.html#geopandas.GeoSeries.geom_equals_exact "geopandas.GeoSeries.geom_equals_exact"): is shape the same as `other` (up to a specified decimal place tolerance)
    
- [`contains()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.contains.html#geopandas.GeoSeries.contains "geopandas.GeoSeries.contains"): is shape contained within `other`
    
- [`intersects()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.intersects.html#geopandas.GeoSeries.intersects "geopandas.GeoSeries.intersects"): does shape intersect `other`
    

## GeoDataFrame

A [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame") is a tabular data structure that contains a [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries").

The most important property of a [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame") is that it always has one [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") column that holds a special status. This [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") is referred to as the [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame")’s “geometry”. When a spatial method is applied to a [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame") (or a spatial attribute like `area` is called), this commands will always act on the “geometry” column.

The “geometry” column – no matter its name – can be accessed through the `geometry` attribute (`gdf.geometry`), and the name of the `geometry` column can be found by typing `gdf.geometry.name`.

A [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame") may also contain other columns with geometrical (shapely) objects, but only one column can be the active geometry at a time. To change which column is the active geometry column, use the [`GeoDataFrame.set_geometry()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.set_geometry.html#geopandas.GeoDataFrame.set_geometry "geopandas.GeoDataFrame.set_geometry") method.

An example using the `geoda.malaria` dataset from `geodatasets` containing the counties of Colombia:

import geodatasets

colombia = geopandas.read_file(geodatasets.get_path('geoda.malaria'))

colombia.head()
Out[3]: 
   ID      ADM0  ... RP2005                                           geometry
0   1  COLOMBIA  ...  61773  POLYGON ((-71.32639 11.84789, -71.33579 11.855...
1   2  COLOMBIA  ...  36465  POLYGON ((-72.42191 11.79824, -72.41980 11.795...
2   3  COLOMBIA  ...  18368  POLYGON ((-72.18910 11.52420, -72.18330 11.532...
3   4  COLOMBIA  ...   7566  POLYGON ((-72.63800 11.36790, -72.62590 11.349...
4   5  COLOMBIA  ...   9343  POLYGON ((-74.77489 10.93158, -74.77530 10.933...

[5 rows x 51 columns]

# Plot countries

colombia.plot(markersize=.5);

![../../_images/colombia_borders.png](https://geopandas.org/en/stable/_images/colombia_borders.png)

Currently, the column named “geometry” with county borders is the active geometry column:

colombia.geometry.name
Out[5]: 'geometry'

You can also rename this column to “borders”:

colombia = colombia.rename_geometry('borders')

colombia.geometry.name
Out[7]: 'borders'

Now, you create centroids and make it the geometry:

colombia['centroid_column'] = colombia.centroid

colombia = colombia.set_geometry('centroid_column')

colombia.plot();

![../../_images/colombia_centroids.png](https://geopandas.org/en/stable/_images/colombia_centroids.png)

**Note:** A [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame") keeps track of the active column by name, so if you rename the active geometry column, you must also reset the geometry:

gdf = gdf.rename(columns={'old_name': 'new_name'}).set_geometry('new_name')

**Note 2:** Somewhat confusingly, by default when you use the [`read_file()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.read_file.html#geopandas.read_file "geopandas.read_file") command, the column containing spatial objects from the file is named “geometry” by default, and will be set as the active geometry column. However, despite using the same term for the name of the column and the name of the special attribute that keeps track of the active column, they are distinct. You can easily shift the active geometry column to a different [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") with the [`set_geometry()`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.set_geometry.html#geopandas.GeoDataFrame.set_geometry "geopandas.GeoDataFrame.set_geometry") command. Further, `gdf.geometry` will always return the active geometry column, _not_ the column named `geometry`. If you wish to call a column named “geometry”, and a different column is the active geometry column, use `gdf['geometry']`, not `gdf.geometry`.

### Attributes and methods

Any of the attributes calls or methods described for a [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries") will work on a [`GeoDataFrame`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame") – effectively, they are just applied to the “geometry” [`GeoSeries`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.html#geopandas.GeoSeries "geopandas.GeoSeries").

However, [`GeoDataFrames`](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.html#geopandas.GeoDataFrame "geopandas.GeoDataFrame") also have a few extra methods for input and output which are described on the [Reading and writing files](https://geopandas.org/en/stable/docs/user_guide/io.html) page and for geocoding with are described in [Geocoding](https://geopandas.org/en/stable/docs/user_guide/geocoding.html).

## Display options

GeoPandas has an `options` attribute with currently a single configuration option to control:

import geopandas

geopandas.options
Out[12]: 
Options(
  display_precision: None [default: None]
      The precision (maximum number of decimals) of the coordinates in the
      WKT representation in the Series/DataFrame display. By default (None),
      it tries to infer and use 3 decimals for projected coordinates and 5
      decimals for geographic coordinates.
  use_pygeos: False [default: False]
      Whether to use PyGEOS to speed up spatial operations. The default is
      True if PyGEOS is installed, and follows the USE_PYGEOS environment
      variable if set.
  io_engine: None [default: None]
      The default engine for ``read_file`` and ``to_file``. Options are
      'pyogrio' and 'fiona'.
  )

The `geopandas.options.display_precision` option can control the number of decimals to show in the display of coordinates in the geometry column. In the `colombia` example of above, the default is to show 5 decimals for geographic coordinates:

colombia['centroid_column'].head()
Out[13]: 
0    POINT (-71.74594 12.00885)
1    POINT (-72.56514 11.58174)
2    POINT (-72.35203 11.32204)
3    POINT (-73.14121 11.15251)
4    POINT (-74.64555 10.88454)
Name: centroid_column, dtype: geometry

If you want to change this, for example to see more decimals, you can do:

geopandas.options.display_precision = 9

colombia['centroid_column'].head()
Out[15]: 
0    POINT (-71.745940217 12.008854228)
1    POINT (-72.565144214 11.581744777)
2    POINT (-72.352030378 11.322036612)
3    POINT (-73.141207300 11.152507044)
4    POINT (-74.645551117 10.884543716)
Name: centroid_column, dtype: geometry