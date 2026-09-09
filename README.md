# Energy Research Hackathon 2026

Welcome to the **Energy Research Hackathon 2026** workspace! 

This hackathon is sponsored by **UKERC** (UK Energy Research Centre), **Supergen Energy Networks**, **SuperAIRE**, and **EDRC** (Energy Demand Research Centre).

This repository contains real open datasets, starter notebooks, and a data dictionary to support participants across the three hackathon challenge tracks.

---

## Quick Start: Launch in Google Colab

Click any badge below to open the starter notebook instantly in your browser with free cloud compute:

| Track | Challenge Title | 1-Click Cloud Workspace |
| :--- | :--- | :--- |
| **Track 01** | **Energy Poverty & Equity** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/0ladayo/UK-Energy-Research-Centre-Hackathon/blob/main/notebooks/track_01_energy_poverty_equity_starter.ipynb) |
| **Track 02** | **Future Electricity Systems** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/0ladayo/UK-Energy-Research-Centre-Hackathon/blob/main/notebooks/track_02_future_electricity_systems_starter.ipynb) |
| **Track 03** | **Heat, Buildings & Decarbonisation** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/0ladayo/UK-Energy-Research-Centre-Hackathon/blob/main/notebooks/track_03_heat_buildings_decarbonisation_starter.ipynb) |

> **Note**: When running in Google Colab, each notebook automatically downloads the data and prepares your environment.

---

## Challenge Tracks & Problem Statements

### Track 01: Energy Poverty & Equity

* **Strategic Objective**: *Affordability & Justice*
* **Policy Context**: Aligned with the UK Government's **Warm Homes Plan**, the **LILEE** (Low Income Low Energy Efficiency) metric, and the **Warm Home Discount**.

#### The Problem
> **In which local neighbourhoods (LSOAs) is fuel poverty risk the highest when considering both low household income and energy-inefficient homes? If you had a fixed support budget, where should you spend it to reduce that risk the most?**

#### The Task:
1. **Link the data**: Connect sub-regional fuel poverty figures with Index of Multiple Deprivation (IMD 2019) scores at the neighbourhood (LSOA) level.
2. **Build a simple index**: Create an easy-to-explain score that ranks neighbourhoods by combined need.
3. **Choose an intervention**: Pick one home improvement (like insulation) or one bill-support scheme, and show which areas should get funded first and why.
4. **Evaluate fairness**: Identify who benefits, who gets missed, and what real-world barriers (such as landlord approval or lack of trust) might stop people from taking part.

* **Key Datasets**: DESNZ Sub-Regional Fuel Poverty (LILEE), English Indices of Deprivation 2019 (IMD), NEED 50k Property Sample, Sub-national LSOA Gas & Electricity Consumption.

---

### Track 02: Future Electricity Systems

* **Strategic Objective**: *Flexibility, Delivery & Geopolitical Resilience*
* **Policy Context**: Aligned with the **Clean Power 2030 Action Plan** and the **NESO Clean Power Pathway**.

#### The Problem
> **Using real British grid data, how much carbon (and cost) could be saved by shifting when electricity is used? What would it take to encourage consumers and businesses to make that shift?**

#### The Task:
1. **Examine grid patterns**: Look at 30-minute carbon intensity and electricity demand data over a recent period.
2. **Model a flexible load**: Choose one electricity use that can shift its timing without hurting its purpose (such as overnight EV charging, heat pump pre-heating, or a business process).
3. **Calculate carbon savings**: Compare carbon emissions between running the load at the worst time versus the cleanest time of day.
4. **Apply to a real community**: Pick one local authority area, evaluate what price signals or tariffs (like Octopus Agile) could trigger the shift, and consider who might be unfairly left behind if they cannot easily shift their habits.
5. **Geopolitical angle**: Show how shifting electricity use reduces reliance on imported gas and cross-border interconnectors during peak hours.

* **Key Datasets**: National Grid Carbon Intensity API, Elexon BMRS Generation by Fuel Type, Octopus Agile Half-Hourly Tariffs 2024, Sub-national Electricity Consumption.

---

### Track 03: Heat, Buildings & Decarbonisation

* **Strategic Objective**: *Delivery, Affordability & Healthy Homes*
* **Policy Context**: Aligned with **Awaab’s Law** (statutory rules requiring social landlords to fix damp and mould quickly) and the **Warm Homes Plan**.

#### The Problem
> **In real heat-pump homes, which properties are most at risk of condensation and mould on cold surfaces? Does that risk get hidden when using standard monthly averages compared to real, measured overnight lows?**

#### The Task:
1. **Calculate surface risk**: Estimate the risk of surface condensation in homes during the coldest winter days.
2. **Compare two methods**: Compare standard monthly averages (the Glaser method) against actual measured overnight freezing temperatures. Count how many homes flip from looking "safe" to being "at risk".
3. **Test key assumptions**: Check how outside winter weather and indoor humidity affect your results.
4. **Recommend practical actions**: Explain what retrofit teams, housing assessors, and social landlords should do differently to protect tenants from damp and cold.

* **Key Datasets**: Electrification of Heat (EoH) Performance Summary, IDEAL Household IoT Temperature & Humidity Sensors, Open EPC Domestic England Sample, UK Winter Cold Snap Hourly Weather (Dec 2022).

---

## Judging Criteria

Presentations will be judged on five balanced areas:
1. **Insight & Policy Relevance (25%)**: How well the solution addresses the challenge and its policy context.
2. **Correct Use of Real Data (25%)**: Honest use of real data, clear assumptions, and sensible calculations.
3. **Reproducibility & Transparency (20%)**: Re-runnable code or clear spreadsheets with no made-up numbers.
4. **Interdisciplinary Teamwork (15%)**: Collaboration across data, engineering, social science, and policy thinking.
5. **Clear Communication (15%)**: A 5-minute plain-English pitch that a non-specialist policymaker could understand and act on.

---

## Data Documentation

For detailed column descriptions, units, formulas, source links, and code snippets:  
👉 [**Read DATASET_DICTIONARY.md**](./DATASET_DICTIONARY.md)

---

## Repository Structure

```text
UK-Energy-Research-Centre-Hackathon/
├── README.md                          # Hackathon guide & 1-click Colab badges
├── DATASET_DICTIONARY.md               # Full data dictionary, units, and methodology
├── notebooks/                         # Ready-to-run starter Jupyter notebooks
│   ├── track_01_energy_poverty_equity_starter.ipynb
│   ├── track_02_future_electricity_systems_starter.ipynb
│   └── track_03_heat_buildings_decarbonisation_starter.ipynb
└── datasets/
    ├── Energy Poverty & Equity/           # Track 01 datasets
    ├── Future Electricity Systems/        # Track 02 datasets
    └── Heat, Buildings & Decarbonisation/ # Track 03 datasets
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
