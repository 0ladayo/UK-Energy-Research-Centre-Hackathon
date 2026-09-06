# UK Energy Research Centre (UKERC) Hackathon 2026

Welcome to the **UK Energy Research Centre Hackathon** workspace! This repository contains curated, real-world energy datasets, starter analysis notebooks, and data schemas designed to support participants tackling the UK's most critical energy transition challenges.

---

## Quick Start: Launch in Google Colab

Click any badge below to instantly open the corresponding starter notebook in a free, ready-to-code cloud environment:

| Track | Challenge Area | Starter Notebook |
| :--- | :--- | :--- |
| **Track 02** | **Energy Poverty & Equity** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/0ladayo/UK-Energy-Research-Centre-Hackathon/blob/main/notebooks/track_02_energy_poverty_equity_starter.ipynb) |
| **Track 03** | **Future Electricity Systems** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/0ladayo/UK-Energy-Research-Centre-Hackathon/blob/main/notebooks/track_03_future_electricity_systems_starter.ipynb) |
| **Track 04** | **Heat, Buildings & Decarbonisation** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/0ladayo/UK-Energy-Research-Centre-Hackathon/blob/main/notebooks/track_04_heat_buildings_decarbonisation_starter.ipynb) |

> **Note**: When running inside Google Colab, each notebook automatically clones the repository and loads the data into the runtime session.

---

## Challenge Tracks Overview

### Track 02: Energy Poverty & Equity
* **Objective**: Investigate geographic, socio-economic, and dwelling-level disparities in energy poverty and consumption across England and Wales.
* **Datasets**:
  * Sub-Regional Fuel Poverty Statistics (DESNZ / LILEE indicator)
  * English Index of Multiple Deprivation (IMD 2019)
  * National Energy Efficiency Data-Framework (NEED 50k dwelling sample)
  * Sub-national Domestic Gas & Electricity LSOA Consumption
  * ONS Lower Layer Super Output Area (LSOA) Boundary Polygon GeoJSON & CSV
* **Key Questions**: Which communities face acute fuel poverty risks? How do deprivation and dwelling age correlate with median household gas and electricity bills?

### Track 03: Future Electricity Systems
* **Objective**: Model national grid flexibility, dynamic tariffs, consumer price incentives, and renewable generation dynamics.
* **Datasets**:
  * Octopus Agile Half-Hourly Dynamic Electricity Tariffs (Full Year 2024)
  * National Grid Carbon Intensity API (30-min actual vs. forecast emissions)
  * Elexon BMRS Half-Hourly Electricity Generation by Fuel Type (Wind, Solar, Gas, Nuclear, Biomass, Hydro, Storage)
  * Sub-national Annual Electricity Consumption Statistics
* **Key Questions**: How can smart flexibility and storage capitalize on negative-price plunge events? How strong is the correlation between grid carbon intensity and wholesale-linked consumer tariffs?

### Track 04: Heat, Buildings & Decarbonisation
* **Objective**: Evaluate heat pump real-world efficiency, building envelope thermal performance, and winter cold snap resilience.
* **Datasets**:
  * Electrification of Heat (EoH) Project Trial Summary (Seasonal Performance Factor SPF / COP)
  * IDEAL Household IoT Sensor Telemetry (Room temperature & relative humidity)
  * Open EPC Domestic England Sample (Current vs. potential energy ratings, fabric insulation)
  * UK Winter Cold Snap Hourly Weather (December 2022 sub-zero temperature profiles)
* **Key Questions**: What is the real-world efficiency distribution of air-source vs. ground-source heat pumps? How rapidly do UK homes lose heat during extreme sub-zero cold spells?

---

## Data Documentation

For detailed column descriptions, units, formulas, source links, and reproduction scripts, see:
👉 [**DATASET_DICTIONARY.md**](./DATASET_DICTIONARY.md)

---

## Repository Structure

```text
UK-Energy-Research-Centre-Hackathon/
├── README.md                          # Hackathon guide & 1-click Colab badges
├── DATASET_DICTIONARY.md               # Full schema, units, and methodology
├── notebooks/                         # Ready-to-run starter Jupyter notebooks
│   ├── track_02_energy_poverty_equity_starter.ipynb
│   ├── track_03_future_electricity_systems_starter.ipynb
│   └── track_04_heat_buildings_decarbonisation_starter.ipynb
├── Energy Poverty & Equity/           # Track 02 datasets
├── Future Electricity Systems/        # Track 03 datasets
└── Heat, Buildings & Decarbonisation/ # Track 04 datasets
```

---

## Local Development (Optional)

If you prefer working locally rather than in Google Colab:

```bash
# Clone the repository
git clone https://github.com/0ladayo/UK-Energy-Research-Centre-Hackathon.git
cd UK-Energy-Research-Centre-Hackathon

# Install recommended packages
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```
