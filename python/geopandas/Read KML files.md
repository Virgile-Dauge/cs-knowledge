```python
import fiona
import geopandas as gpd

fiona.drvsupport.supported_drivers['KML'] = 'rw'
agglo = gpd.read_file('2021/L4400_agglo_2021.kml', driver='KML')
agglo

```
