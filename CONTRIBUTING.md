# Contributing Guide

**Goal:**
Everyone works in the `dev` branch.
We only merge `dev` → `main` after review.
Keep commits small, messages clear, and never push huge data directly.

---

## 📁 Project Structure

```
311-neighborhood-equity/
├─ data/        # raw + processed data (large files stay local or LFS)
├─ scripts/     # notebooks and Python scripts
├─ figures/     # plots, maps, visualizations
├─ reports/     # notes and writeups
├─ requirements.txt
├─ .env         # local settings (not committed)
└─ README.md
```

---

## Setup (first time only)

### 1. Install Git LFS *(before cloning)*

Some project data uses **Git Large File Storage (LFS)**.
Install and enable it once so large files download automatically.

**Fedora / Linux**

```bash
sudo dnf install git-lfs && git lfs install
```

**macOS**

```bash
brew install git-lfs && git lfs install
```

**Windows (PowerShell)**

```powershell
choco install git-lfs
git lfs install
```

If you already cloned before installing:

```bash
git lfs pull
```

---

### 2. Clone the repo

```bash
cd ~/projects
git clone https://github.com/manpazito/311-neighborhood-equity.git
cd 311-neighborhood-equity
```

---

### 3. Install Python requirements

```bash
pip install -r requirements.txt
```

---

### 4. Create your `.env` file

Each teammate makes their own `.env` (not pushed to GitHub):

```bash
# .env
API_KEY=your_api_key_here
DATA_PATH=./data/
MAPBOX_TOKEN=your_mapbox_token_here
```

In Python, load it like this:

```python
from dotenv import load_dotenv
import os
load_dotenv()
API_KEY = os.getenv("API_KEY")
```

---

## Workflow

1. **Go to the repo**

   ```bash
   cd ~/projects/311-neighborhood-equity
   ```

2. **Switch to and update `dev`**

   ```bash
   git checkout dev
   git pull origin dev
   ```

3. **Work normally**

   * Edit notebooks or scripts in `scripts/`
   * Add plots or figures
   * Avoid committing very large files directly

4. **Stage your changes**

   ```bash
   git add .
   ```

   or specific files:

   ```bash
   git add scripts/clean_data.py figures/map1.png
   ```

5. **Commit with a short, clear message**

   ```bash
   git commit -m "clean: standardized 311 CSV columns"
   ```

6. **Push to GitHub**

   ```bash
   git push origin dev
   ```

7. **Make a Pull Request**

   * Go to the repo on GitHub
   * Click **“Compare & pull request”**
   * Base branch: `main` → Compare: `dev`
   * Add a short description of what changed

---

## Handling Large Data Files

Never push large files 500 MB + files directly.

### Option A – Shared Drive (default)

* Store big files (e.g., `311_Cases_2023.csv`, `serv_req_cleaned.parquet`) in a shared Google Drive or OneDrive folder [here](https://drive.google.com/drive/folders/1-8gLff4e4engZ5tkt-4zM_JgbdhAp56Q?usp=drive_link).
* Keep local copies in:

  * `data/raw/` → original
  * `data/processed/` → cleaned
* These folders are ignored in `.gitignore`.
* Add small `README.md` files explaining where to get the data.

### Option B – Git LFS (when agreed)

If the team decides to version data inside GitHub:

```bash
git lfs track "data/**"
git add .gitattributes
git commit -m "chore: track data files with LFS"
git push origin dev
```

Everyone must have Git LFS installed, and note that GitHub LFS storage is limited.

---

## Commit Message Style

Use short, action-based messages. Here are some examples:

* `new data cleaning script`
* `join mismatch on tract_id`
* `update income choropleth`
* `update requirements.txt`

---

## Common Fixes & Troubleshooting

**A) Don’t see teammates’ work**

```bash
git checkout dev
git pull origin dev
```

**B) Changes not on GitHub**

```bash
git add .
git commit -m "message"
git push origin dev
```

**C) Wrong branch**

```bash
git branch
git checkout dev
git pull origin dev
```

**D) Merge conflict**

1. Open the conflicted file and pick the correct version
2. Then:

   ```bash
   git add path/to/file
   git commit -m "resolve: merge conflict"
   git push origin dev
   ```

**E) New library added**
After installing new packages:

```bash
pip freeze > requirements.txt
git add requirements.txt
git commit -m "deps: update requirements"
git push origin dev
```

**F) `.env` reminders**

* Never commit `.env`
* If you add a new key (like `MAPBOX_TOKEN`), tell the team

---

## Quick Reference

```bash
cd 311-neighborhood-equity
git checkout dev
git pull origin dev

# work, edit, save
git add .
git commit -m "short: describe change"
git push origin dev
```

Then open a **Pull Request from `dev` → `main`** when the work is ready to review or present.