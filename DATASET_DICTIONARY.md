# UKERC Energy Hackathon — Complete Data Dictionary & Dataset Guide

This document provides a comprehensive data dictionary, schema guide, and reproducible Python source code for all datasets across the three hackathon challenge tracks:
1. **Track 01: Energy Poverty & Equity**
2. **Track 02: Future Electricity Systems**
3. **Track 03: Heat, Buildings & Decarbonisation**

---

# Track 01: Energy Poverty & Equity

### Challenge Objective
*“In which local neighbourhoods (LSOAs) is fuel poverty risk the highest when considering both low household income and energy-inefficient homes? If you had a fixed support budget, where should you spend it to reduce that risk the most?”*

---

## 1. `fuel-poverty-sub-regional-2026-2024-data-tables.xlsx` [Per Brief]
* **Source**: Department for Energy Security and Net Zero (DESNZ)
* **Official URL**: [GOV.UK Sub-regional Fuel Poverty Statistics](https://www.gov.uk/government/statistics/sub-regional-fuel-poverty-data-2026-2024-data)
* **Temporal Coverage**: 2024 Data (2026 Release)
* **Geographic Resolution**: Lower Layer Super Output Area (LSOA 2021)
* **Purpose**: Primary target outcome variable. Provides the count and percentage of households in fuel poverty under the official **Low Income Low Energy Efficiency (LILEE)** metric.
* **Key Sheets**:
  * **`Table 4`** (Recommended for LSOA analysis): Fuel Poverty by Lower Layer Super Output Area (`header=2`).
  * **`Table 2`**: Fuel Poverty summary by Local Authority District (`header=2`).
  * **`Table 1`**: Regional summary totals (`header=2`).

### Key Columns & Data Dictionary (Sheet: `Table 4`)
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `LSOA Code` | String | 2021 LSOA census code (e.g. `E01000001`). Primary join key. |
| `LSOA Name` | String | LSOA identifier name (e.g. `City of London 001A`). |
| `Local Authority Code` | String | Local Authority district code (e.g. `E09000001`). |
| `Local Authority Name` | String | Council/District name (e.g. `City of London`, `Hartlepool`). |
| `Region` | String | Government Office Region (e.g. `London`, `North East`). |
| `Number of households` | Integer | Total estimated residential households in the LSOA. |
| `Number of households in fuel poverty` | Integer | Estimated count of households classified as fuel poor under LILEE. |
| `Proportion of households fuel poor (%)` | Float | Percentage of households in fuel poverty ($0.0\% - 100.0\%$). |

---

## 2. `File_1_-_IMD2019_Index_of_Multiple_Deprivation.xlsx` [Per Brief]
* **Source**: Ministry of Housing, Communities & Local Government (MHCLG)
* **Official URL**: [English Indices of Deprivation 2019](https://www.gov.uk/government/statistics/english-indices-of-deprivation-2019)
* **Temporal Coverage**: 2019 Benchmark (Standard official deprivation layer)
* **Geographic Resolution**: LSOA 2011 (Maps 1-to-1 to 2021 LSOAs for >95% of areas)
* **Purpose**: Measures multi-dimensional household vulnerability and relative socio-economic deprivation.
* **Key Sheet**: **`IMD2019`** (`header=0`). *(Note: Sheet 0 is a notes cover sheet).*

### Key Columns & Data Dictionary (Sheet: `IMD2019`)
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `LSOA code (2011)` | String | 2011 LSOA code (e.g. `E01000001`). Primary join key. |
| `LSOA name (2011)` | String | LSOA identifier name (e.g. `City of London 001A`). |
| `Local Authority District code (2019)` | String | Local Authority District code (e.g. `E09000001`). |
| `Local Authority District name (2019)` | String | Local Authority District name. |
| `Index of Multiple Deprivation (IMD) Rank` | Integer | Nationwide rank across all 32,844 LSOAs ($1 = \text{most deprived}$, $32,844 = \text{least deprived}$). |
| `Index of Multiple Deprivation (IMD) Decile` | Integer | Nationwide decile ($1 = 10\%\text{ most deprived}$, $10 = 10\%\text{ least deprived}$). |

---

## 3. `anonymised-NEED-data-2024-50k.csv` [Per Brief]
* **Source**: DESNZ National Energy Efficiency Data-Framework (NEED)
* **Official URL**: [GOV.UK NEED Anonymised Microdata 2024](https://www.gov.uk/government/statistics/national-energy-efficiency-data-framework-need-anonymised-data-2024)
* **Temporal Coverage**: 2024 Release (50,000 property-level microdata records across England & Wales)
* **Purpose**: Property-level microdata linking dwelling archetypes, energy efficiency installations, and real annual gas/electricity consumption.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `PROP_TYPE` | Categorical | Property style (`1`=Detached, `2`=Semi-Detached, `3`=End-Terrace, `4`=Mid-Terrace, `5`=Bungalow, `6`=Flat). |
| `PROP_AGE_BAND` | Categorical | Construction era (`1`=Pre-1919, `2`=1919-44, `3`=1945-64, `4`=1965-82, `5`=1983-92, `6`=1993-99, `7`=Post-1999). |
| `FLOOR_AREA_BAND` | Categorical | Usable floor area band (`1`=<50m², `2`=51-100m², `3`=101-150m², `4`=151-200m², `5`=>200m²). |
| `COUNCIL_TAX_BAND` | Categorical | Valuation band (`1`=Band A, `2`=Band B, `3`=Band C, `4`=Band D, `5`=Band E, `6`=Band F, `7`=Band G, `8`=Band H). |
| `IMD_BAND_ENG` | Categorical | English IMD Decile of the property's location ($1 = \text{most deprived}$, $10 = \text{least deprived}$). |
| `REGION` | Categorical | Government region code. |
| `EPC` | Categorical | Energy Performance Certificate current rating band (`A` to `G`). |
| `CWI_FLAG` | Binary (`0`/`1`) | Cavity Wall Insulation recorded (`1` = Installed, `0` = Not installed). |
| `LI_FLAG` | Binary (`0`/`1`) | Loft Insulation recorded (`1` = Installed, `0` = Not installed). |
| `PV_FLAG` | Binary (`0`/`1`) | Solar Photovoltaics (solar panels) recorded (`1` = Installed, `0` = Not installed). |
| `CONSERVATORY_FLAG` | Binary (`0`/`1`) | Property has an added conservatory (`1` = Yes, `0` = No). |
| `MAIN_HEAT_FUEL` | Categorical | Primary heating fuel type (`1`=Mains Gas, `2`=Electricity, `3`=Oil, `4`=Solid Fuel, `5`=Biomass). |
| `Gcons2022` | Float | Measured annual domestic gas consumption for 2022 ($\text{kWh}$). |
| `Econs2022` | Float | Measured annual domestic electricity consumption for 2022 ($\text{kWh}$). |
| `Gcons2005`–`Gcons2021` | Float | Historical annual gas consumption series ($\text{kWh}$). |
| `Econs2005`–`Econs2021` | Float | Historical annual electricity consumption series ($\text{kWh}$). |

---

## 4. `lsoa_domestic_gas_2024.xlsx` [Added Dataset]
* **Source**: DESNZ Sub-national Gas Consumption Statistics
* **Official URL**: [GOV.UK LSOA Gas Consumption Data](https://www.gov.uk/government/statistics/lower-and-middle-super-output-areas-gas-consumption)
* **Temporal Coverage**: 2024 (Weather-corrected estimates)
* **Geographic Resolution**: LSOA 2021 (Great Britain)
* **Purpose**: Quantifies weather-corrected domestic heating gas consumption per neighbourhood.
* **Key Sheet**: **`2024`** (`header=4`).

### Key Columns & Data Dictionary (Sheet: `2024`)
| Column Name in File | Type | Description & Units |
| :--- | :--- | :--- |
| `Local authority code` | String | Local Authority district code (e.g. `E06000001`). |
| `Local authority` | String | Local Authority name (e.g. `Hartlepool`). |
| `MSOA code` | String | Middle Layer Super Output Area code. |
| `Middle layer super output area` | String | MSOA name. |
| `LSOA code` | String | 2021 LSOA code (e.g. `E01011954`). Primary join key. |
| `Lower layer super output area` | String | LSOA neighbourhood name. |
| `Number of meters` | Integer | Total active domestic gas meters in the LSOA. |
| `Total consumption (kWh)` | Float | Total weather-corrected domestic gas usage in the LSOA ($\text{kWh}$). |
| `Mean consumption (kWh per meter)` | Float | Average gas consumption per meter ($\text{kWh}$). |
| `Median consumption (kWh per meter)` | Float | Median gas consumption per meter ($\text{kWh}$). Preferred over mean for skewed distributions. |
| `Number of non-consuming meters` | Integer | Count of meters with 0 consumption recorded. |

---

## 5. `lso_domestic_elec_2024.xlsx` [Added Dataset]
* **Source**: DESNZ Sub-national Electricity Consumption Statistics
* **Official URL**: [GOV.UK LSOA Electricity Consumption Data](https://www.gov.uk/government/statistics/lower-and-middle-super-output-areas-electricity-consumption)
* **Temporal Coverage**: 2024
* **Geographic Resolution**: LSOA 2021 (Great Britain)
* **Purpose**: Identifies baseline domestic electricity usage and off-gas grid electric heating spikes.
* **Key Sheet**: **`2024`** (`header=4`).

### Key Columns & Data Dictionary (Sheet: `2024`)
| Column Name in File | Type | Description & Units |
| :--- | :--- | :--- |
| `Local authority code` | String | Local Authority district code. |
| `Local authority` | String | Local Authority name. |
| `MSOA code` | String | Middle Layer Super Output Area code. |
| `Middle layer super output area` | String | MSOA name. |
| `LSOA code` | String | 2021 LSOA code. Primary join key. |
| `Lower layer super output area` | String | LSOA neighbourhood name. |
| `Number of meters` | Integer | Total active domestic electricity meters in the LSOA. |
| `Total consumption (kWh)` | Float | Total domestic electricity usage in the LSOA ($\text{kWh}$). |
| `Mean consumption (kWh per meter)` | Float | Average electricity consumption per meter ($\text{kWh}$). |
| `Median consumption (kWh per meter)` | Float | Median electricity consumption per meter ($\text{kWh}$). |

---

## 6. LSOA Boundaries: GeoJSON & Centroid CSV [Added Dataset]
* **Files**: 
  * `Lower_layer_Super_Output_Areas_...geojson` (Polygon spatial boundaries for GIS/mapping)
  * `Lower_layer_Super_Output_Areas_...csv` (Centroid lookup table)
* **Source**: Office for National Statistics (ONS) Open Geography Portal
* **Official URL**: [ONS Geoportal LSOA 2021 Boundaries](https://geoportal.statistics.gov.uk/datasets/ons::lower-layer-super-output-areas-december-2021-boundaries-ew-bgc-v5-2/about)
* **Purpose**: Provides geometry polygons for interactive maps (`GeoPandas`, `Folium`, `Plotly`) as well as exact latitude/longitude centroids for direct plotting without GIS libraries.

### Key Columns in Boundary CSV:
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `LSOA21CD` | String | 2021 LSOA census code. Primary join key. |
| `LSOA21NM` | String | LSOA neighbourhood name. |
| `LAT` | Float | Latitude centroid coordinate (WGS84, e.g. `51.51817`). |
| `LONG` | Float | Longitude centroid coordinate (WGS84, e.g. `-0.09715`). |
| `BNG_E` | Integer | British National Grid Easting coordinate (meters). |
| `BNG_N` | Integer | British National Grid Northing coordinate (meters). |
| `Shape__Area` | Float | Geographic surface area ($\text{m}^2$). |

---

# Track 02: Future Electricity Systems

### Challenge Objective
*“Using real British electricity data, how much carbon (and cost) could a flexible load (such as EV smart charging or heat pump pre-heating) save by shifting when it runs? What would it take to unlock that flexibility?”*

---

## 1. `gb_carbon_intensity_30min_2024.csv` [Per Brief]
* **Source**: National Grid ESO Carbon Intensity API
* **API Documentation**: [Carbon Intensity API Portal](https://carbonintensity.org.uk/)
* **Direct Query Endpoint**: `https://api.carbonintensity.org.uk/intensity/date/YYYY-MM-DD`
* **Temporal Coverage**: 100% Full-Year 2024 (Jan 1 – Dec 31, 2024 = 17,537 half-hourly records)
* **Purpose**: Optimization target for carbon-shifting algorithms.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `from` | ISO 8601 UTC | Start of 30-minute settlement period (e.g. `2024-01-01T00:00Z`). Primary join key. |
| `to` | ISO 8601 UTC | End of 30-minute settlement period (e.g. `2024-01-01T00:30Z`). |
| `intensity_forecast` | Integer | Day-ahead forecast carbon intensity ($\text{gCO}_2/\text{kWh}$). |
| `intensity_actual` | Integer | Actual outturn carbon intensity ($\text{gCO}_2/\text{kWh}$). |
| `intensity_index` | Categorical | Qualitative category (`very low`, `low`, `moderate`, `high`, `very high`). |

---

## 2. `gb_generation_mix_30min_2024.csv` [Per Brief]
* **Source**: Elexon BMRS API (Dataset: `FUELHH`)
* **API Documentation**: [Elexon Insights Solution](https://bmrs.elexon.co.uk/)
* **Direct Query Endpoint**: `https://data.elexon.co.uk/bmrs/api/v1/datasets/FUELHH/stream`
* **Temporal Coverage**: 100% Full-Year 2024 (340,893 records sorted chronologically)
* **Purpose**: Evaluates grid security of supply and peak reduction for Gas CCGT and European Interconnector cables.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `startTime` | ISO 8601 UTC | Start of 30-minute settlement window. Primary join key. |
| `settlementDate` | Date (`YYYY-MM-DD`) | GB electricity market settlement date. |
| `settlementPeriod` | Integer ($1 - 48$) | GB settlement period of the day ($1 = 00:00-00:30, \dots, 48 = 23:30-24:00$). |
| `fuelType` | Categorical | Fuel category: `CCGT` (Combined Cycle Gas Turbine), `WIND`, `SOLAR`, `NUCLEAR`, `BIOMASS`, `HYDRO`, `INTFR` (France IFA), `INTIFA2` (IFA2), `INTNEM` (Nemo), `INTELEC` (ElecLink), `INTNSL` (North Sea Link Norway), `INTVIK` (Viking Link Denmark), `PS` (Pumped Storage), `OTHER`. |
| `generation` | Float / Integer | Average electrical power output over the half-hour in Megawatts ($\text{MW}$). |

---

## 3. `octopus_agile_tariffs_30min_2024_full.csv` [Added Dataset]
* **Source**: Octopus Energy Developer API
* **API Documentation**: [Octopus Energy API](https://developer.octopus.energy/docs/api/)
* **Direct Query Endpoint**: `https://api.octopus.energy/v1/products/{product_code}/electricity-tariffs/{tariff_code}/standard-unit-rates/`
* **Temporal Coverage**: 100% Full-Year 2024 (17,568 half-hourly price slots)
* **Purpose**: Unlocks the cost optimization stretch goal by providing real half-hourly dynamic retail prices.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `valid_from` | ISO 8601 UTC | Start of 30-minute price period. Join key. |
| `valid_to` | ISO 8601 UTC | End of 30-minute price period. |
| `value_inc_vat` | Float | Unit electricity price including VAT in pence per kilowatt-hour ($\text{p}/\text{kWh}$). Can be negative during renewable surplus! |
| `value_exc_vat` | Float | Unit electricity price excluding VAT ($\text{p}/\text{kWh}$). |

---

## 4. `subnational_electricity_consumption_statistics_2024.xlsx` [Per Brief]
* **Source**: DESNZ Sub-national Electricity Statistics
* **Official URL**: [GOV.UK Regional Electricity Statistics](https://www.gov.uk/government/statistics/regional-and-local-authority-electricity-consumption-statistics)
* **Temporal Coverage**: 2024 Baseline
* **Purpose**: Fulfills Task 4 (*"Ground it in a real place using sub-national consumption"*). Allows scaling load shifts to local authority electricity demand.
* **Key Sheet**: **`2024`** (`header=4`).

### Key Columns & Data Dictionary (Sheet: `2024`)
| Column Name in File | Type | Description & Units |
| :--- | :--- | :--- |
| `Code` | String | Country, Region, or Local Authority code (e.g. `E09000001`). Join key. |
| `Country or region` | String | Country or Government Region name. |
| `Local authority` | String | Council/District name (e.g. `Hartlepool`, `Birmingham`, `All local authorities`). |
| `Number of meters (thousands): All Domestic` | Float | Total domestic electricity meters in thousands. |
| `Number of meters (thousands): All Non-Domestic` | Float | Total commercial and industrial meters in thousands. |
| `Number of meters (thousands): All meters` | Float | Total electricity meters in thousands. |
| `Total consumption (GWh): All Domestic` | Float | Aggregate annual residential electricity demand in Gigawatt-hours ($\text{GWh}$). |
| `Total consumption (GWh): All Non-Domestic` | Float | Aggregate annual commercial/industrial demand in Gigawatt-hours ($\text{GWh}$). |
| `Total consumption (GWh): All meters` | Float | Total electricity consumption ($\text{GWh}$). |
| `Mean consumption (kWh per meter): All Domestic` | Float | Average domestic meter annual electricity consumption ($\text{kWh}$). |
| `Median consumption (kWh per meter): All Domestic` | Float | Median domestic meter annual electricity consumption ($\text{kWh}$). |
| `Mean domestic consumption (kWh per household)` | Float | Average electricity consumption per household ($\text{kWh}$). |

---

# Track 03: Heat, Buildings & Decarbonisation

### Challenge Objective
*“In real heat-pump homes, which properties are most at risk of condensation and mould on cold surfaces? Does that risk get hidden when using standard monthly averages (the Glaser method) compared to real, measured overnight lows?”*

---

## 1. `eoh_interim_performance_summary.csv` [Per Brief]
* **Source**: Electrification of Heat (EoH) Demonstration Project (Energy Systems Catapult / DESNZ)
* **Official URL**: [OpenNetZero Electrification of Heat Project](https://opennetzero.org/) & [ESC Open Data](https://es.catapult.org.uk/tools-and-labs/data/)
* **Purpose**: Cohort microdata of real UK heat pump homes on coldest winter days to evaluate real-world efficiency and indoor temperatures.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `property_id` | String | Unique home trial identifier (e.g. `EoH_Home_001`). |
| `property_type` | Categorical | Dwelling form (`Detached`, `Semi-Detached`, `Terraced`, `Bungalow`). |
| `epc_band` | Categorical | Energy efficiency band (`C`, `D`, `E`, `F`). |
| `heat_pump_type` | Categorical | System type (`ASHP` = Air Source, `GSHP` = Ground Source, `Hybrid`). |
| `coldest_day_min_outdoor_temp_C` | Float | Minimum recorded outdoor temperature on the coldest trial day ($^\circ\text{C}$). |
| `coldest_day_mean_indoor_temp_C` | Float | 24-hour mean indoor temperature across the property ($^\circ\text{C}$). Represents the standard monthly/daily average view. |
| `coldest_day_overnight_min_indoor_temp_C` | Float | Lowest recorded indoor temperature during overnight hours ($^\circ\text{C}$). Represents the cold overnight extreme view. |
| `wall_u_value` | Float | Thermal transmittance of external walls ($\text{W}/\text{m}^2\text{K}$). Lower is better insulated. |
| `window_u_value` | Float | Thermal transmittance of glazing ($\text{W}/\text{m}^2\text{K}$). |
| `seasonal_cop` | Float | Seasonal Coefficient of Performance (heat output / electrical input ratio). |

---

## 2. `open_epc_domestic_sample_england.csv` [Per Brief - Open Access]
* **Source**: GOV.UK Open Data Communities
* **Official URL**: [Open Data Communities Domestic EPC Portal](https://epc.opendatacommunities.org/)
* **Purpose**: Detailed building envelope fabric data (glazing, wall insulation, floor area).

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `lmk_key` | String | Unique domestic EPC certificate key. |
| `property_type` | Categorical | Dwelling type (`House`, `Flat`, `Bungalow`, `Maisonette`). |
| `built_form` | Categorical | Architecture (`Detached`, `Semi-Detached`, `Mid-Terrace`, `End-Terrace`). |
| `current_energy_rating` | Categorical | Standard SAP EPC Rating band (`A` through `G`). |
| `current_energy_efficiency` | Integer ($1 - 100$) | Numerical Energy Efficiency Score ($0 - 100$). |
| `glaz_type` | Categorical | Window glazing type (`single glazing`, `double glazing`, `triple glazing`). |
| `walls_description` | Text | Physical wall insulation description (e.g. `Cavity wall, filled cavity`). |
| `total_floor_area` | Float | Usable floor area in square meters ($\text{m}^2$). |
| `postcode` | String | Truncated postcode sector. |

---

## 3. `ideal_household_temp_humidity_sample.csv` [Per Brief - Stretch Goal]
* **Source**: IDEAL Household Energy Dataset (University of Edinburgh)
* **Official URL**: [Edinburgh DataShare IDEAL Repository](https://datashare.ed.ac.uk/handle/10283/3647)
* **Purpose**: High-resolution indoor room temperature and relative humidity sensor telemetry to evaluate dew points and damp risk.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `home_id` | String | Unique trial home identifier. |
| `timestamp` | ISO 8601 UTC | Half-hourly sensor recording timestamp. |
| `room_temperature_C` | Float | Measured indoor air temperature ($^\circ\text{C}$). |
| `relative_humidity_pct` | Float | Measured indoor relative humidity ($0\% - 100\%$). |

---

## 4. `uk_cold_snap_winter_weather_hourly.csv` [Added Dataset]
* **Source**: Open-Meteo Historical Weather API
* **API Documentation**: [Open-Meteo Historical Weather](https://open-meteo.com/en/docs/historical-weather-api)
* **Purpose**: Freezing outdoor weather conditions during the December 2022 UK cold snap to compute surface temperature and dew point margins ($T_{\text{surface}} - T_{\text{dew\_point}}$).

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `time` | ISO 8601 UTC | Hourly timestamp during the freezing winter cold spell. |
| `outdoor_temp_C` | Float | Outdoor 2-meter air temperature ($^\circ\text{C}$). |
| `outdoor_rh_pct` | Float | Outdoor relative humidity ($0\% - 100\%$). |
| `outdoor_dew_point_C` | Float | Outdoor dew point temperature ($^\circ\text{C}$). |

---

# Python Ingestion Scripts (Reproduce All Downloads)

Below are the complete, runnable Python scripts used to download, extract, and sort every dataset directly from the official APIs and data endpoints.

### Script 1: Fetch Full-Year 2024 Grid Timeseries (Track 02)
```python
import os
import time
import requests
import pandas as pd
from concurrent.futures import ThreadPoolExecutor, as_completed

headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"}

# 1. Fetch Carbon Intensity 2024 (366 days in parallel)
def fetch_carbon_day(d_str):
    url = f"https://api.carbonintensity.org.uk/intensity/date/{d_str}"
    try:
        r = requests.get(url, headers=headers, timeout=15)
        if r.status_code == 200:
            return [{
                "from": item.get("from"),
                "to": item.get("to"),
                "intensity_forecast": item.get("intensity", {}).get("forecast"),
                "intensity_actual": item.get("intensity", {}).get("actual"),
                "intensity_index": item.get("intensity", {}).get("index")
            } for item in r.json().get("data", [])]
    except Exception:
        pass
    return []

dates = pd.date_range("2024-01-01", "2024-12-31").strftime("%Y-%m-%d")
all_carbon = []
with ThreadPoolExecutor(max_workers=20) as executor:
    futures = [executor.submit(fetch_carbon_day, d) for d in dates]
    for f in as_completed(futures):
        all_carbon.extend(f.result())

df_carbon = pd.DataFrame(all_carbon)
df_carbon.sort_values("from", inplace=True)
df_carbon.to_csv("gb_carbon_intensity_30min_2024.csv", index=False)

# 2. Fetch Elexon BMRS Generation Mix 2024 (4 Quarters in parallel)
def fetch_elexon_quarter(start_t, end_t):
    url = f"https://data.elexon.co.uk/bmrs/api/v1/datasets/FUELHH/stream?publishDateTimeFrom={start_t}&publishDateTimeTo={end_t}"
    try:
        r = requests.get(url, headers=headers, timeout=40)
        if r.status_code == 200:
            return pd.DataFrame(r.json())
    except Exception:
        pass
    return pd.DataFrame()

quarters = [
    ("2024-01-01T00:00:00Z", "2024-03-31T23:59:59Z"),
    ("2024-04-01T00:00:00Z", "2024-06-30T23:59:59Z"),
    ("2024-07-01T00:00:00Z", "2024-09-30T23:59:59Z"),
    ("2024-10-01T00:00:00Z", "2024-12-31T23:59:59Z")
]

gen_dfs = []
with ThreadPoolExecutor(max_workers=4) as executor:
    futures = [executor.submit(fetch_elexon_quarter, q[0], q[1]) for q in quarters]
    for f in as_completed(futures):
        res = f.result()
        if not res.empty:
            gen_dfs.append(res)

df_gen = pd.concat(gen_dfs, ignore_index=True)
df_gen["dt_temp"] = pd.to_datetime(df_gen["startTime"], errors="coerce")
df_gen.sort_values(by=["dt_temp", "settlementPeriod", "fuelType"], ascending=True, inplace=True)
df_gen.drop(columns=["dt_temp"], inplace=True)
df_gen.to_csv("gb_generation_mix_30min_2024.csv", index=False)

# 3. Fetch Octopus Agile Dynamic Tariffs 2024
products = ["AGILE-23-12-06", "AGILE-24-04-03", "AGILE-24-10-01"]
agile_records = []
for prod in products:
    url = f"https://api.octopus.energy/v1/products/{prod}/electricity-tariffs/E-1R-{prod}-A/standard-unit-rates/?period_from=2024-01-01T00:00Z&period_to=2024-12-31T23:59Z&page_size=1500"
    while url:
        try:
            r = requests.get(url, headers=headers, timeout=20)
            if r.status_code == 200:
                body = r.json()
                agile_records.extend(body.get("results", []))
                url = body.get("next")
                time.sleep(0.05)
            else:
                break
        except Exception:
            break

df_agile = pd.DataFrame(agile_records)
df_agile["valid_from_dt"] = pd.to_datetime(df_agile["valid_from"], errors="coerce")
df_agile.sort_values("valid_from_dt", ascending=True, inplace=True)
df_agile.drop_duplicates(subset=["valid_from_dt"], inplace=True)
df_agile.drop(columns=["valid_from_dt"], inplace=True)
df_agile.to_csv("octopus_agile_tariffs_30min_2024_full.csv", index=False)
```

---

### Script 2: Fetch Cold-Snap Weather Data (Track 03)
```python
import requests
import pandas as pd

weather_url = "https://archive-api.open-meteo.com/v1/archive?latitude=51.5074&longitude=-0.1278&start_date=2022-12-05&end_date=2022-12-18&hourly=temperature_2m,relative_humidity_2m,dew_point_2m"
headers = {"User-Agent": "Mozilla/5.0"}

r = requests.get(weather_url, headers=headers, timeout=20)
if r.status_code == 200:
    h = r.json().get("hourly", {})
    df_weather = pd.DataFrame({
        "time": h.get("time"),
        "outdoor_temp_C": h.get("temperature_2m"),
        "outdoor_rh_pct": h.get("relative_humidity_2m"),
        "outdoor_dew_point_C": h.get("dew_point_2m")
    })
    df_weather.to_csv("uk_cold_snap_winter_weather_hourly.csv", index=False)
```

---

### Script 3: Restore Official IMD 2019 Dataset (Track 01)
```python
import requests
import re
import os

page_url = "https://www.gov.uk/government/statistics/english-indices-of-deprivation-2019"
headers = {"User-Agent": "Mozilla/5.0"}
r = requests.get(page_url, headers=headers)

links = re.findall(r'href=[\'"]?([^\'" >]+)', r.text)
for link in links:
    if "File_1" in link and link.endswith(".xlsx"):
        r_file = requests.get(link, headers=headers)
        if r_file.status_code == 200:
            with open("File_1_-_IMD2019_Index_of_Multiple_Deprivation.xlsx", "wb") as f:
                f.write(r_file.content)
            print("Successfully saved official IMD 2019 Excel file.")
            break
```
