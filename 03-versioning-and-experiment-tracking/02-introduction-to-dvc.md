# 🧠 What is DVC (Easy Understanding)

👉 Think like this:

> DVC = Git, but for large data

---
### ❌ Problem with Git

Git is good for:

- Code
- Small files

But not for:

- Big datasets
- Model files

👉 If you store big data in Git:

> Repo becomes slow and heavy

---
### ✅ What DVC Does

👉 DVC solves this by:

- Tracking data versions
- Storing actual data outside Git
- Keeping Git repo small

---
### 📦 Simple Idea

👉 With DVC:

- Git stores → small pointer file (.dvc)
- Real data → stored in cloud (S3, etc.)

---
### 🍷 Example (Wine Prediction)

You have:

- wine_data_sample.csv (data)
- train.py (code)

---
### ❌ Without DVC

- CSV stored in Git
- Repo becomes heavy

---
### ✅ With DVC

- Git stores:

```
wine_data_sample.csv.dvc
```

Actual CSV goes to:

- S3 / cloud storage

👉 Git stays clean ✅

---
### 🔄 How DVC Works (Simple Flow)

#### 1. Track dataset

```
dvc add wine_data_sample.csv
```

👉 Creates .dvc file

#### 2. Save in Git

```
git add wine_data_sample.csv.dvc
git commit
```

#### 3. Connect storage (like S3)

```
dvc remote add -d myremote s3://mybucket/dvcstore
```

#### 4. Upload data

```
dvc push
```

👉 Data goes to S3

#### 5. Get data anytime

```
dvc pull
```

👉 Anyone can download same dataset

---
### 🔥 Final Simple Understanding

👉 DVC = tracks big data without storing it in Git

---
### ⚡ One-Line Memory

👉

- Git tracks code
- DVC tracks data

---
### 💡 Why it’s useful

- Repo stays fast
- Data is versioned
- Anyone can reproduce same project
