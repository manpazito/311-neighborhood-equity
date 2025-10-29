# Contributing Guide

**Goal:** Everyone does their work in `dev` first. We only merge to `main` after review.

---
> Folder layout:
>
> ```
> 311-neighborhood-equity/
> ├─ data/      # raw/processed data (no secrets)
> ├─ scripts/   # Python notebooks & scripts
> ├─ figures/   # exported plots/maps
> └─ reports/   # notes & writeups
> ```

---

## 1) Everyday workflow (TL;DR checklist)

> **You do these steps at the start and end of each work session.**

1. Open a terminal inside the project folder: `cd 311-neighborhood-equity`
2. **Make sure you’re on `dev`:**

   ```bash
   git checkout dev
   ```
3. **Get the newest code from GitHub into `dev`:**

   ```bash
   git pull origin dev
   ```
4. Do your work (edit files in `data/`, `scripts/`, `figures/`, or `reports/`).
5. **See what changed:**

   ```bash
   git status
   ```
6. **Stage your changes:**

   * Add new/edited files:

     ```bash
     git add path/to/file1 path/to/file2
     # or: add everything you changed
     git add .
     ```
   * Remove files you deleted (so Git knows):

     ```bash
     git rm path/to/file_to_remove
     ```
7. **Commit with a short message:**

   ```bash
   git commit -m "short: what you changed (e.g., clean 311 CSV; add income join)"
   ```
8. **Upload your commits to the `dev` branch on GitHub:**

   ```bash
   git push origin dev
   ```
9. Tell the team in chat that you pushed.

> **Rule of thumb:** small, frequent commits (1 logical idea per commit) are best.

---

## 2) Recommended: Personal feature branches (safer)

If you’re doing bigger changes, work on your own branch based off `dev`, then merge back into `dev`.

1. **Start from up‑to‑date `dev`:**

   ```bash
   git checkout dev
   git pull origin dev
   ```
2. **Create and switch to your branch:**

   ```bash
   git checkout -b feat/<your-name>-<short-topic>
   # example: feat/miriam-clean-calls
   ```
3. Do work → `git add` → `git commit -m "..."` (repeat as needed).
4. **Push your branch (first time needs -u):**

   ```bash
   git push -u origin feat/<your-name>-<short-topic>
   ```
5. On GitHub, open a **Pull Request** to merge your feature branch **into `dev`**. Ask 1 teammate to review.
6. After approval, **merge into `dev`**. (We only merge `dev` → `main` for releases/milestones.)

---

## 3) How we handle `main` vs `dev`

* **`main`** = clean, presentation‑ready state. Protected. Do **not** commit directly.
* **`dev`** = active collaboration branch. Everyone pushes here or opens PRs into it.
* **Flow:** feature branches → PR → `dev` → (periodically) PR → `main`.

---

## 4) File naming & organization

* Use **lowercase_with_underscores**. Examples:

  * `data/raw/311_requests_2015.csv`
  * `data/processed/311_sf_2010_2020.parquet`
  * `scripts/clean_311_to_acs_join.py`
  * `figures/choro_income_311_rate.png`
* Never commit secrets, credentials, or huge raw dumps (>100MB). If needed, coordinate first.

---

## 5) Common commands (copy/paste)

**Switch to a branch:**

```bash
git checkout dev
git checkout main
git checkout feat/<your-branch>
```

**Create a branch and switch to it:**

```bash
git checkout -b feat/<your-branch>
```

**See changes:**

```bash
git status
```

**Stage all changes:**

```bash
git add .
```

**Stage specific files:**

```bash
git add scripts/clean_311_to_acs_join.py figures/map1.png
```

**Unstage a file (if you added by accident):**

```bash
git restore --staged path/to/file
```

**Remove a tracked file:**

```bash
git rm path/to/file
```

**Commit:**

```bash
git commit -m "short: explain what you changed"
```

**Pull latest `dev`:**

```bash
git checkout dev
git pull origin dev
```

**Push to `dev`:**

```bash
git push origin dev
```

---

## 6) Typical issues & quick fixes

**A) “Everything is up to date” but you don’t see teammates’ work**

```bash
git checkout dev
git pull origin dev
```

Make sure you’re actually on `dev`.

**B) First push of a new branch complains about upstream**

```bash
git push -u origin feat/<your-branch>
```

**C) Merge conflict (two people edited the same lines)**

1. Try to pull:

   ```bash
   git pull origin dev
   ```
2. Git will mark conflict files with `<<<<<<`, `======`, `>>>>>>`.
3. Open those files, decide which pieces to keep, then:

   ```bash
   git add path/to/conflicted_file
   git commit -m "resolve: merge conflicts in <file>"
   git push origin dev
   ```

Ask a teammate for help if stuck.

**D) You have local edits but want fresh `dev`**

```bash
git stash          # temporarily save your edits
git pull origin dev
git stash pop      # re‑apply your edits
```

**E) Accidentally worked on `main`**

```bash
git checkout dev
# optionally cherry‑pick your commits or create a feature branch:
git checkout -b feat/move-work-from-main
```

Then open a PR into `dev`.

---

## 7) Commit message style (simple)

* Start with a short verb: `add`, `fix`, `clean`, `refactor`, `doc`, `plot`, `data`.
* Keep it under ~70 chars.
* Examples:

  * `clean: drop null service requests and standardize columns`
  * `plot: add income vs 311 rate choropleth`
  * `data: add ACS 2013 tract income table`

---

## 8) Pull Request (PR) checklist (into `dev`)

* [ ] Branch up to date with `dev` (`git pull origin dev` on your branch)
* [ ] Runs without errors (scripts/notebooks)
* [ ] Clear description of what changed and how to test
* [ ] At least 1 teammate reviewed

We merge `dev` → `main` after we agree it’s presentation‑ready.

---

## 9) Glossary (plain English)

* **Repository (repo):** The project folder tracked by Git.
* **Branch:** A named line of work. `main` is the clean one; `dev` is the shared work area.
* **Commit:** A saved snapshot of your changes with a message.
* **Push:** Upload your local commits to GitHub.
* **Pull:** Download teammates’ commits from GitHub.
* **Merge conflict:** When two commits change the same lines; you must choose what to keep.

---

## 10) Quick start (print me!)

#### From terminal, enter:
```bash
cd 311-neighborhood-equity
```
##### start work
```bash
git checkout dev
git pull origin dev
```

##### edit files in data/, scripts/, figures/, reports/
```bash
git add .
git commit -m "short: what changed"

git push origin dev
```

If you get stuck, ping the team and paste the exact error message.
