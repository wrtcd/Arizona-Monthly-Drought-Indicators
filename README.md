# Arizona Monthly Drought Indicators (2019–2024)

This repository provides monthly drought-related environmental indicators for the state of Arizona from January 2019 to December 2024. The analysis leverages Google Earth Engine (GEE) to generate consistent, spatially averaged measurements of vegetation health, surface temperature, precipitation, and combined drought indices. These variables are especially relevant for understanding climate stress in arid and semi-arid landscapes such as Arizona.

## Dataset Summary

| Variable             | Source Dataset                               | Description                                 | Resolution   |
|----------------------|----------------------------------------------|---------------------------------------------|--------------|
| NDVI                 | `COPERNICUS/S2_SR_HARMONIZED`               | Sentinel-2 based vegetation index           | 10–30 m      |
| Land Surface Temp    | `MODIS/061/MOD11A2`                         | 8-day composite of LST (converted to °C)    | 1 km         |
| Precipitation        | `UCSB-CHG/CHIRPS/DAILY`                     | Daily rainfall, aggregated monthly          | ~5 km        |
| Vegetation Health Index (VHI) | Derived (NDVI + LST-based)          | Normalized index combining greenness & heat stress | — |

## Methodology

- **NDVI** is computed using the normalized difference of near-infrared (B8) and red (B4) bands from Sentinel-2, filtered for clouds and composited monthly.
- **Land Surface Temperature (LST)** is obtained from MODIS 8-day products (`LST_Day_1km`), averaged for each month, and converted from Kelvin to Celsius.
- **Precipitation** is calculated by summing daily CHIRPS rainfall estimates for each month.
- **Vegetation Health Index (VHI)** is derived by combining normalized NDVI and LST signals to indicate drought-related vegetation stress (higher = healthier vegetation).

All variables are spatially averaged over the Arizona state boundary using TIGER/Line shapefiles.

## Output

The final output is available in the file:

**`Arizona_Monthly_Drought_Indicators_2019_2024.csv`**

This CSV contains the following columns:

| Column             | Description                                                 |
|--------------------|-------------------------------------------------------------|
| `date`             | Month in `YYYY-MM` format                                   |
| `mean_lst_c`       | Mean daytime land surface temperature (°C)                  |
| `mean_ndvi`        | Mean NDVI across Arizona (unitless)                         |
| `mean_precip_mm`   | Total monthly precipitation (mm)                            |
| `mean_vhi`         | Vegetation Health Index (0–1), combining LST and NDVI       |

## Applications

- Monitoring seasonal vegetation response to drought and heat
- Identifying prolonged dry spells and surface warming trends
- Supporting water management, wildfire preparedness, and ecological monitoring
- Useful for desert ecosystem adaptation and agricultural decision support

## Data Access

- [Sentinel-2 SR Harmonized](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)
- [MODIS Land Surface Temperature (MOD11A2)](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD11A2)
- [CHIRPS Precipitation](https://developers.google.com/earth-engine/datasets/catalog/UCSB_CHG_CHIRPS_DAILY)
- [Arizona Boundary (U.S. Census TIGER)](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html)

## License

This project is released under the MIT License.
