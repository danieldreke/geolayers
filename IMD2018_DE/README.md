<h1 id="toc">Table of Contents</h1>

- [1. Download Imperviousness Density Rasters](#1-download-imperviousness-density-rasters)
- [2. Create 100m Karlsruhe Raster based on 100m EU Raster](#2-create-100m-karlsruhe-raster-based-on-100m-eu-raster)
- [3. Create 10m Karlsruhe Raster based on 10m Germany Raster Tiles](#3-create-10m-karlsruhe-raster-based-on-10m-germany-raster-tiles)
- [4. Create 100m Karlsruhe Raster based on 10m Karlsruhe Raster](#4-create-100m-karlsruhe-raster-based-on-10m-karlsruhe-raster)

## 1. Download Imperviousness Density Rasters

[top](#toc)

- [land.copernicus.eu ~ Imperviousness Density 2018](https://land.copernicus.eu/pan-european/high-resolution-layers/imperviousness/status-maps/imperviousness-density-2018?tab=download)
  - 100m Raster for EEA39 `IMD-2018-100m-EEA39`
  - 10m Raster for Germany `IMD-2018-010m-Germany`

## 2. Create 100m Karlsruhe Raster based on 100m EU Raster

[top](#toc)

- Open raster `IMD_2018_100m_eu_03035_V2_0.tif`
- Add layer `NUTS_DE_Karlsruhe`
- Clip raster by Extent `NUTS_DE_Karlsruhe`
- Clip result raster by Mask `NUTS_DE_Karlsruhe`
  - Uncheck `Match extent`
  - Profile `High compression`
  - Save to `IMD_2018_100m_Karlsruhe_clipped.tif`

## 3. Create 10m Karlsruhe Raster based on 10m Germany Raster Tiles

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

## 4. Create 100m Karlsruhe Raster based on 10m Karlsruhe Raster

[top](#toc)

- Create 100m Grid
  - Toolbox `Create grid`
    - Type `Rectangle`
    - Extent `NUTS_DE_Karlsruhe`
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