### How to Create LAU_DE Layer

- Download [`LAU-2018-01M-SH.zip`](https://ec.europa.eu/eurostat/cache/GISCO/geodatafiles/LAU-2018-01M-SH.zip) (~ 36 MB)
  - Description: Local Administrative Units (LAU) 2018, Scale 1:1 Million, Shapefile, CRS ETRS89
  - Source: [ec.europa.eu ~ LAU Eurostat](https://ec.europa.eu/eurostat/web/gisco/geodata/reference-data/administrative-units-statistical-units/lau)
  - Details: [ec.europa.eu ~ Local Administrative Units (LAU)](https://ec.europa.eu/eurostat/web/nuts/local-administrative-units)
- Open `LAU-2018-01M-SH.zip`.`LAU_2018.shp`
- Create Layer `LAU_DE`
  - Select by Expression `LEFT("GISCO_ID", 3) = 'DE_'`
  - Toolbox `Fix geometries`
    - Check `Selected features only`
  - Remove layer `LAU_2018.shp`
  - Reproject and save layer `Fixed geometries`
    - Export > `Save Features As`
    - Format `GeoPackage`
    - File name `LAU_DE`
    - CRS `3035`
    - Deselect fields `Shape_Leng` and `Shape_Area`
