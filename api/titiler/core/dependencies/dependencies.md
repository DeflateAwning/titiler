# Module titiler.core.dependencies

Common dependency.

## Variables

```python3
RescaleType
```

## Functions

    
### BufferParams

```python3
def BufferParams(
    buffer: typing_extensions.Annotated[Union[float, NoneType], Query(PydanticUndefined)] = None
) -> Union[float, NoneType]
```

Tile buffer Parameter.

    
### ColorFormulaParams

```python3
def ColorFormulaParams(
    color_formula: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[str, NoneType]
```

ColorFormula Parameter.

    
### ColorMapParams

```python3
def ColorMapParams(
    colormap_name: typing_extensions.Annotated[Literal['oranges', 'gist_earth', 'gray', 'dense', 'purples', 'puor', 'gnuplot2_r', 'spectral', 'rain', 'cfastie', 'tab20_r', 'curl', 'solar_r', 'terrain', 'afmhot_r', 'cubehelix', 'jet_r', 'magma_r', 'gist_yarg', 'tab20', 'rdgy', 'afmhot', 'gist_earth_r', 'rdgy_r', 'viridis_r', 'reds_r', 'binary_r', 'flag', 'turbid', 'accent', 'thermal', 'pink', 'plasma', 'balance_r', 'cool', 'pubugn_r', 'set3', 'gnuplot', 'ocean', 'copper_r', 'bwr', 'matter_r', 'turbid_r', 'gnuplot_r', 'amp', 'orrd', 'tab20b_r', 'algae', 'rdylgn_r', 'gist_gray_r', 'prism_r', 'ocean_r', 'autumn_r', 'piyg', 'tarn', 'greys_r', 'set2_r', 'winter_r', 'brbg_r', 'gist_rainbow', 'pubu', 'ylgn_r', 'gist_heat_r', 'seismic', 'dark2', 'hot', 'rdylgn', 'oranges_r', 'puor_r', 'bwr_r', 'ylorrd_r', 'inferno', 'speed', 'set3_r', 'ylgnbu', 'balance', 'rdylbu', 'greens', 'ylgnbu_r', 'topo_r', 'wistia', 'prgn_r', 'bupu', 'jet', 'gist_gray', 'ylgn', 'tab10_r', 'seismic_r', 'twilight', 'tab20c_r', 'hsv_r', 'ylorbr_r', 'orrd_r', 'gist_heat', 'blues', 'gist_ncar', 'coolwarm_r', 'paired', 'wistia_r', 'purd_r', 'autumn', 'greys', 'diff', 'topo', 'tab20b', 'oxy_r', 'purples_r', 'diff_r', 'rdylbu_r', 'tempo', 'tab20c', 'gist_stern_r', 'prism', 'tarn_r', 'gnuplot2', 'set1_r', 'bugn_r', 'purd', 'cmrmap_r', 'cividis_r', 'spectral_r', 'dark2_r', 'pastel1_r', 'inferno_r', 'twilight_shifted_r', 'delta', 'pubu_r', 'terrain_r', 'ice', 'brbg', 'viridis', 'hot_r', 'rainbow_r', 'haline', 'rdpu', 'cool_r', 'magma', 'tab10', 'solar', 'twilight_shifted', 'gist_yarg_r', 'coolwarm', 'oxy', 'amp_r', 'tempo_r', 'flag_r', 'brg', 'rdpu_r', 'pubugn', 'bone_r', 'deep', 'winter', 'dense_r', 'gnbu', 'blues_r', 'summer_r', 'cubehelix_r', 'speed_r', 'cividis', 'hsv', 'gray_r', 'piyg_r', 'binary', 'plasma_r', 'gist_rainbow_r', 'pastel1', 'set1', 'nipy_spectral_r', 'gnbu_r', 'prgn', 'copper', 'rplumbo', 'thermal_r', 'pastel2', 'rdbu', 'spring_r', 'delta_r', 'set2', 'rainbow', 'bugn', 'greens_r', 'brg_r', 'reds', 'turbo', 'ylorrd', 'curl_r', 'gist_stern', 'schwarzwald', 'phase', 'rain_r', 'matter', 'deep_r', 'ice_r', 'paired_r', 'cmrmap', 'bupu_r', 'pastel2_r', 'spring', 'phase_r', 'algae_r', 'turbo_r', 'rdbu_r', 'nipy_spectral', 'bone', 'ylorbr', 'pink_r', 'gist_ncar_r', 'twilight_r', 'accent_r', 'summer', 'haline_r'], Query(PydanticUndefined)] = None,
    colormap: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

    
### CoordCRSParams

```python3
def CoordCRSParams(
    crs: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[rasterio.crs.CRS, NoneType]
```

Coordinate Reference System Coordinates Param.

    
### DatasetPathParams

```python3
def DatasetPathParams(
    url: typing_extensions.Annotated[str, Query(PydanticUndefined)]
) -> str
```

Create dataset path from args

    
### DstCRSParams

```python3
def DstCRSParams(
    crs: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[rasterio.crs.CRS, NoneType]
```

Coordinate Reference System Coordinates Param.

    
### RescalingParams

```python3
def RescalingParams(
    rescale: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
) -> Union[List[Tuple[float, ...]], NoneType]
```

Min/Max data Rescaling

    
### create_colormap_dependency

```python3
def create_colormap_dependency(
    cmap: rio_tiler.colormap.ColorMaps
) -> Callable
```

Create Colormap Dependency.

## Classes

### AssetsBidxExprParams

```python3
class AssetsBidxExprParams(
    indexes: typing_extensions.Annotated[Union[List[int], NoneType], Query(PydanticUndefined)] = None,
    assets: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None,
    expression: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None,
    asset_indexes: typing_extensions.Annotated[Union[Sequence[str], NoneType], Query(PydanticUndefined)] = None,
    asset_as_band: typing_extensions.Annotated[Union[bool, NoneType], Query(PydanticUndefined)] = None
)
```

Assets, Expression and Asset's band Indexes parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.AssetsParams
* titiler.core.dependencies.BidxParams
* titiler.core.dependencies.DefaultDependency

#### Descendants

* titiler.core.dependencies.AssetsBidxExprParamsOptional

#### Class variables

```python3
asset_as_band
```

```python3
asset_indexes
```

```python3
assets
```

```python3
expression
```

```python3
indexes
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### AssetsBidxExprParamsOptional

```python3
class AssetsBidxExprParamsOptional(
    indexes: typing_extensions.Annotated[Union[List[int], NoneType], Query(PydanticUndefined)] = None,
    assets: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None,
    expression: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None,
    asset_indexes: typing_extensions.Annotated[Union[Sequence[str], NoneType], Query(PydanticUndefined)] = None,
    asset_as_band: typing_extensions.Annotated[Union[bool, NoneType], Query(PydanticUndefined)] = None
)
```

Assets, Expression and Asset's band Indexes parameters but with no requirement.

#### Ancestors (in MRO)

* titiler.core.dependencies.AssetsBidxExprParams
* titiler.core.dependencies.AssetsParams
* titiler.core.dependencies.BidxParams
* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
asset_as_band
```

```python3
asset_indexes
```

```python3
assets
```

```python3
expression
```

```python3
indexes
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### AssetsBidxParams

```python3
class AssetsBidxParams(
    indexes: typing_extensions.Annotated[Union[List[int], NoneType], Query(PydanticUndefined)] = None,
    assets: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None,
    asset_indexes: typing_extensions.Annotated[Union[Sequence[str], NoneType], Query(PydanticUndefined)] = None,
    asset_expression: typing_extensions.Annotated[Union[Sequence[str], NoneType], Query(PydanticUndefined)] = None
)
```

Assets, Asset's band Indexes and Asset's band Expression parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.AssetsParams
* titiler.core.dependencies.BidxParams
* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
asset_expression
```

```python3
asset_indexes
```

```python3
assets
```

```python3
indexes
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### AssetsParams

```python3
class AssetsParams(
    assets: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
)
```

Assets parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Descendants

* titiler.core.dependencies.AssetsBidxExprParams
* titiler.core.dependencies.AssetsBidxParams

#### Class variables

```python3
assets
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### BandsExprParams

```python3
class BandsExprParams(
    bands: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None,
    expression: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

Band names and Expression parameters (Band or Expression required).

#### Ancestors (in MRO)

* titiler.core.dependencies.ExpressionParams
* titiler.core.dependencies.BandsParams
* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
bands
```

```python3
expression
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### BandsExprParamsOptional

```python3
class BandsExprParamsOptional(
    bands: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None,
    expression: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

Optional Band names and Expression parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.ExpressionParams
* titiler.core.dependencies.BandsParams
* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
bands
```

```python3
expression
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### BandsParams

```python3
class BandsParams(
    bands: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
)
```

Band names parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Descendants

* titiler.core.dependencies.BandsExprParamsOptional
* titiler.core.dependencies.BandsExprParams

#### Class variables

```python3
bands
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### BidxExprParams

```python3
class BidxExprParams(
    indexes: typing_extensions.Annotated[Union[List[int], NoneType], Query(PydanticUndefined)] = None,
    expression: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

Band Indexes and Expression parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.ExpressionParams
* titiler.core.dependencies.BidxParams
* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
expression
```

```python3
indexes
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### BidxParams

```python3
class BidxParams(
    indexes: typing_extensions.Annotated[Union[List[int], NoneType], Query(PydanticUndefined)] = None
)
```

Band Indexes parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Descendants

* titiler.core.dependencies.BidxExprParams
* titiler.core.dependencies.AssetsBidxExprParams
* titiler.core.dependencies.AssetsBidxParams

#### Class variables

```python3
indexes
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### DatasetParams

```python3
class DatasetParams(
    nodata: typing_extensions.Annotated[Union[str, int, float, NoneType], Query(PydanticUndefined)] = None,
    unscale: typing_extensions.Annotated[bool, Query(PydanticUndefined)] = False,
    resampling_method: typing_extensions.Annotated[Literal['nearest', 'bilinear', 'cubic', 'cubic_spline', 'lanczos', 'average', 'mode', 'gauss', 'rms'], Query(PydanticUndefined)] = 'nearest',
    reproject_method: typing_extensions.Annotated[Literal['nearest', 'bilinear', 'cubic', 'cubic_spline', 'lanczos', 'average', 'mode', 'sum', 'rms'], Query(PydanticUndefined)] = 'nearest'
)
```

Low level WarpedVRT Optional parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
nodata
```

```python3
reproject_method
```

```python3
resampling_method
```

```python3
unscale
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### DefaultDependency

```python3
class DefaultDependency(
    
)
```

Dataclass with dict unpacking

#### Descendants

* titiler.core.dependencies.BidxParams
* titiler.core.dependencies.ExpressionParams
* titiler.core.dependencies.AssetsParams
* titiler.core.dependencies.BandsParams
* titiler.core.dependencies.PreviewParams
* titiler.core.dependencies.PartFeatureParams
* titiler.core.dependencies.DatasetParams
* titiler.core.dependencies.ImageRenderingParams
* titiler.core.dependencies.StatisticsParams
* titiler.core.dependencies.HistogramParams
* titiler.core.dependencies.TileParams

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### ExpressionParams

```python3
class ExpressionParams(
    expression: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

Expression parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Descendants

* titiler.core.dependencies.BidxExprParams
* titiler.core.dependencies.BandsExprParamsOptional
* titiler.core.dependencies.BandsExprParams

#### Class variables

```python3
expression
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### HistogramParams

```python3
class HistogramParams(
    bins: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None,
    range: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

Numpy Histogram options.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
bins
```

```python3
range
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### ImageRenderingParams

```python3
class ImageRenderingParams(
    add_mask: typing_extensions.Annotated[bool, Query(PydanticUndefined)] = True
)
```

Image Rendering options.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
add_mask
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### PartFeatureParams

```python3
class PartFeatureParams(
    max_size: typing_extensions.Annotated[Union[int, NoneType], 'Maximum image size to read onto.'] = None,
    height: typing_extensions.Annotated[Union[int, NoneType], 'Force output image height.'] = None,
    width: typing_extensions.Annotated[Union[int, NoneType], 'Force output image width.'] = None
)
```

Common parameters for bbox and feature.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
height
```

```python3
max_size
```

```python3
width
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### PreviewParams

```python3
class PreviewParams(
    max_size: typing_extensions.Annotated[int, 'Maximum image size to read onto.'] = 1024,
    height: typing_extensions.Annotated[Union[int, NoneType], 'Force output image height.'] = None,
    width: typing_extensions.Annotated[Union[int, NoneType], 'Force output image width.'] = None
)
```

Common Preview parameters.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
height
```

```python3
max_size
```

```python3
width
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### StatisticsParams

```python3
class StatisticsParams(
    categorical: typing_extensions.Annotated[bool, Query(PydanticUndefined)] = False,
    categories: typing_extensions.Annotated[Union[List[Union[float, int]], NoneType], Query(PydanticUndefined)] = None,
    percentiles: typing_extensions.Annotated[Union[List[int], NoneType], Query(PydanticUndefined)] = None
)
```

Statistics options.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
categorical
```

```python3
categories
```

```python3
percentiles
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.

### TileParams

```python3
class TileParams(
    buffer: typing_extensions.Annotated[Union[float, NoneType], Query(PydanticUndefined)] = None,
    padding: typing_extensions.Annotated[Union[int, NoneType], Query(PydanticUndefined)] = None
)
```

Tile options.

#### Ancestors (in MRO)

* titiler.core.dependencies.DefaultDependency

#### Class variables

```python3
buffer
```

```python3
padding
```

#### Methods

    
#### keys

```python3
def keys(
    self
)
```

Return Keys.