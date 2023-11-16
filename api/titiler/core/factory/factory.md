# Module titiler.core.factory

TiTiler Router factories.

## Variables

```python3
DEFAULT_TEMPLATES
```

```python3
WGS84_CRS
```

```python3
img_endpoint_params
```

## Classes

### AlgorithmFactory

```python3
class AlgorithmFactory(
    supported_algorithm: titiler.core.algorithm.Algorithms = Algorithms(data={'hillshade': <class 'titiler.core.algorithm.dem.HillShade'>, 'contours': <class 'titiler.core.algorithm.dem.Contours'>, 'normalizedIndex': <class 'titiler.core.algorithm.index.NormalizedIndex'>, 'terrarium': <class 'titiler.core.algorithm.dem.Terrarium'>, 'terrainrgb': <class 'titiler.core.algorithm.dem.TerrainRGB'>}),
    router: fastapi.routing.APIRouter = <factory>
)
```

Algorithm endpoints Factory.

#### Class variables

```python3
supported_algorithm
```

### BaseTilerFactory

```python3
class BaseTilerFactory(
    reader: Type[rio_tiler.io.base.BaseReader],
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Callable[..., Any] = <function DatasetPathParams at 0x7fe422f0f040>,
    layer_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.BidxExprParams'>,
    dataset_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DatasetParams'>,
    process_dependency: Callable[..., Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]] = <function Algorithms.dependency.<locals>.post_process at 0x7fe41d2dbd30>,
    rescale_dependency: Callable[..., Union[List[Tuple[float, ...]], NoneType]] = <function RescalingParams at 0x7fe422b9a160>,
    color_formula_dependency: Callable[..., Union[str, NoneType]] = <function ColorFormulaParams at 0x7fe41d5d5040>,
    colormap_dependency: Callable[..., Union[Dict[int, Tuple[int, int, int, int]], Sequence[Tuple[Tuple[Union[float, int], Union[float, int]], Tuple[int, int, int, int]]], NoneType]] = <function create_colormap_dependency.<locals>.deps at 0x7fe42742a040>,
    render_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.ImageRenderingParams'>,
    reader_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DefaultDependency'>,
    environment_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7fe41d2ecc10>,
    supported_tms: morecantile.defaults.TileMatrixSets = TileMatrixSets(tms={'CDB1GlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CDB1GlobalGrid.json'), 'CanadianNAD83_LCC': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CanadianNAD83_LCC.json'), 'EuropeanETRS89_LAEAQuad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/EuropeanETRS89_LAEAQuad.json'), 'GNOSISGlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/GNOSISGlobalGrid.json'), 'LINZAntarticaMapTilegrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/LINZAntarticaMapTilegrid.json'), 'NZTM2000Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/NZTM2000Quad.json'), 'UPSAntarcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSAntarcticWGS84Quad.json'), 'UPSArcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSArcticWGS84Quad.json'), 'UTM31WGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UTM31WGS84Quad.json'), 'WGS1984Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WGS1984Quad.json'), 'WebMercatorQuad': <TileMatrixSet title='Google Maps Compatible for the World' id='WebMercatorQuad' crs='http://www.opengis.net/def/crs/EPSG/0/3857>, 'WorldCRS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldCRS84Quad.json'), 'WorldMercatorWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldMercatorWGS84Quad.json')}),
    default_tms: str = 'WebMercatorQuad',
    router_prefix: str = '',
    optional_headers: List[titiler.core.resources.enums.OptionalHeader] = <factory>,
    route_dependencies: List[Tuple[List[titiler.core.routing.EndpointScope], List[fastapi.params.Depends]]] = <factory>,
    extensions: List[titiler.core.factory.FactoryExtension] = <factory>,
    templates: starlette.templating.Jinja2Templates = <starlette.templating.Jinja2Templates object at 0x7fe41d565130>
)
```

BaseTiler Factory.

Abstract Base Class which defines most inputs used by dynamic tiler.
#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| reader | rio_tiler.io.base.BaseReader | A rio-tiler reader (e.g Reader). | None |
| router | fastapi.APIRouter | Application router to register endpoints to. | None |
| path_dependency | Callable | Endpoint dependency defining `path` to pass to the reader init. | None |
| dataset_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining dataset overwriting options (e.g nodata). | None |
| layer_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining dataset indexes/bands/assets options. | None |
| render_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining image rendering options (e.g add_mask). | None |
| colormap_dependency | Callable | Endpoint dependency defining ColorMap options (e.g colormap_name). | None |
| process_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining image post-processing options (e.g rescaling, color-formula). | None |
| tms_dependency | Callable | Endpoint dependency defining TileMatrixSet to use. | None |
| reader_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining BaseReader options. | None |
| environment_dependency | Callable | Endpoint dependency to define GDAL environment at runtime. | None |
| router_prefix | str | prefix where the router will be mounted in the application. | None |
| optional_headers | sequence of titiler.core.resources.enums.OptionalHeader | additional headers to return with the response. | None |

#### Descendants

* titiler.core.factory.TilerFactory

#### Class variables

```python3
dataset_dependency
```

```python3
default_tms
```

```python3
layer_dependency
```

```python3
reader_dependency
```

```python3
render_dependency
```

```python3
router_prefix
```

```python3
supported_tms
```

```python3
templates
```

#### Methods

    
#### add_route_dependencies

```python3
def add_route_dependencies(
    self,
    *,
    scopes: List[titiler.core.routing.EndpointScope],
    dependencies=typing.List[fastapi.params.Depends]
)
```

Add dependencies to routes.

Allows a developer to add dependencies to a route after the route has been defined.

    
#### color_formula_dependency

```python3
def color_formula_dependency(
    color_formula: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[str, NoneType]
```

ColorFormula Parameter.

    
#### colormap_dependency

```python3
def colormap_dependency(
    colormap_name: typing_extensions.Annotated[Literal['oranges', 'gist_earth', 'gray', 'dense', 'purples', 'puor', 'gnuplot2_r', 'spectral', 'rain', 'cfastie', 'tab20_r', 'curl', 'solar_r', 'terrain', 'afmhot_r', 'cubehelix', 'jet_r', 'magma_r', 'gist_yarg', 'tab20', 'rdgy', 'afmhot', 'gist_earth_r', 'rdgy_r', 'viridis_r', 'reds_r', 'binary_r', 'flag', 'turbid', 'accent', 'thermal', 'pink', 'plasma', 'balance_r', 'cool', 'pubugn_r', 'set3', 'gnuplot', 'ocean', 'copper_r', 'bwr', 'matter_r', 'turbid_r', 'gnuplot_r', 'amp', 'orrd', 'tab20b_r', 'algae', 'rdylgn_r', 'gist_gray_r', 'prism_r', 'ocean_r', 'autumn_r', 'piyg', 'tarn', 'greys_r', 'set2_r', 'winter_r', 'brbg_r', 'gist_rainbow', 'pubu', 'ylgn_r', 'gist_heat_r', 'seismic', 'dark2', 'hot', 'rdylgn', 'oranges_r', 'puor_r', 'bwr_r', 'ylorrd_r', 'inferno', 'speed', 'set3_r', 'ylgnbu', 'balance', 'rdylbu', 'greens', 'ylgnbu_r', 'topo_r', 'wistia', 'prgn_r', 'bupu', 'jet', 'gist_gray', 'ylgn', 'tab10_r', 'seismic_r', 'twilight', 'tab20c_r', 'hsv_r', 'ylorbr_r', 'orrd_r', 'gist_heat', 'blues', 'gist_ncar', 'coolwarm_r', 'paired', 'wistia_r', 'purd_r', 'autumn', 'greys', 'diff', 'topo', 'tab20b', 'oxy_r', 'purples_r', 'diff_r', 'rdylbu_r', 'tempo', 'tab20c', 'gist_stern_r', 'prism', 'tarn_r', 'gnuplot2', 'set1_r', 'bugn_r', 'purd', 'cmrmap_r', 'cividis_r', 'spectral_r', 'dark2_r', 'pastel1_r', 'inferno_r', 'twilight_shifted_r', 'delta', 'pubu_r', 'terrain_r', 'ice', 'brbg', 'viridis', 'hot_r', 'rainbow_r', 'haline', 'rdpu', 'cool_r', 'magma', 'tab10', 'solar', 'twilight_shifted', 'gist_yarg_r', 'coolwarm', 'oxy', 'amp_r', 'tempo_r', 'flag_r', 'brg', 'rdpu_r', 'pubugn', 'bone_r', 'deep', 'winter', 'dense_r', 'gnbu', 'blues_r', 'summer_r', 'cubehelix_r', 'speed_r', 'cividis', 'hsv', 'gray_r', 'piyg_r', 'binary', 'plasma_r', 'gist_rainbow_r', 'pastel1', 'set1', 'nipy_spectral_r', 'gnbu_r', 'prgn', 'copper', 'rplumbo', 'thermal_r', 'pastel2', 'rdbu', 'spring_r', 'delta_r', 'set2', 'rainbow', 'bugn', 'greens_r', 'brg_r', 'reds', 'turbo', 'ylorrd', 'curl_r', 'gist_stern', 'schwarzwald', 'phase', 'rain_r', 'matter', 'deep_r', 'ice_r', 'paired_r', 'cmrmap', 'bupu_r', 'pastel2_r', 'spring', 'phase_r', 'algae_r', 'turbo_r', 'rdbu_r', 'nipy_spectral', 'bone', 'ylorbr', 'pink_r', 'gist_ncar_r', 'twilight_r', 'accent_r', 'summer', 'haline_r'], Query(PydanticUndefined)] = None,
    colormap: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

    
#### environment_dependency

```python3
def environment_dependency(
    
)
```

    
#### path_dependency

```python3
def path_dependency(
    url: typing_extensions.Annotated[str, Query(PydanticUndefined)]
) -> str
```

Create dataset path from args

    
#### process_dependency

```python3
def process_dependency(
    algorithm: typing_extensions.Annotated[Literal['hillshade', 'contours', 'normalizedIndex', 'terrarium', 'terrainrgb'], Query(PydanticUndefined)] = None,
    algorithm_params: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]
```

Data Post-Processing options.

    
#### register_routes

```python3
def register_routes(
    self
)
```

Register Tiler Routes.

    
#### rescale_dependency

```python3
def rescale_dependency(
    rescale: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
) -> Union[List[Tuple[float, ...]], NoneType]
```

Min/Max data Rescaling

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

Return full url (with prefix) for a specific endpoint.

### FactoryExtension

```python3
class FactoryExtension(
    
)
```

Factory Extension.

#### Methods

    
#### register

```python3
def register(
    self,
    factory: 'BaseTilerFactory'
)
```

Register extension to the factory.

### MultiBandTilerFactory

```python3
class MultiBandTilerFactory(
    reader: Type[rio_tiler.io.base.MultiBandReader] = <class 'rio_tiler.io.rasterio.Reader'>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Callable[..., Any] = <function DatasetPathParams at 0x7fe422f0f040>,
    layer_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.BandsExprParams'>,
    dataset_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DatasetParams'>,
    process_dependency: Callable[..., Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]] = <function Algorithms.dependency.<locals>.post_process at 0x7fe41d2dbd30>,
    rescale_dependency: Callable[..., Union[List[Tuple[float, ...]], NoneType]] = <function RescalingParams at 0x7fe422b9a160>,
    color_formula_dependency: Callable[..., Union[str, NoneType]] = <function ColorFormulaParams at 0x7fe41d5d5040>,
    colormap_dependency: Callable[..., Union[Dict[int, Tuple[int, int, int, int]], Sequence[Tuple[Tuple[Union[float, int], Union[float, int]], Tuple[int, int, int, int]]], NoneType]] = <function create_colormap_dependency.<locals>.deps at 0x7fe42742a040>,
    render_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.ImageRenderingParams'>,
    reader_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DefaultDependency'>,
    environment_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7fe41d2ecc10>,
    supported_tms: morecantile.defaults.TileMatrixSets = TileMatrixSets(tms={'CDB1GlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CDB1GlobalGrid.json'), 'CanadianNAD83_LCC': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CanadianNAD83_LCC.json'), 'EuropeanETRS89_LAEAQuad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/EuropeanETRS89_LAEAQuad.json'), 'GNOSISGlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/GNOSISGlobalGrid.json'), 'LINZAntarticaMapTilegrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/LINZAntarticaMapTilegrid.json'), 'NZTM2000Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/NZTM2000Quad.json'), 'UPSAntarcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSAntarcticWGS84Quad.json'), 'UPSArcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSArcticWGS84Quad.json'), 'UTM31WGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UTM31WGS84Quad.json'), 'WGS1984Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WGS1984Quad.json'), 'WebMercatorQuad': <TileMatrixSet title='Google Maps Compatible for the World' id='WebMercatorQuad' crs='http://www.opengis.net/def/crs/EPSG/0/3857>, 'WorldCRS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldCRS84Quad.json'), 'WorldMercatorWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldMercatorWGS84Quad.json')}),
    default_tms: str = 'WebMercatorQuad',
    router_prefix: str = '',
    optional_headers: List[titiler.core.resources.enums.OptionalHeader] = <factory>,
    route_dependencies: List[Tuple[List[titiler.core.routing.EndpointScope], List[fastapi.params.Depends]]] = <factory>,
    extensions: List[titiler.core.factory.FactoryExtension] = <factory>,
    templates: starlette.templating.Jinja2Templates = <starlette.templating.Jinja2Templates object at 0x7fe41d565130>,
    stats_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.StatisticsParams'>,
    histogram_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.HistogramParams'>,
    img_preview_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.PreviewParams'>,
    img_part_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.PartFeatureParams'>,
    tile_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.TileParams'>,
    add_preview: bool = True,
    add_part: bool = True,
    add_viewer: bool = True,
    bands_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.BandsParams'>
)
```

Custom Tiler Factory for MultiBandReader classes.

Note:
    To be able to use the rio_tiler.io.MultiBandReader we need to be able to pass a `bands`
    argument to most of its methods. By using the `BandsExprParams` for the `layer_dependency`, the
    .tile(), .point(), .preview() and the .part() methods will receive bands or expression arguments.

    The rio_tiler.io.MultiBandReader  `.info()` and `.metadata()` have `bands` as
    a requirement arguments (https://github.com/cogeotiff/rio-tiler/blob/main/rio_tiler/io/base.py#L775).
    This means we have to update the /info and /metadata endpoints in order to add the `bands` dependency.

    For implementation example see https://github.com/developmentseed/titiler-pds

#### Ancestors (in MRO)

* titiler.core.factory.TilerFactory
* titiler.core.factory.BaseTilerFactory

#### Class variables

```python3
add_part
```

```python3
add_preview
```

```python3
add_viewer
```

```python3
bands_dependency
```

```python3
dataset_dependency
```

```python3
default_tms
```

```python3
histogram_dependency
```

```python3
img_part_dependency
```

```python3
img_preview_dependency
```

```python3
layer_dependency
```

```python3
reader
```

```python3
reader_dependency
```

```python3
render_dependency
```

```python3
router_prefix
```

```python3
stats_dependency
```

```python3
supported_tms
```

```python3
templates
```

```python3
tile_dependency
```

#### Methods

    
#### add_route_dependencies

```python3
def add_route_dependencies(
    self,
    *,
    scopes: List[titiler.core.routing.EndpointScope],
    dependencies=typing.List[fastapi.params.Depends]
)
```

Add dependencies to routes.

Allows a developer to add dependencies to a route after the route has been defined.

    
#### bounds

```python3
def bounds(
    self
)
```

Register /bounds endpoint.

    
#### color_formula_dependency

```python3
def color_formula_dependency(
    color_formula: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[str, NoneType]
```

ColorFormula Parameter.

    
#### colormap_dependency

```python3
def colormap_dependency(
    colormap_name: typing_extensions.Annotated[Literal['oranges', 'gist_earth', 'gray', 'dense', 'purples', 'puor', 'gnuplot2_r', 'spectral', 'rain', 'cfastie', 'tab20_r', 'curl', 'solar_r', 'terrain', 'afmhot_r', 'cubehelix', 'jet_r', 'magma_r', 'gist_yarg', 'tab20', 'rdgy', 'afmhot', 'gist_earth_r', 'rdgy_r', 'viridis_r', 'reds_r', 'binary_r', 'flag', 'turbid', 'accent', 'thermal', 'pink', 'plasma', 'balance_r', 'cool', 'pubugn_r', 'set3', 'gnuplot', 'ocean', 'copper_r', 'bwr', 'matter_r', 'turbid_r', 'gnuplot_r', 'amp', 'orrd', 'tab20b_r', 'algae', 'rdylgn_r', 'gist_gray_r', 'prism_r', 'ocean_r', 'autumn_r', 'piyg', 'tarn', 'greys_r', 'set2_r', 'winter_r', 'brbg_r', 'gist_rainbow', 'pubu', 'ylgn_r', 'gist_heat_r', 'seismic', 'dark2', 'hot', 'rdylgn', 'oranges_r', 'puor_r', 'bwr_r', 'ylorrd_r', 'inferno', 'speed', 'set3_r', 'ylgnbu', 'balance', 'rdylbu', 'greens', 'ylgnbu_r', 'topo_r', 'wistia', 'prgn_r', 'bupu', 'jet', 'gist_gray', 'ylgn', 'tab10_r', 'seismic_r', 'twilight', 'tab20c_r', 'hsv_r', 'ylorbr_r', 'orrd_r', 'gist_heat', 'blues', 'gist_ncar', 'coolwarm_r', 'paired', 'wistia_r', 'purd_r', 'autumn', 'greys', 'diff', 'topo', 'tab20b', 'oxy_r', 'purples_r', 'diff_r', 'rdylbu_r', 'tempo', 'tab20c', 'gist_stern_r', 'prism', 'tarn_r', 'gnuplot2', 'set1_r', 'bugn_r', 'purd', 'cmrmap_r', 'cividis_r', 'spectral_r', 'dark2_r', 'pastel1_r', 'inferno_r', 'twilight_shifted_r', 'delta', 'pubu_r', 'terrain_r', 'ice', 'brbg', 'viridis', 'hot_r', 'rainbow_r', 'haline', 'rdpu', 'cool_r', 'magma', 'tab10', 'solar', 'twilight_shifted', 'gist_yarg_r', 'coolwarm', 'oxy', 'amp_r', 'tempo_r', 'flag_r', 'brg', 'rdpu_r', 'pubugn', 'bone_r', 'deep', 'winter', 'dense_r', 'gnbu', 'blues_r', 'summer_r', 'cubehelix_r', 'speed_r', 'cividis', 'hsv', 'gray_r', 'piyg_r', 'binary', 'plasma_r', 'gist_rainbow_r', 'pastel1', 'set1', 'nipy_spectral_r', 'gnbu_r', 'prgn', 'copper', 'rplumbo', 'thermal_r', 'pastel2', 'rdbu', 'spring_r', 'delta_r', 'set2', 'rainbow', 'bugn', 'greens_r', 'brg_r', 'reds', 'turbo', 'ylorrd', 'curl_r', 'gist_stern', 'schwarzwald', 'phase', 'rain_r', 'matter', 'deep_r', 'ice_r', 'paired_r', 'cmrmap', 'bupu_r', 'pastel2_r', 'spring', 'phase_r', 'algae_r', 'turbo_r', 'rdbu_r', 'nipy_spectral', 'bone', 'ylorbr', 'pink_r', 'gist_ncar_r', 'twilight_r', 'accent_r', 'summer', 'haline_r'], Query(PydanticUndefined)] = None,
    colormap: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

    
#### environment_dependency

```python3
def environment_dependency(
    
)
```

    
#### info

```python3
def info(
    self
)
```

Register /info endpoint.

    
#### map_viewer

```python3
def map_viewer(
    self
)
```

Register /map endpoint.

    
#### part

```python3
def part(
    self
)
```

Register /bbox and `/feature` endpoints.

    
#### path_dependency

```python3
def path_dependency(
    url: typing_extensions.Annotated[str, Query(PydanticUndefined)]
) -> str
```

Create dataset path from args

    
#### point

```python3
def point(
    self
)
```

Register /point endpoints.

    
#### preview

```python3
def preview(
    self
)
```

Register /preview endpoint.

    
#### process_dependency

```python3
def process_dependency(
    algorithm: typing_extensions.Annotated[Literal['hillshade', 'contours', 'normalizedIndex', 'terrarium', 'terrainrgb'], Query(PydanticUndefined)] = None,
    algorithm_params: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]
```

Data Post-Processing options.

    
#### register_routes

```python3
def register_routes(
    self
)
```

This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialization.

    
#### rescale_dependency

```python3
def rescale_dependency(
    rescale: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
) -> Union[List[Tuple[float, ...]], NoneType]
```

Min/Max data Rescaling

    
#### statistics

```python3
def statistics(
    self
)
```

add statistics endpoints.

    
#### tile

```python3
def tile(
    self
)
```

Register /tiles endpoint.

    
#### tilejson

```python3
def tilejson(
    self
)
```

Register /tilejson.json endpoint.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

Return full url (with prefix) for a specific endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

Register /wmts endpoint.

### MultiBaseTilerFactory

```python3
class MultiBaseTilerFactory(
    reader: Type[rio_tiler.io.base.MultiBaseReader] = <class 'rio_tiler.io.rasterio.Reader'>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Callable[..., Any] = <function DatasetPathParams at 0x7fe422f0f040>,
    layer_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.AssetsBidxExprParams'>,
    dataset_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DatasetParams'>,
    process_dependency: Callable[..., Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]] = <function Algorithms.dependency.<locals>.post_process at 0x7fe41d2dbd30>,
    rescale_dependency: Callable[..., Union[List[Tuple[float, ...]], NoneType]] = <function RescalingParams at 0x7fe422b9a160>,
    color_formula_dependency: Callable[..., Union[str, NoneType]] = <function ColorFormulaParams at 0x7fe41d5d5040>,
    colormap_dependency: Callable[..., Union[Dict[int, Tuple[int, int, int, int]], Sequence[Tuple[Tuple[Union[float, int], Union[float, int]], Tuple[int, int, int, int]]], NoneType]] = <function create_colormap_dependency.<locals>.deps at 0x7fe42742a040>,
    render_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.ImageRenderingParams'>,
    reader_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DefaultDependency'>,
    environment_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7fe41d2ecc10>,
    supported_tms: morecantile.defaults.TileMatrixSets = TileMatrixSets(tms={'CDB1GlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CDB1GlobalGrid.json'), 'CanadianNAD83_LCC': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CanadianNAD83_LCC.json'), 'EuropeanETRS89_LAEAQuad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/EuropeanETRS89_LAEAQuad.json'), 'GNOSISGlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/GNOSISGlobalGrid.json'), 'LINZAntarticaMapTilegrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/LINZAntarticaMapTilegrid.json'), 'NZTM2000Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/NZTM2000Quad.json'), 'UPSAntarcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSAntarcticWGS84Quad.json'), 'UPSArcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSArcticWGS84Quad.json'), 'UTM31WGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UTM31WGS84Quad.json'), 'WGS1984Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WGS1984Quad.json'), 'WebMercatorQuad': <TileMatrixSet title='Google Maps Compatible for the World' id='WebMercatorQuad' crs='http://www.opengis.net/def/crs/EPSG/0/3857>, 'WorldCRS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldCRS84Quad.json'), 'WorldMercatorWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldMercatorWGS84Quad.json')}),
    default_tms: str = 'WebMercatorQuad',
    router_prefix: str = '',
    optional_headers: List[titiler.core.resources.enums.OptionalHeader] = <factory>,
    route_dependencies: List[Tuple[List[titiler.core.routing.EndpointScope], List[fastapi.params.Depends]]] = <factory>,
    extensions: List[titiler.core.factory.FactoryExtension] = <factory>,
    templates: starlette.templating.Jinja2Templates = <starlette.templating.Jinja2Templates object at 0x7fe41d565130>,
    stats_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.StatisticsParams'>,
    histogram_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.HistogramParams'>,
    img_preview_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.PreviewParams'>,
    img_part_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.PartFeatureParams'>,
    tile_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.TileParams'>,
    add_preview: bool = True,
    add_part: bool = True,
    add_viewer: bool = True,
    assets_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.AssetsParams'>
)
```

Custom Tiler Factory for MultiBaseReader classes.

Note:
    To be able to use the rio_tiler.io.MultiBaseReader we need to be able to pass a `assets`
    argument to most of its methods. By using the `AssetsBidxExprParams` for the `layer_dependency`, the
    .tile(), .point(), .preview() and the .part() methods will receive assets, expression or indexes arguments.

    The rio_tiler.io.MultiBaseReader  `.info()` and `.metadata()` have `assets` as
    a requirement arguments (https://github.com/cogeotiff/rio-tiler/blob/main/rio_tiler/io/base.py#L365).
    This means we have to update the /info and /metadata endpoints in order to add the `assets` dependency.

#### Ancestors (in MRO)

* titiler.core.factory.TilerFactory
* titiler.core.factory.BaseTilerFactory

#### Class variables

```python3
add_part
```

```python3
add_preview
```

```python3
add_viewer
```

```python3
assets_dependency
```

```python3
dataset_dependency
```

```python3
default_tms
```

```python3
histogram_dependency
```

```python3
img_part_dependency
```

```python3
img_preview_dependency
```

```python3
layer_dependency
```

```python3
reader
```

```python3
reader_dependency
```

```python3
render_dependency
```

```python3
router_prefix
```

```python3
stats_dependency
```

```python3
supported_tms
```

```python3
templates
```

```python3
tile_dependency
```

#### Methods

    
#### add_route_dependencies

```python3
def add_route_dependencies(
    self,
    *,
    scopes: List[titiler.core.routing.EndpointScope],
    dependencies=typing.List[fastapi.params.Depends]
)
```

Add dependencies to routes.

Allows a developer to add dependencies to a route after the route has been defined.

    
#### bounds

```python3
def bounds(
    self
)
```

Register /bounds endpoint.

    
#### color_formula_dependency

```python3
def color_formula_dependency(
    color_formula: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[str, NoneType]
```

ColorFormula Parameter.

    
#### colormap_dependency

```python3
def colormap_dependency(
    colormap_name: typing_extensions.Annotated[Literal['oranges', 'gist_earth', 'gray', 'dense', 'purples', 'puor', 'gnuplot2_r', 'spectral', 'rain', 'cfastie', 'tab20_r', 'curl', 'solar_r', 'terrain', 'afmhot_r', 'cubehelix', 'jet_r', 'magma_r', 'gist_yarg', 'tab20', 'rdgy', 'afmhot', 'gist_earth_r', 'rdgy_r', 'viridis_r', 'reds_r', 'binary_r', 'flag', 'turbid', 'accent', 'thermal', 'pink', 'plasma', 'balance_r', 'cool', 'pubugn_r', 'set3', 'gnuplot', 'ocean', 'copper_r', 'bwr', 'matter_r', 'turbid_r', 'gnuplot_r', 'amp', 'orrd', 'tab20b_r', 'algae', 'rdylgn_r', 'gist_gray_r', 'prism_r', 'ocean_r', 'autumn_r', 'piyg', 'tarn', 'greys_r', 'set2_r', 'winter_r', 'brbg_r', 'gist_rainbow', 'pubu', 'ylgn_r', 'gist_heat_r', 'seismic', 'dark2', 'hot', 'rdylgn', 'oranges_r', 'puor_r', 'bwr_r', 'ylorrd_r', 'inferno', 'speed', 'set3_r', 'ylgnbu', 'balance', 'rdylbu', 'greens', 'ylgnbu_r', 'topo_r', 'wistia', 'prgn_r', 'bupu', 'jet', 'gist_gray', 'ylgn', 'tab10_r', 'seismic_r', 'twilight', 'tab20c_r', 'hsv_r', 'ylorbr_r', 'orrd_r', 'gist_heat', 'blues', 'gist_ncar', 'coolwarm_r', 'paired', 'wistia_r', 'purd_r', 'autumn', 'greys', 'diff', 'topo', 'tab20b', 'oxy_r', 'purples_r', 'diff_r', 'rdylbu_r', 'tempo', 'tab20c', 'gist_stern_r', 'prism', 'tarn_r', 'gnuplot2', 'set1_r', 'bugn_r', 'purd', 'cmrmap_r', 'cividis_r', 'spectral_r', 'dark2_r', 'pastel1_r', 'inferno_r', 'twilight_shifted_r', 'delta', 'pubu_r', 'terrain_r', 'ice', 'brbg', 'viridis', 'hot_r', 'rainbow_r', 'haline', 'rdpu', 'cool_r', 'magma', 'tab10', 'solar', 'twilight_shifted', 'gist_yarg_r', 'coolwarm', 'oxy', 'amp_r', 'tempo_r', 'flag_r', 'brg', 'rdpu_r', 'pubugn', 'bone_r', 'deep', 'winter', 'dense_r', 'gnbu', 'blues_r', 'summer_r', 'cubehelix_r', 'speed_r', 'cividis', 'hsv', 'gray_r', 'piyg_r', 'binary', 'plasma_r', 'gist_rainbow_r', 'pastel1', 'set1', 'nipy_spectral_r', 'gnbu_r', 'prgn', 'copper', 'rplumbo', 'thermal_r', 'pastel2', 'rdbu', 'spring_r', 'delta_r', 'set2', 'rainbow', 'bugn', 'greens_r', 'brg_r', 'reds', 'turbo', 'ylorrd', 'curl_r', 'gist_stern', 'schwarzwald', 'phase', 'rain_r', 'matter', 'deep_r', 'ice_r', 'paired_r', 'cmrmap', 'bupu_r', 'pastel2_r', 'spring', 'phase_r', 'algae_r', 'turbo_r', 'rdbu_r', 'nipy_spectral', 'bone', 'ylorbr', 'pink_r', 'gist_ncar_r', 'twilight_r', 'accent_r', 'summer', 'haline_r'], Query(PydanticUndefined)] = None,
    colormap: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

    
#### environment_dependency

```python3
def environment_dependency(
    
)
```

    
#### info

```python3
def info(
    self
)
```

Register /info endpoint.

    
#### map_viewer

```python3
def map_viewer(
    self
)
```

Register /map endpoint.

    
#### part

```python3
def part(
    self
)
```

Register /bbox and `/feature` endpoints.

    
#### path_dependency

```python3
def path_dependency(
    url: typing_extensions.Annotated[str, Query(PydanticUndefined)]
) -> str
```

Create dataset path from args

    
#### point

```python3
def point(
    self
)
```

Register /point endpoints.

    
#### preview

```python3
def preview(
    self
)
```

Register /preview endpoint.

    
#### process_dependency

```python3
def process_dependency(
    algorithm: typing_extensions.Annotated[Literal['hillshade', 'contours', 'normalizedIndex', 'terrarium', 'terrainrgb'], Query(PydanticUndefined)] = None,
    algorithm_params: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]
```

Data Post-Processing options.

    
#### register_routes

```python3
def register_routes(
    self
)
```

This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialization.

    
#### rescale_dependency

```python3
def rescale_dependency(
    rescale: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
) -> Union[List[Tuple[float, ...]], NoneType]
```

Min/Max data Rescaling

    
#### statistics

```python3
def statistics(
    self
)
```

Register /statistics endpoint.

    
#### tile

```python3
def tile(
    self
)
```

Register /tiles endpoint.

    
#### tilejson

```python3
def tilejson(
    self
)
```

Register /tilejson.json endpoint.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

Return full url (with prefix) for a specific endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

Register /wmts endpoint.

### TMSFactory

```python3
class TMSFactory(
    supported_tms: morecantile.defaults.TileMatrixSets = TileMatrixSets(tms={'CDB1GlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CDB1GlobalGrid.json'), 'CanadianNAD83_LCC': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CanadianNAD83_LCC.json'), 'EuropeanETRS89_LAEAQuad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/EuropeanETRS89_LAEAQuad.json'), 'GNOSISGlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/GNOSISGlobalGrid.json'), 'LINZAntarticaMapTilegrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/LINZAntarticaMapTilegrid.json'), 'NZTM2000Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/NZTM2000Quad.json'), 'UPSAntarcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSAntarcticWGS84Quad.json'), 'UPSArcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSArcticWGS84Quad.json'), 'UTM31WGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UTM31WGS84Quad.json'), 'WGS1984Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WGS1984Quad.json'), 'WebMercatorQuad': <TileMatrixSet title='Google Maps Compatible for the World' id='WebMercatorQuad' crs='http://www.opengis.net/def/crs/EPSG/0/3857>, 'WorldCRS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldCRS84Quad.json'), 'WorldMercatorWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldMercatorWGS84Quad.json')}),
    router: fastapi.routing.APIRouter = <factory>,
    router_prefix: str = ''
)
```

TileMatrixSet endpoints Factory.

#### Class variables

```python3
router_prefix
```

```python3
supported_tms
```

#### Methods

    
#### register_routes

```python3
def register_routes(
    self
)
```

Register TMS endpoint routes.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

Return full url (with prefix) for a specific endpoint.

### TilerFactory

```python3
class TilerFactory(
    reader: Type[rio_tiler.io.base.BaseReader] = <class 'rio_tiler.io.rasterio.Reader'>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Callable[..., Any] = <function DatasetPathParams at 0x7fe422f0f040>,
    layer_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.BidxExprParams'>,
    dataset_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DatasetParams'>,
    process_dependency: Callable[..., Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]] = <function Algorithms.dependency.<locals>.post_process at 0x7fe41d2dbd30>,
    rescale_dependency: Callable[..., Union[List[Tuple[float, ...]], NoneType]] = <function RescalingParams at 0x7fe422b9a160>,
    color_formula_dependency: Callable[..., Union[str, NoneType]] = <function ColorFormulaParams at 0x7fe41d5d5040>,
    colormap_dependency: Callable[..., Union[Dict[int, Tuple[int, int, int, int]], Sequence[Tuple[Tuple[Union[float, int], Union[float, int]], Tuple[int, int, int, int]]], NoneType]] = <function create_colormap_dependency.<locals>.deps at 0x7fe42742a040>,
    render_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.ImageRenderingParams'>,
    reader_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DefaultDependency'>,
    environment_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7fe41d2ecc10>,
    supported_tms: morecantile.defaults.TileMatrixSets = TileMatrixSets(tms={'CDB1GlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CDB1GlobalGrid.json'), 'CanadianNAD83_LCC': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CanadianNAD83_LCC.json'), 'EuropeanETRS89_LAEAQuad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/EuropeanETRS89_LAEAQuad.json'), 'GNOSISGlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/GNOSISGlobalGrid.json'), 'LINZAntarticaMapTilegrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/LINZAntarticaMapTilegrid.json'), 'NZTM2000Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/NZTM2000Quad.json'), 'UPSAntarcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSAntarcticWGS84Quad.json'), 'UPSArcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSArcticWGS84Quad.json'), 'UTM31WGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UTM31WGS84Quad.json'), 'WGS1984Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WGS1984Quad.json'), 'WebMercatorQuad': <TileMatrixSet title='Google Maps Compatible for the World' id='WebMercatorQuad' crs='http://www.opengis.net/def/crs/EPSG/0/3857>, 'WorldCRS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldCRS84Quad.json'), 'WorldMercatorWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldMercatorWGS84Quad.json')}),
    default_tms: str = 'WebMercatorQuad',
    router_prefix: str = '',
    optional_headers: List[titiler.core.resources.enums.OptionalHeader] = <factory>,
    route_dependencies: List[Tuple[List[titiler.core.routing.EndpointScope], List[fastapi.params.Depends]]] = <factory>,
    extensions: List[titiler.core.factory.FactoryExtension] = <factory>,
    templates: starlette.templating.Jinja2Templates = <starlette.templating.Jinja2Templates object at 0x7fe41d565130>,
    stats_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.StatisticsParams'>,
    histogram_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.HistogramParams'>,
    img_preview_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.PreviewParams'>,
    img_part_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.PartFeatureParams'>,
    tile_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.TileParams'>,
    add_preview: bool = True,
    add_part: bool = True,
    add_viewer: bool = True
)
```

Tiler Factory.

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| reader | rio_tiler.io.base.BaseReader | A rio-tiler reader. Defaults to `rio_tiler.io.Reader`. | `rio_tiler.io.Reader` |
| stats_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining options for rio-tiler's statistics method. | None |
| histogram_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining options for numpy's histogram method. | None |
| img_preview_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining options for rio-tiler's preview method. | None |
| img_part_dependency | titiler.core.dependencies.DefaultDependency | Endpoint dependency defining options for rio-tiler's part/feature methods. | None |
| add_preview | bool | add `/preview` endpoints. Defaults to True. | True |
| add_part | bool | add `/bbox` and `/feature` endpoints. Defaults to True. | True |
| add_viewer | bool | add `/map` endpoints. Defaults to True. | True |

#### Ancestors (in MRO)

* titiler.core.factory.BaseTilerFactory

#### Descendants

* titiler.core.factory.MultiBaseTilerFactory
* titiler.core.factory.MultiBandTilerFactory

#### Class variables

```python3
add_part
```

```python3
add_preview
```

```python3
add_viewer
```

```python3
dataset_dependency
```

```python3
default_tms
```

```python3
histogram_dependency
```

```python3
img_part_dependency
```

```python3
img_preview_dependency
```

```python3
layer_dependency
```

```python3
reader
```

```python3
reader_dependency
```

```python3
render_dependency
```

```python3
router_prefix
```

```python3
stats_dependency
```

```python3
supported_tms
```

```python3
templates
```

```python3
tile_dependency
```

#### Methods

    
#### add_route_dependencies

```python3
def add_route_dependencies(
    self,
    *,
    scopes: List[titiler.core.routing.EndpointScope],
    dependencies=typing.List[fastapi.params.Depends]
)
```

Add dependencies to routes.

Allows a developer to add dependencies to a route after the route has been defined.

    
#### bounds

```python3
def bounds(
    self
)
```

Register /bounds endpoint.

    
#### color_formula_dependency

```python3
def color_formula_dependency(
    color_formula: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[str, NoneType]
```

ColorFormula Parameter.

    
#### colormap_dependency

```python3
def colormap_dependency(
    colormap_name: typing_extensions.Annotated[Literal['oranges', 'gist_earth', 'gray', 'dense', 'purples', 'puor', 'gnuplot2_r', 'spectral', 'rain', 'cfastie', 'tab20_r', 'curl', 'solar_r', 'terrain', 'afmhot_r', 'cubehelix', 'jet_r', 'magma_r', 'gist_yarg', 'tab20', 'rdgy', 'afmhot', 'gist_earth_r', 'rdgy_r', 'viridis_r', 'reds_r', 'binary_r', 'flag', 'turbid', 'accent', 'thermal', 'pink', 'plasma', 'balance_r', 'cool', 'pubugn_r', 'set3', 'gnuplot', 'ocean', 'copper_r', 'bwr', 'matter_r', 'turbid_r', 'gnuplot_r', 'amp', 'orrd', 'tab20b_r', 'algae', 'rdylgn_r', 'gist_gray_r', 'prism_r', 'ocean_r', 'autumn_r', 'piyg', 'tarn', 'greys_r', 'set2_r', 'winter_r', 'brbg_r', 'gist_rainbow', 'pubu', 'ylgn_r', 'gist_heat_r', 'seismic', 'dark2', 'hot', 'rdylgn', 'oranges_r', 'puor_r', 'bwr_r', 'ylorrd_r', 'inferno', 'speed', 'set3_r', 'ylgnbu', 'balance', 'rdylbu', 'greens', 'ylgnbu_r', 'topo_r', 'wistia', 'prgn_r', 'bupu', 'jet', 'gist_gray', 'ylgn', 'tab10_r', 'seismic_r', 'twilight', 'tab20c_r', 'hsv_r', 'ylorbr_r', 'orrd_r', 'gist_heat', 'blues', 'gist_ncar', 'coolwarm_r', 'paired', 'wistia_r', 'purd_r', 'autumn', 'greys', 'diff', 'topo', 'tab20b', 'oxy_r', 'purples_r', 'diff_r', 'rdylbu_r', 'tempo', 'tab20c', 'gist_stern_r', 'prism', 'tarn_r', 'gnuplot2', 'set1_r', 'bugn_r', 'purd', 'cmrmap_r', 'cividis_r', 'spectral_r', 'dark2_r', 'pastel1_r', 'inferno_r', 'twilight_shifted_r', 'delta', 'pubu_r', 'terrain_r', 'ice', 'brbg', 'viridis', 'hot_r', 'rainbow_r', 'haline', 'rdpu', 'cool_r', 'magma', 'tab10', 'solar', 'twilight_shifted', 'gist_yarg_r', 'coolwarm', 'oxy', 'amp_r', 'tempo_r', 'flag_r', 'brg', 'rdpu_r', 'pubugn', 'bone_r', 'deep', 'winter', 'dense_r', 'gnbu', 'blues_r', 'summer_r', 'cubehelix_r', 'speed_r', 'cividis', 'hsv', 'gray_r', 'piyg_r', 'binary', 'plasma_r', 'gist_rainbow_r', 'pastel1', 'set1', 'nipy_spectral_r', 'gnbu_r', 'prgn', 'copper', 'rplumbo', 'thermal_r', 'pastel2', 'rdbu', 'spring_r', 'delta_r', 'set2', 'rainbow', 'bugn', 'greens_r', 'brg_r', 'reds', 'turbo', 'ylorrd', 'curl_r', 'gist_stern', 'schwarzwald', 'phase', 'rain_r', 'matter', 'deep_r', 'ice_r', 'paired_r', 'cmrmap', 'bupu_r', 'pastel2_r', 'spring', 'phase_r', 'algae_r', 'turbo_r', 'rdbu_r', 'nipy_spectral', 'bone', 'ylorbr', 'pink_r', 'gist_ncar_r', 'twilight_r', 'accent_r', 'summer', 'haline_r'], Query(PydanticUndefined)] = None,
    colormap: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

    
#### environment_dependency

```python3
def environment_dependency(
    
)
```

    
#### info

```python3
def info(
    self
)
```

Register /info endpoint.

    
#### map_viewer

```python3
def map_viewer(
    self
)
```

Register /map endpoint.

    
#### part

```python3
def part(
    self
)
```

Register /bbox and `/feature` endpoints.

    
#### path_dependency

```python3
def path_dependency(
    url: typing_extensions.Annotated[str, Query(PydanticUndefined)]
) -> str
```

Create dataset path from args

    
#### point

```python3
def point(
    self
)
```

Register /point endpoints.

    
#### preview

```python3
def preview(
    self
)
```

Register /preview endpoint.

    
#### process_dependency

```python3
def process_dependency(
    algorithm: typing_extensions.Annotated[Literal['hillshade', 'contours', 'normalizedIndex', 'terrarium', 'terrainrgb'], Query(PydanticUndefined)] = None,
    algorithm_params: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]
```

Data Post-Processing options.

    
#### register_routes

```python3
def register_routes(
    self
)
```

This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialization.

    
#### rescale_dependency

```python3
def rescale_dependency(
    rescale: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
) -> Union[List[Tuple[float, ...]], NoneType]
```

Min/Max data Rescaling

    
#### statistics

```python3
def statistics(
    self
)
```

add statistics endpoints.

    
#### tile

```python3
def tile(
    self
)
```

Register /tiles endpoint.

    
#### tilejson

```python3
def tilejson(
    self
)
```

Register /tilejson.json endpoint.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

Return full url (with prefix) for a specific endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

Register /wmts endpoint.