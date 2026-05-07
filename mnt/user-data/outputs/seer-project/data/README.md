# Data

Raw SEER data files are **not included in this repository** in accordance with the SEER Research Data Use Agreement, which prohibits releasing data to others.

## How to Reproduce This Dataset

### 1. Request Data Access
- Go to [seer.cancer.gov/data/access.html](https://seer.cancer.gov/data/access.html)
- Register for **SEER Research Data** (free, approved within a few days)
- Read and accept the Data Use Agreement and Treatment Data Limitations

### 2. Download SEER*Stat
- Download the latest version from [seer.cancer.gov/seerstat](https://seer.cancer.gov/seerstat/)
- Log in with the email used to register

### 3. Export the Dataset
Use the following SEER*Stat query parameters to reproduce the exact dataset used in this project:

**Database:** SEER Research Data, 1975–2023 (November 2025 Submission)  
**Statistic type:** Case Listing

**Variables selected:**
| Variable | Notes |
|---|---|
| Age at Diagnosis | Continuous |
| Sex | |
| Race/Ethnicity | Use "Race and origin (recommended by SEER)" |
| Year of Diagnosis | |
| Primary Site | |
| SEER Combined Summary Stage | Target variable — used to derive late-stage label |
| State/Registry | Geographic region |
| Insurance Recode (2007+) | |
| Radiation Therapy | See treatment data limitations |
| Chemotherapy | See treatment data limitations |
| Survival months | For survival analysis phase |
| Vital Status | For survival analysis phase |

**Filters applied:**
- Year of diagnosis: 2000–2023
- Exclude unknown stage

**Export:** Export as `.csv` and place in `data/raw/`

### 4. Run Preprocessing
```bash
python src/preprocess.py
```
This will generate the cleaned dataset at `data/processed/seer_clean.csv`.

---

## Data Citation
*Update this with the exact citation from SEER*Stat Help > Suggested Citations after export.*

Surveillance, Epidemiology, and End Results (SEER) Program (www.seer.cancer.gov)
SEER*Stat Database: Incidence - SEER Research Data, [version], [registry grouping],
Nov 2025 Sub (2000-2023) — Linked To County Attributes, National Cancer Institute,
DCCPS, Surveillance Research Program, released April 2026.

---

## Data Use Agreement
All users of this data must agree to the [SEER Research Data Use Agreement](https://seer.cancer.gov/data/access.html).
Key restrictions relevant to this project:
- Do not share raw data files
- Do not attempt to re-identify individuals
- Suppress any statistics based on cell counts of 1–4
- Do not use raw data with external AI/ML tools (e.g., cloud-based LLMs)
