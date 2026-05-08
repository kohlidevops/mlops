# 🍷 Wine Dataset Versioning with DVC + AWS S3

This project demonstrates how to use **DVC (Data Version Control)** to track dataset changes and store large files in **AWS S3**, while keeping Git lightweight.

---

## 🚀 Tech Stack

* Python (venv)
* DVC (Data Version Control)
* AWS S3 (Remote Storage)
* Git & GitHub

---

## 📂 Project Structure

```
wine_prediction_demo/
│── data/
│   ├── wine_sample.csv
│   ├── wine_sample.csv.dvc
│
│── .dvc/
│── .gitignore
│── README.md
```

---

## ⚙️ Step 1: Setup Virtual Environment

```bash
python -m venv .venv
```

### Activate Environment

**Windows (Git Bash):**

```bash
source .venv/Scripts/activate
```

**Windows (CMD):**

```cmd
.venv\Scripts\activate
```

---

## 📦 Step 2: Install Dependencies

```bash
python -m pip install dvc dvc_s3
```

---

## 🔧 Step 3: Initialize DVC

```bash
dvc init
```

This creates:

* `.dvc/` folder
* `.dvc/config`

---

## 📊 Step 4: Add Dataset to DVC

```bash
dvc add data/wine_sample.csv
```

This generates:

* `wine_sample.csv.dvc` → tracks dataset version
* Updates `.gitignore` → prevents large file upload to Git

---

## 📝 Step 5: Track Changes in Git

```bash
git add data/wine_sample.csv.dvc .gitignore
git commit -m "Add dataset with DVC tracking"
```

---

## ☁️ Step 6: Configure AWS S3 Remote

```bash
dvc remote add -d wineremote s3://latchu-mlops-dvc-bucket
```

---

## 🔐 Step 7: Configure AWS CLI

```bash
aws configure
```

Provide:

* AWS Access Key
* Secret Key
* Region (e.g., ap-south-1)

---

## ⬆️ Step 8: Push Data to S3

```bash
dvc push
```

✅ Data is now stored in S3
✅ Git only tracks metadata (.dvc file)

---

## 🔄 Step 9: Update Dataset Version

Whenever dataset changes:

```bash
# Edit dataset
vim data/wine_sample.csv

# Track new version
dvc add data/wine_sample.csv

# Commit changes
git commit -am "Updated dataset version"

# Push to S3
dvc push
```

---

## 📄 Example `.dvc` File

```yaml
outs:
- md5: <hash>
  size: <file_size>
  path: data/wine_sample.csv
```

---

## 🎯 Key Benefits

* Version control for datasets (like Git for data)
* No large files in GitHub
* Easy rollback to previous dataset versions
* Scalable storage using S3

---
