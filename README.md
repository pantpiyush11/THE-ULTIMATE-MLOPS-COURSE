# 🚀 THE-ULTIMATE-MLOPS-COURSE

> *Documenting my day-by-day progress through MLOps — concepts, code snippets, and honest notes from someone learning in public.*

---

## 📚 Table of Contents
- [Data Versioning using DVC](#1-data-versioning-using-dvc)

---

## 4. Data Versioning using DVC

Every ML pipeline run generates **artifacts** — processed data chunks passed between modules.
As data formats change and models retrain, tracking these versions becomes critical.

> ❌ **Git fails here** — it can't handle large data files.
> ✅ **DVC solves this** — it versions data and artifacts the way Git versions code.

Every **Git commit (SHA)** links to a corresponding **DVC snapshot** — so you always know which data ran with which code.

---

### ⚙️ Setup

```bash
# Install DVC
pip install dvc

# Initialise DVC inside your git repo
dvc init

# Create remote storage directory
mkdir S3

# Point DVC to remote storage
dvc remote add -d myremote S3
```

---

### 📦 Track Your Data

```bash
# Hand data tracking from Git to DVC
git rm -r --cached 'data'
git commit -m "stop tracking data"

# Tell DVC to track your data folder
dvc add data/

# Commit the DVC tracking file
git add .gitignore data.dvc
git commit -m "dvc tracking data"

# Push code and data
git push origin main
dvc push
```

---

### ⏪ Restore a Previous Version

```bash
git checkout <commit-sha>
dvc pull
```

---

<div align="center">

*Learning in public. One concept at a time.*

</div>
