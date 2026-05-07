# Predicting Late-Stage Cancer Diagnosis: A Risk Factor Analysis Using SEER Data

> What patient, demographic, and clinical factors are most associated with late-stage cancer diagnosis — and can we predict it?

Late-stage cancer detection is where outcomes diverge most dramatically. This project uses the NCI SEER cancer registry (1975–2023) to identify who gets diagnosed late, where, and why — and builds a predictive model and interactive dashboard to surface those disparities.

**Status:** 🚧 In progress

---

## Project Structure

```
├── data/
│   ├── raw/              # SEER exports — gitignored (see data/README.md)
│   ├── processed/        # Cleaned, feature-engineered data
│   └── README.md         # How to reproduce the dataset
├── notebooks/
│   ├── 01_eda.ipynb          # Exploratory data analysis
│   ├── 02_preprocessing.ipynb
│   ├── 03_modeling.ipynb
│   └── 04_survival_analysis.ipynb
├── src/
│   ├── preprocess.py     # Data cleaning pipeline
│   ├── features.py       # Feature engineering
│   ├── model.py          # Training and evaluation
│   └── utils.py
├── dashboard/
│   └── app.py            # Streamlit dashboard
├── models/               # Saved model artifacts (gitignored)
├── requirements.txt
└── README.md
```

---

## Research Question

Binary classification: **late-stage diagnosis (Stage III/IV) vs. early-stage (Stage I/II)**

Key factors examined:
- Demographics: age, sex, race/ethnicity
- Geography: state/registry region
- Clinical: cancer site, year of diagnosis
- Socioeconomic: insurance status

---

## Methodology

### Phase 1 — EDA & Data Preparation
- Stage distribution by cancer type, demographics, geography
- Visualization of disparities
- Missingness analysis, categorical encoding, feature engineering

### Phase 2 — Classification Modeling
- Baseline: logistic regression (interpretability)
- Benchmark: Random Forest, XGBoost
- Evaluation: AUC-ROC, precision/recall
- Class imbalance handling: SMOTE + class weighting
- Feature importance analysis

### Phase 3 — Survival Analysis
- Kaplan-Meier survival curves by stage, cancer type, demographic group
- Implemented with the `lifelines` library

### Phase 4 — Streamlit Dashboard
- Interactive EDA visualizations
- Model input → predicted risk output
- Disparity maps by geography and demographics

---

## Setup

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
pip install -r requirements.txt
```

To reproduce the dataset, see [`data/README.md`](data/README.md).

To run the dashboard:
```bash
streamlit run dashboard/app.py
```

---

## Data Source

NCI Surveillance, Epidemiology, and End Results (SEER) Program.
See [`data/README.md`](data/README.md) for full citation and access instructions.

Raw data is not included in this repository per the SEER Research Data Use Agreement.

---

## Acknowledgments

This project uses publicly available cancer registry data from the National Cancer Institute SEER Program. See the [SEER website](https://seer.cancer.gov) for more information.
