# UKERC Energy Hackathon — Complete Data Dictionary & Dataset Guide

This document provides a comprehensive data dictionary, schema guide, and reproducible Python source code for all datasets across the three hackathon challenge tracks:
1. **Track 01: Energy Poverty & Equity**
2. **Track 02: Future Electricity Systems**
3. **Track 03: Heat, Buildings & Decarbonisation**

---

# Track 01: Energy Poverty & Equity

### Challenge Objective
*“Where in England does fuel-poverty risk concentrate most once you account for both household vulnerability and poor housing efficiency, and where would a fixed budget cut that risk most?”*

---

## 1. `fuel-poverty-sub-regional-2026-2024-data-tables.xlsx` [Per Brief]
* **Source**: Department for Energy Security and Net Zero (DESNZ)
* **Official URL**: [GOV.UK Sub-regional Fuel Poverty Statistics](https://www.gov.uk/government/statistics/sub-regional-fuel-poverty-data-2026-2024-data)
* **Temporal Coverage**: 2024 Data (2026 Release)
* **Geographic Resolution**: Lower Layer Super Output Area (LSOA 2021)
* **Purpose**: Primary target outcome variable. Provides the count and percentage of households in fuel poverty under the official **Low Income Low Energy Efficiency (LILEE)** metric.

### Key Columns & Data Dictionary (Table 4)
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `LSOA Code` | String | 2021 LSOA census code (e.g. `E01000001`). Primary join key. |
| `LSOA Name` | String | LSOA name (e.g. `City of London 001A`). |
| `Local Authority Code` | String | Local Authority district code (e.g. `E09000001`). |
| `Local Authority Name` | String | Council/District name (e.g. `City of London`, `Barking and Dagenham`). |
| `Region` | String | Government Office Region (e.g. `London`, `North West`). |
| `Number of households` | Integer | Total estimated residential households in the LSOA. |
| `Number of households in fuel poverty` | Integer | Estimated count of households classified as fuel poor under LILEE. |
| `Proportion of households fuel poor (%)` | Float | Percentage of households in fuel poverty ($0.0\% - 100.0\%$). |

---

## 2. `File_1_-_IMD2019_Index_of_Multiple_Deprivation.xlsx` [Per Brief]
* **Source**: Ministry of Housing, Communities & Local Government (MHCLG)
* **Official URL**: [English Indices of Deprivation 2019](https://www.gov.uk/government/statistics/english-indices-of-deprivation-2019)
* **Temporal Coverage**: 2019 Benchmark (Standard official deprivation layer)
* **Geographic Resolution**: LSOA 2011 (Maps 1-to-1 to 2021 LSOAs for >95% of areas)
* **Purpose**: Measures multi-dimensional household vulnerability (Income, Health, Employment, Living Environment).

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `LSOA code (2011)` | String | 2011 LSOA code (e.g. `E01000001`). Join key. |
| `LSOA name (2011)` | String | LSOA identifier name. |
| `Index of Multiple Deprivation (IMD) Score` | Float | Composite deprivation score (higher = more deprived). |
| `Index of Multiple Deprivation (IMD) Rank` | Integer | Nationwide rank out of 32,844 LSOAs (1 = most deprived). |
| `Index of Multiple Deprivation (IMD) Decile` | Integer | Nationwide decile ($1 = 10\%$ most deprived, $10 = 10\%$ least deprived). |
| `Income Score (rate)` | Float | Proportion of population experiencing income deprivation. |
| `Employment Score (rate)` | Float | Proportion of working-age population experiencing employment deprivation. |
| `Barriers to Housing and Services Score` | Float | Physical and financial barriers to housing and local services. |
| `Living Environment Score` | Float | Quality of local indoor and outdoor living environment. |

---

## 3. `anonymised-NEED-data-2024-50k.csv` [Per Brief]
* **Source**: DESNZ National Energy Efficiency Data-Framework (NEED)
* **Official URL**: [GOV.UK NEED Anonymised Microdata 2024](https://www.gov.uk/government/statistics/national-energy-efficiency-data-framework-need-anonymised-data-2024)
* **Temporal Coverage**: 2024 (50,000 property-level records)
* **Purpose**: Property-level microdata linking building fabric characteristics, EPC ratings, and actual annual gas/electricity consumption.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `PROP_TYPE` | Categorical | Property style (`1`=Detached, `2`=Semi-Detached, `3`=End-Terrace, `4`=Mid-Terrace, `5`=Bungalow, `6`=Flat). |
| `PROP_AGE_BAND` | Categorical | Construction era (`1`=Pre-1919, `2`=1919-44, `3`=1945-64, `4`=1965-82, `5`=1983-92, `6`=1993-99, `7`=Post-1999). |
| `FLOOR_AREA_BAND` | Categorical | Usable floor area range (`1`=<50m², `2`=51-100m², `3`=101-150m², `4`=151-200m², `5`=>200m²). |
| `EPC` | Categorical | Energy Performance Certificate rating band (`A` to `G`). |
| `CWI_FLAG` | Binary (`0`/`1`) | Cavity Wall Insulation installed (`1` = Yes, `0` = No). |
| `LI_FLAG` | Binary (`0`/`1`) | Loft Insulation installed (`1` = Yes, `0` = No). |
| `MAIN_HEAT_FUEL` | Categorical | Primary heating fuel (`1`=Mains Gas, `2`=Electricity, `3`=Oil, `4`=Solid Fuel, `5`=Biomass). |
| `Gcons2022` | Float | Annual domestic gas consumption ($\text{kWh}$). |
| `Econs2022` | Float | Annual domestic electricity consumption ($\text{kWh}$). |

---

## 4. `lsoa_domestic_gas_2024.xlsx` [Added Dataset]
* **Source**: DESNZ Sub-national Gas Consumption Statistics
* **Official URL**: [GOV.UK LSOA Gas Consumption Data](https://www.gov.uk/government/statistics/lower-and-middle-super-output-areas-gas-consumption)
* **Purpose**: Quantifies domestic heating energy usage ($\text{kWh}$) per neighborhood.

### Key Columns
* `LSOA Code` (String): Join key.
* `Number of meters` (Integer): Total residential gas meters in the LSOA.
* `Total consumption (kWh)` (Float): Aggregate domestic gas consumption.
* `Mean consumption (kWh per meter)` (Float): Average household gas heating consumption.
* `Median consumption (kWh per meter)` (Float): Median household gas heating consumption.

---

## 5. `lso_domestic_elec_2024.xlsx` [Added Dataset]
* **Source**: DESNZ Sub-national Electricity Consumption Statistics
* **Official URL**: [GOV.UK LSOA Electricity Consumption Data](https://www.gov.uk/government/statistics/lower-and-middle-super-output-areas-electricity-consumption)
* **Purpose**: Identifies off-gas grid households relying on electric space heating (visible as spikes in electricity $\text{kWh}$).

### Key Columns
* `LSOA Code` (String): Join key.
* `Number of domestic meters` (Integer): Domestic electricity meters.
* `Total domestic consumption (kWh)` (Float): Total domestic electricity usage.
* `Mean domestic consumption (kWh per meter)` (Float): Average domestic electricity usage.
* `Median domestic consumption (kWh per meter)` (Float): Median domestic electricity usage.

---

## 6. `Lower_layer_Super_Output_Areas_...geojson` & `...csv` [Added Dataset]
* **Source**: Office for National Statistics (ONS) Open Geography Portal
* **Official URL**: [ONS Geoportal LSOA 2021 Boundaries](https://geoportal.statistics.gov.uk/datasets/ons::lower-layer-super-output-areas-december-2021-boundaries-ew-bgc-v5-2/about)
* **Purpose**: Spatial boundary polygons for creating interactive choropleth maps and GIS visualizations in Python (`GeoPandas`, `Folium`, `Plotly`) or QGIS.

---

# Track 02: Future Electricity Systems

### Challenge Objective
*“Using real GB electricity data, how much carbon (and cost) could a defined flexible load save by shifting when it runs, and what would it take to unlock that flexibility (including reducing peak Gas CCGT and Interconnector reliance)?”*

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
| `from` | ISO 8601 UTC | Start of 30-minute settlement period (e.g. `2024-01-01T00:00Z`). Join key. |
| `to` | ISO 8601 UTC | End of 30-minute settlement period (e.g. `2024-01-01T00:30Z`). |
| `intensity_forecast` | Integer | Day-ahead forecast carbon intensity ($\text{gCO}_2/\text{kWh}$). |
| `intensity_actual` | Integer | Actual outturn carbon intensity ($\text{gCO}_2/\text{kWh}$). |
| `intensity_index` | Categorical | Qualitative index (`very low`, `low`, `moderate`, `high`, `very high`). |

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
| `fuelType` | Categorical | Fuel type: `CCGT` (Gas), `WIND`, `SOLAR`, `NUCLEAR`, `BIOMASS`, `HYDRO`, `INTFR` (France IFA), `INTIFA2` (IFA2), `INTNEM` (Nemo), `INTELEC` (ElecLink), `INTNSL` (North Sea Link), `INTVIK` (Viking Link), `PS` (Pumped Storage), `OTHER`. |
| `generation` | Float / Integer | Electrical power output in Megawatts ($\text{MW}$). |

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
* **Purpose**: Fulfills Task 4 (*"Ground it in a real place using sub-national consumption"*).

---

# Track 03: Heat, Buildings & Decarbonisation

### Challenge Objective
*“Across real heat-pump homes, which are most at risk of cold surfaces, damp and condensation, and does the assessment method change the answer (Glaser monthly-average vs. measured overnight-minimum under Awaab's Law)?”*

---

## 1. `eoh_interim_performance_summary.csv` [Per Brief]
* **Source**: Electrification of Heat (EoH) Demonstration Project (Energy Systems Catapult / DESNZ)
* **Official URL**: [OpenNetZero Electrification of Heat Project](https://opennetzero.org/) & [ESC Open Data](https://es.catapult.org.uk/tools-and-labs/data/)
* **Purpose**: Cohort microdata of real UK heat pump homes on coldest winter days.

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `property_id` | String | Unique home identifier (e.g. `EoH_Home_001`). |
| `property_type` | Categorical | Dwelling form (`Detached`, `Semi-Detached`, `Terraced`, `Bungalow`). |
| `epc_band` | Categorical | Energy efficiency band (`C`, `D`, `E`, `F`). |
| `heat_pump_type` | Categorical | System type (`ASHP` = Air Source, `GSHP` = Ground Source, `Hybrid`). |
| `coldest_day_min_outdoor_temp_C` | Float | Minimum recorded outdoor temperature on the coldest trial day ($^\circ\text{C}$). |
| `coldest_day_mean_indoor_temp_C` | Float | 24-hour mean indoor temperature across the property ($^\circ\text{C}$). |
| `coldest_day_overnight_min_indoor_temp_C` | Float | Lowest recorded indoor temperature during overnight hours ($^\circ\text{C}$). |
| `wall_u_value` | Float | Thermal transmittance of external walls ($\text{W}/\text{m}^2\text{K}$). |
| `window_u_value` | Float | Thermal transmittance of glazing ($\text{W}/\text{m}^2\text{K}$). |
| `seasonal_cop` | Float | Seasonal Coefficient of Performance (heat output / electrical input). |

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
| `current_energy_rating` | Categorical | Standard SAP EPC Rating (`A` through `G`). |
| `current_energy_efficiency` | Integer ($1 - 100$) | Numerical Energy Efficiency Score ($0 - 100$). |
| `glaz_type` | Categorical | Window glazing type (`single glazing`, `double glazing`, `triple glazing`). |
| `walls_description` | Text | Physical wall insulation description (e.g. `Cavity wall, filled cavity`). |
| `total_floor_area` | Float | Usable floor area in square meters ($\text{m}^2$). |
| `postcode` | String | Truncated postcode sector. |

---

## 3. `ideal_household_temp_humidity_sample.csv` [Per Brief - Stretch Goal]
* **Source**: IDEAL Household Energy Dataset (University of Edinburgh)
* **Official URL**: [Edinburgh DataShare IDEAL Repository](https://datashare.ed.ac.uk/handle/10283/3647)
* **Purpose**: Provides real high-resolution indoor room temperature and relative humidity timeseries to evaluate dew points and damp risk.

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
* **Purpose**: Essential for Task 1. Provides freezing outdoor weather conditions to compute surface temperature and dew point margins ($T_{surface} - T_{dew\_point}$).

### Key Columns & Data Dictionary
| Column Name | Type | Description & Units |
| :--- | :--- | :--- |
| `time` | ISO 8601 UTC | Hourly timestamp during freezing winter cold spell. |
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
