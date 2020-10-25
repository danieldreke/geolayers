## Imperviousness Density Germany

- [land.copernicus.eu ~ Imperviousness Density 2018](https://land.copernicus.eu/pan-european/high-resolution-layers/imperviousness/status-maps/imperviousness-density-2018?tab=download)
  - Download `IMD-2018-010m-Germany`

### Extract for Karlsruhe

- Add layers
  - `IMD_2018_010m_E41N28_03035_v020`
  - `IMD_2018_010m_E42N28_03035_v020`
- Clip both layers by `NUTS_DE_Karlsruhe`
  - Toolbox `Clip raster by extent`
- Merge clipped rasters
  - Toolbox `Merge`
  - Output data type `Byte`
- Clip merged raster by `NUTS_DE_Karlsruhe`
  - Toolbox `Clip raster by mask layer`
  - Uncheck `Match extent`
- Export as `IMD_2018_010m_Karlsruhe`
  - Profile `High compression`
  - No data `240`
