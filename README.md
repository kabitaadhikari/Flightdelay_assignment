# Flight Delay Prediction — Part A (On-Premises)

This repository contains the **on-premises** machine-learning pipeline for predicting whether a flight will arrive **15+ minutes late** (`target = 1`).  

## What this project does
- Loads & filters BTS On-Time Performance data (2014–2018 subset)
- EDA: class balance and delay patterns by Month / Hour / DOW / Airline / Airport
- Features: select relevant columns, treat `DepHourOfDay` as categorical, one-hot encode
- Baseline model: Logistic Regression with `class_weight="balanced"`
- Evaluation: Confusion matrix, ROC curve, and metrics (Accuracy, Precision, Recall, Specificity, F1, ROC-AUC)
- Exports **combined_csv_v1.csv** for Part B (not checked into Git)

## Repo layout
- `onpremises.ipynb` — main notebook (run top→bottom; relative paths)
- `requirements.txt` — Python dependencies
- `README.md` — this file
- `.gitignore` — excludes data and heavy artifacts

> **Excluded locally (reproducible by running the notebook):**  
> `data_compressed/`, `data_csv/`, `outputs/`, any `*.zip` / `*.csv`.

## Environment
```bash
conda create -n flight-delay python=3.10 -y
conda activate flight-delay
pip install -r requirements.txt



# ======= =======
GITHUB_USER="kabitaadhikari"
REPO_NAME="flight-delay-part-a"
# ============================================================

# my project folder
cd "C:/Users/kkabi/Desktop/Assignments/Data Science pipeline_final project" || exit 1

# Rename notebook (remove spaces)
if [ -f "onpremises final submission.ipynb" ]; then
  mv "onpremises final submission.ipynb" "onpremises.ipynb"
fi

# .gitignore – exclude data & large artifacts
cat > .gitignore << 'EOF'
data_compressed/
data_csv/
outputs/
*.zip
*.csv
*.parquet
.ipynb_checkpoints/
*.ipynb~*
.DS_Store
Thumbs.db
.vscode/
.idea/
