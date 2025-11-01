# 311-Neighborhood-Equity

This project analyzes the relationship between **311 service requests** and **household income** across San Francisco neighborhoods (2010–2020).
It explores how patterns of civic reporting vary by income level to highlight potential disparities in access to city services.

---

## Overview

* **Goal:** Examine whether income correlates with reporting frequency of non-emergency 311 requests.
* **Data Sources:**

  * San Francisco 311 Service Requests (open data portal)
  * U.S. Census American Community Survey (ACS 5-Year Estimates)
* **Methods:**

  * Data cleaning, geospatial joins by neighborhood and census tract
  * Statistical summaries and map visualizations
  * Exploration of reporting intensity vs. median income

---

## Repository Structure

```
311-neighborhood-equity/
├── data/         # Raw and processed datasets (311 + ACS)
├── figures/      # Maps, charts, and visualization outputs
├── scripts/      # Python notebooks and analysis scripts
└── reports/      # Notes and writeups
```

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-user-or-org>/311-neighborhood-equity.git
cd 311-neighborhood-equity
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. (Optional) Download data

Large raw data files are not stored in the repo.
You can obtain them from:

* [SF Open Data – 311 Service Requests](https://data.sfgov.org/)
* [U.S. Census Bureau – ACS Data API](https://www.census.gov/data/developers/data-sets/acs-5year.html)

Place datasets under:

```
data/raw/
```

### 4. Run analysis

Example:

```bash
python scripts/clean_data.py
python scripts/analyze_data.py
```

or open the provided notebooks (e.g., `data_analysis.ipynb`) in Jupyter Lab or VS Code.

---

## Example Outputs

* Choropleth maps of 311 request density by neighborhood
* Scatterplots of household income vs. request frequency
* Summary tables comparing service request types across income groups

Example figure (from `figures/`):

```
Income_vs_311_Map.png
```

---

## Tools & Libraries

* **Python 3**
* pandas, geopandas, numpy
* matplotlib / seaborn / plotly
* shapely, fiona
* jupyter / notebook

---

## License

This project is released under the [BSD 2-Clause License](./LICENSE)
for academic and educational use.
Please attribute **Leslie Veliz**, **Felix Zhang**, and **Manuel A. Martinez Garcia** when reusing or referencing this work.

---

## Citation

If referencing this project in academic or professional contexts, please cite:

> Veliz, L., Zhang, F., & Martinez Garcia, M. A. (2025). *311 Neighborhood Equity: Exploring Civic Reporting and Income Disparities in San Francisco*.
> University of California, Berkeley.