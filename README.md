# Titanic-ML-Prediction

A complete end-to-end machine learning pipeline for the **Kaggle Titanic — Machine Learning from Disaster** competition.

This project includes data preprocessing, feature engineering, SMOTE oversampling, model comparison (Logistic Regression, Random Forest, XGBoost), hyperparameter tuning, and generation of a Kaggle submission file.

**Repository tag:** `v1.0` — First working pipeline with Kaggle submission (public score: **0.74641**).

---

## 🗂 Repository structure

ML-Titanic-Disaster-Prediction/  
├── titanic_analysis.ipynb  # Notebook: full pipeline, preprocessing -> model -> submission  
├── README.md  
├── .gitignore  # contains: *.csv, .ipynb_checkpoints, etc.  
└── requirements.txt  # (recommended) pip requirements list  

> **Note:** `train.csv`, `test.csv`, and `submission.csv` are intentionally **not** committed.  
> They are included in `.gitignore` (`*.csv`) so your data remains local and private.

---

## ⚙️ Quick setup (Windows)

### 1. Clone the repository
```bash
git clone https://github.com/USERNAME/ML-Titanic-Disaster-Prediction.git
cd ML-Titanic-Disaster-Prediction

2. Create and activate a virtual environment

PowerShell:

python -m venv .venv
.\.venv\Scripts\Activate.ps1


CMD:

python -m venv .venv
.\.venv\Scripts\activate

3. Install dependencies

Create a requirements.txt file with:

pandas
numpy
scikit-learn
xgboost
imbalanced-learn
kaggle
matplotlib


Then install:

pip install -r requirements.txt

🚀 How to run

Place the downloaded dataset files (train.csv, test.csv) in the project root locally (do not commit them).

Open titanic_analysis.ipynb in VS Code or Jupyter and run cells sequentially.

The notebook performs: cleaning, feature engineering, SMOTE, model training, hyperparameter tuning, final training, test preprocessing, and writes submission.csv.

After running the notebook, submission.csv will be generated in the project folder.

🧩 Kaggle CLI setup (Windows)
1. Install Kaggle CLI
pip install kaggle

2. Get your Kaggle API token

Visit Kaggle Account Settings → API → Create New API Token

This downloads a file called kaggle.json.

3. Move kaggle.json to your Kaggle folder

PowerShell:

New-Item -ItemType Directory -Path "$env:USERPROFILE\.kaggle" -Force
Move-Item -Path "$env:USERPROFILE\Downloads\kaggle.json" -Destination "$env:USERPROFILE\.kaggle\kaggle.json" -Force
Set-ItemProperty -Path "$env:USERPROFILE\.kaggle\kaggle.json" -Name IsReadOnly -Value $true


CMD:

mkdir "%USERPROFILE%\.kaggle"
move "%USERPROFILE%\Downloads\kaggle.json" "%USERPROFILE%\.kaggle\kaggle.json"
attrib +R "%USERPROFILE%\.kaggle\kaggle.json"

4. Verify credentials
kaggle competitions list

5. Join the competition

Go to:
👉 https://www.kaggle.com/competitions/titanic

and click Join Competition.

6. Submit your predictions

From your project folder:

kaggle competitions submit -c titanic -f submission.csv -m "My submission message"


Check previous submissions:

kaggle competitions submissions -c titanic

📊 Notes on reproducibility

The notebook uses SMOTE (imbalanced-learn) to balance classes.
If you prefer not to use SMOTE, skip that cell and retrain.

The final model is an XGBoost classifier (hyperparameters tuned).

Set random_state consistently for deterministic runs.

🧠 Results

Public leaderboard score (initial submission): 0.74641

Top features: Sex, Pclass, Age, Fare, Title, Deck, FamilySize, IsAlone

🔮 Future improvements

Group and reduce rare title categories.

Try LightGBM / CatBoost and stacking/ensembling.

Add feature interactions (Fare per person, ticket prefix).

Use stratified cross-validation and advanced tuning.

📜 License

This repo is provided for educational purposes.
You may reuse or modify it freely under a permissive license (MIT recommended).
