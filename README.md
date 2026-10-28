# 🌾 FarmStack — Field Shift: Adapting Farms with NASA Data

[![NASA Space Apps Challenge 2026](https://img.shields.io/badge/NASA%20Space%20Apps-2026-blue.svg)](https://www.spaceappschallenge.org/2026/challenges/field-shift-adapting-farms-with-nasa-data/)
[![Challenge](https://img.shields.io/badge/Challenge-Field%20Shift-orange.svg)](https://www.spaceappschallenge.org/2026/challenges/field-shift-adapting-farms-with-nasa-data/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-In%20Development-green.svg)]()

> **A smart agricultural decision-support platform empowering farmers to explore resilient crop rotation strategies, protect soil health, and adapt to climate extremes using NASA Earth Observations, local soil profiles, and farmer priorities.**

---

## 📌 Table of Contents

- [Overview](#-overview)
- [The Challenge](#-the-challenge)
- [Our Solution](#-our-solution)
- [Key Features](#-key-features)
- [NASA Earth Observation Datasets](#-nasa-earth-observation-datasets)
- [System Architecture](#-system-architecture)
- [Technology Stack](#-technology-stack)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Running the Application](#running-the-application)
- [User Workflow](#-user-workflow)
- [Roadmap](#-roadmap)
- [Team & Contributions](#-team--contributions)
- [Acknowledgments](#-acknowledgments)
- [License](#-license)

---

## 🌍 Overview

Farmers globally are on the frontlines of a shifting climate:
- Unpredictable rainfall patterns and severe droughts
- Escalating temperature anomalies and heat stress
- Soil degradation, erosion, and declining organic matter
- Depleting groundwater and regional water shortages

Selecting the right crop rotation sequence is one of the most powerful natural mechanisms to build soil organic matter, break pest cycles, and optimize water utilization. However, traditional rotation choices often rely on historical weather assumptions that no longer hold true.

**FarmStack** bridges the gap between state-of-the-art satellite remote sensing and everyday farm management, delivering an intuitive decision-support tool tailored to hyper-local realities.

---

## 🎯 The Challenge

**Challenge Title:** [Field Shift: Adapting Farms with NASA Data](https://www.spaceappschallenge.org/2026/challenges/field-shift-adapting-farms-with-nasa-data/)  
**Event:** 2026 NASA Space Apps Challenge  
**Difficulty:** Intermediate / Advanced  
**Subjects:** Earth Science, Software, Arts & Multimedia  

> *"Create a decision‑support tool that uses NASA Earth observations along with local soil information, crop characteristics, and farmer priorities to help farmers explore rotation strategies that could strengthen soil health and adapt their farms to changing conditions."*

---

## 💡 Our Solution

FarmStack integrates four foundational pillars into an intelligent recommendation and scenario-exploration engine:

1. **NASA Earth Observations:** Real-time and historical climate, precipitation, temperature anomalies, and soil moisture data.
2. **Local Soil Dynamics:** Texture, pH, cation exchange capacity (CEC), nitrogen-phosphorus-potassium (NPK), and organic matter baseline.
3. **Crop & Legume Profiles:** Water requirements, root depth, nitrogen fixation potential, growing season days, and thermal tolerances.
4. **Farmer Priorities & Constraints:** Economic yield, market access, water availability, machinery capabilities, and risk tolerance.

Through an interactive dashboard, growers and agricultural advisors can simulate multi-year crop rotation sequences and visualize projections for:
- **Soil Health Index (SHI)** trajectory (organic matter accumulation, nitrogen replenishment)
- **Water Stress & Irrigation Footprint**
- **Climate Resilience Score** against simulated droughts, extreme heat, or floods
- **Projected Economic Stability & Diversification**

---

## ✨ Key Features

- 🛰️ **Hyper-Local NASA Data Ingestion:** Auto-fetches climate and soil parameters based on GPS field coordinates or parcel boundary polygons.
- 🔄 **Rotation Strategy Simulator:** Test custom sequences (e.g., *Maize ➔ Legume/Cover Crop ➔ Small Grain ➔ Fallow/Pasture*) across 3–5 year horizons.
- 🌱 **Soil Health Trajectory Forecaster:** Simulates organic carbon changes, root biomass depth, and erosion mitigation based on crop ground cover.
- 💧 **Water Budget & Drought Risk Analytics:** Matches crop water demand curves against historical & projected rainfall from NASA GPM and soil moisture from SMAP.
- ⚖️ **Multi-Objective Optimization Engine:** Suggests optimal rotations balancing ecological resilience with farmer-selected priorities (profit vs. water conservation vs. soil restoration).
- 📱 **Accessible & Farmer-First UI:** Designed for field usability with plain-language explanations, visual trade-off sliders, and downloadable PDF reports.

---

## 🛰️ NASA Earth Observation Datasets

FarmStack leverages curated NASA Earth Science missions and products:

| Dataset / Mission | Parameter / Usage | Purpose in FarmStack |
| :--- | :--- | :--- |
| **NASA POWER Project** | Solar radiation, daily temperatures, precipitation, relative humidity | Agroclimatology baselines and crop heat/chill unit calculations |
| **SMAP** *(Soil Moisture Active Passive)* | Surface (top 5 cm) and root-zone soil moisture | Assessing current field moisture capacity & planting windows |
| **GPM** *(Global Precipitation Measurement / IMERG)* | Multi-satellite precipitation estimates & rainfall intensity | Historical drought analysis and extreme weather frequency |
| **MODIS / VIIRS (Terra & Aqua)** | NDVI, EVI (Vegetation indices) & Land Surface Temperature (LST) | Historical biomass trends and baseline field productivity |
| **ECOSTRESS** | Evapotranspiration (ET) & Evaporative Stress Index (ESI) | Monitoring plant water stress and fine-scale thermal stress |
| **OpenET / Landsat** | Field-scale evapotranspiration and consumptive water use | Calibrating crop water consumption in rotation models |

---

## 🏗️ System Architecture

```text
               +-------------------------------------------+
               |          Farmer / Advisor Input           |
               | (Field Polygon, Soil Tests, Preferences)  |
               +---------------------+---------------------+
                                     |
                                     v
+-----------------------+   +-------------------+   +------------------------+
|   NASA Earth Data     |   |   Local Soil DB   |   |   Crop Knowledge Base  |
| (POWER, SMAP, GPM,    |-->|  (SoilGrids /     |-->| (Water demand, roots,  |
|  MODIS, ECOSTRESS)    |   |   user soil test) |   |  N-fixation, lifecycle)|
+-----------+-----------+   +---------+---------+   +-----------+------------+
            |                         |                         |
            +--------------------+----+-------------------------+
                                 |
                                 v
               +-----------------------------------+
               |    Rotation Simulation Engine     |
               |  - Soil Health Trajectory Model   |
               |  - Water Deficit & Climate Stress |
               |  - Multi-Objective Ranking        |
               +-----------------+-----------------+
                                 |
                                 v
               +-----------------------------------+
               |        Interactive Dashboard      |
               |  - Scenario Comparison Cards     |
               |  - 5-Year Resilience Metrics      |
               |  - Actionable Field Schedule      |
               +-----------------------------------+
```

---

## 🛠️ Technology Stack

- **Frontend:** Modern Web UI (Vite / React / Vanilla Web Components, TailwindCSS / CSS3, Chart.js / Recharts, Leaflet / Mapbox for spatial field boundary selection)
- **Backend / API:** FastAPI / Node.js
- **Data & Geospatial Processing:** Python (`rasterio`, `geopandas`, `xarray`, `shapely`, `requests`)
- **NASA Data APIs:** NASA POWER API, NASA Earthdata CMR, NASA GIBS tile services
- **Database / Storage:** PostgreSQL with PostGIS / SQLite (local testing)

---



## 📋 User Workflow

1. **Pinpoint Your Field:** Select your geographic location by pin drop, address search, or parcel polygon upload (GeoJSON/KML).
2. **Define Baseline Conditions:** Confirm soil characteristics (auto-filled via regional soil data or customized with soil test numbers).
3. **Set Farm Goals:** Choose what matters most:
   - 🛡️ *Maximum Soil Regeneration*
   - 💧 *Severe Water Conservation*
   - 🌾 *Economic Crop Diversification*
   - ⚖️ *Balanced Resilient Strategy*
4. **Compare Rotation Plans:** View side-by-side comparisons of 3–5 year rotation scenarios with predicted soil carbon growth, drought vulnerability scores, and projected water savings.
5. **Take Action:** Export a detailed seasonal rotation schedule with NASA-backed risk alerts and cover crop recommendations.

---

## 🗺️ Roadmap

- [x] Challenge ideation and NASA data source mapping
- [ ] Implement NASA POWER & SMAP API ingestion pipeline
- [ ] Develop crop rotation multi-criteria recommendation algorithm
- [ ] Build interactive spatial parcel selector & map visualizer
- [ ] Add offline support / low-bandwidth mode for rural field connectivity
- [ ] Enable multi-language support for international farming communities

---

## 👥 Team & Contributions

Developed for the **2026 NASA Space Apps Challenge** by **Team FarmStack**:

| Name | Role | Responsibilities |
| :--- | :--- | :--- |
| **[Member Name]** | Team Lead / Software Engineer | Architecture & Full-stack Development |
| **[Member Name]** | Earth Observation / Data Specialist | NASA Datasets Integration & Modeling |
| **[Member Name]** | Agronomy & Research | Crop profiles & Soil Health Index formulation |
| **[Member Name]** | UI/UX & Multimedia | Dashboard Design, Data Visualizations & Storytelling |

---

## 🙏 Acknowledgments

- **NASA Space Apps Challenge Organizers & Mentors** for providing the platform and inspiration.
- **NASA Earth Science Division** and the **NASA Applied Sciences Program (Agriculture)** for open access to Earth Observation data.
- Global farming communities whose resilience inspires this project.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
