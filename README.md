# Arizona Monthly NDVI & Land Surface Temperature (2019–2024)

This repository provides a monthly summary of vegetation greenness and daytime land surface temperature (LST) across Arizona from January 2019 to December 2024. The analysis uses Google Earth Engine (GEE) to evaluate seasonal drought conditions and climate stress in an arid, heat-prone U.S. state.

## Dataset Summary

| Variable       | Source Dataset                               | Description                               | Resolution |
|----------------|----------------------------------------------|-------------------------------------------|------------|
| NDVI           | `COPERNICUS/S2_SR_HARMONIZED`               | Sentinel-2 based vegetation index         | 10–30 m    |
| LST (Daytime)  | `MODIS/061/MOD11A2`                         | 8-day composite of land surface temp.     | 1 km       |

## Methodology

- **NDVI** is calculated using the normalized difference of NIR (B8) and Red (B4) bands from Sentinel-2, composited monthly with cloud masking.
- **Land Surface Temperature (LST)** is derived from MODIS 8-day products and averaged monthly using the `LST_Day_1km` band.
- Monthly spatial averages are computed across the Arizona boundary using U.S. Census TIGER/Line shapefiles.

## Output

The final output is available in the file:

**`Arizona_Monthly_Drought_Indicators_2019_2024.csv`**

This CSV contains the following columns:

| Column          | Description                                              |
|------------------|----------------------------------------------------------|
| `date`           | Month in `YYYY-MM` format                                |
| `mean_ndvi`      | Monthly average NDVI across Arizona                      |
| `mean_lst_day`   | Monthly average LST (Kelvin) during daytime hours        |

## Applications

- Detecting heat stress and drought-linked vegetation changes
- Monitoring surface warming trends over time
- Supporting land management, water conservation, and wildfire risk mitigation
- Useful for understanding desert ecosystem dynamics and agricultural adaptation

## Data Access

- [Sentinel-2 SR Harmonized](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)
- [MODIS LST (MOD11A2)](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD11A2)
- [Arizona State Boundary (U.S. Census TIGER)](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html)

## License

This project is released under the MIT License.
