<h1 id="toc">Table of Contents</h1>

- [1. Download Imperviousness Density for Germany](#1-download-imperviousness-density-for-germany)
- [2. Create 10m Raster for Karlsruhe](#2-create-10m-raster-for-karlsruhe)
- [3. Create 100m Raster for Karlsruhe](#3-create-100m-raster-for-karlsruhe)

## 1. Download Imperviousness Density for Germany

[top](#toc)

- [land.copernicus.eu ~ Imperviousness Density 2018](https://land.copernicus.eu/pan-european/high-resolution-layers/imperviousness/status-maps/imperviousness-density-2018?tab=download)
  - Download `IMD-2018-010m-Germany`

## 2. Create 10m Raster for Karlsruhe

[top](#toc)

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

## 3. Create 100m Raster for Karlsruhe

[top](#toc)

- Create 100m Grid
  - Option 1: Vectorize/Polygonize `cellids.tif`
    - Feature Count `32617`
  - Option 2: Toolbox `Create grid`
    - Type `Rectangle`
    - Extent `Heatdemand_DE_Karlsruhe`
    - Spacing `100 meters`
- Calculate `mean` for grid cells
  - Toolbox `Zonal statistics`
  - Raster layer `IMD_2018_010m_Karlsruhe`
  - Vector layer `Grid`
  - Statistics to Calculate `mean`
- Rasterize and save grid
  - Toolbox `Rasterize (vector to raster)`
  - Input layer `Grid`
  - Field `mean`
  - Output raster size units `Georeferenced units`
  - Width & Height `100`
  - Output extent `NUTS_DE_Karlsruhe`
  - Nodata value `240`
  - Profile `High compression`
  - Output data type `Byte`
  - Save as `IMD_2018_100m_Karlsruhe_mean.tif`