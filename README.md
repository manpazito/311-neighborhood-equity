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

````

---

## Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-org-or-user>/311-neighborhood-equity.git
   cd 311-neighborhood-equity
    ```

2. **Create a virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate      # (Mac/Linux)
   venv\Scripts\activate         # (Windows)
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Run scripts**

   ```bash
   python scripts/clean_data.py
   python scripts/analyze_data.py
   ```

---

## Collaboration Guidelines

We are a 3-person team working in parallel on different parts of the project.
To keep everything organized and avoid conflicts:

### Branch Workflow

* `main` → stable, reviewed work only
* `dev` → staging branch for merging team contributions
* Each member creates their own feature branch:

  * `leslie-viz/` for figures and maps
  * `felix-analysis/` for cleaning and analysis
  * `manuel-report/` for documentation and writing

### Workflow Steps

1. **Pull latest changes** before starting work:

   ```bash
   git pull origin dev
   ```
2. **Create a new branch** for your task:

   ```bash
   git checkout -b <your-branch-name>
   ```
3. **Commit frequently** with clear messages:

   ```bash
   git commit -m "Cleaned ACS data and added tract join"
   ```
4. **Push and open a Pull Request (PR)** to `dev`:

   ```bash
   git push origin <your-branch-name>
   ```
5. **Review Pull Requests** from teammates before merging.

## 📄 License

This project is for academic and educational use.
Feel free to adapt or reference with proper attribution.