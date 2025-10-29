# 311-Neighborhood-Equity

Exploring the relationship between 311 service requests and household income across San Francisco neighborhoods (2010–2020).
This project examines how patterns of civic reporting vary by income level to highlight potential disparities in access to city services.

---

## Repository Structure

```
311-neighborhood-equity/
├── data/         # Raw and processed datasets (311 + ACS)
├── figures/      # Maps, charts, and other visual outputs
├── scripts/      # Python scripts for cleaning, analysis, and mapping
└── reports/      # Drafts, notes, and final reports
```

---

## Getting Started

1. **Clone the repository**

   ```bash
   git clone https://github.com/<your-org-or-user>/311-neighborhood-equity.git
   cd 311-neighborhood-equity
   ```

2. **Create a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate      # (Mac/Linux)
   venv\Scripts\activate         # (Windows)
   ```

3. **Install dependencies**

   ```bash
   pip3 install -r requirements.txt
   ```

4. **Run scripts**

   ```bash
   python3 scripts/clean_data.py
   python3 scripts/analyze_data.py
   ```

---

## Collaboration Guidelines

To keep everything organized and avoid conflicts, please refer to the **[Contributing Guide](./CONTRIBUTING.md)** for step-by-step collaboration instructions.

This guide includes:

* How to switch to and pull from `dev`
* How to add, remove, commit, and push changes
* Recommended branch naming and PR workflow
* Troubleshooting common Git issues

---

## License

This project is released under the [BSD 2-Clause License](./LICENSE)  
for academic and educational purposes.  
You are welcome to reuse, adapt, or reference this work with proper attribution  
to **Leslie Veliz, Felix Zhang, and Manuel A. Martinez Garcia**.
