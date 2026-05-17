# bank-churn-analysis

End-to-end churn analysis for a simulated retail bank (10K customers). SQL data modeling in PostgreSQL, EDA and cleaning in Python/Pandas, and a Power BI dashboard with risk segmentation and retention recommendations.

This is a portfolio project. Scope, decisions and limitations are documented in `docs/`.

## Stack

- Python 3.12 + Pandas (EDA, cleaning, feature engineering)
- PostgreSQL (data modeling and queries)
- Power BI (dashboard)
- Git / GitHub

## Repo structure

```
data/
  raw/            # source CSV from Kaggle (do not edit)
  processed/      # cleaned outputs of the notebooks
docs/
  business_case.md
  data_dictionary.md
  findings_and_recommendations.md
  decision_log.md
notebooks/
  01_eda.ipynb
  02_cleaning.ipynb
  03_feature_engineering.ipynb
scripts/
  etl_pipeline.py
sql/
  01_schema.sql
  02_data_quality_checks.sql
  03_business_questions.sql
  04_kpi_views.sql
powerbi/
  churn_dashboard.pbix
```

## Setup

1. Clone the repo and `cd` into it.
2. Create a virtual environment and activate it:
```bash
   python3 -m venv venv
   source venv/bin/activate
```
3. Install dependencies:
```bash
   pip install -r requirements.txt
```
4. Open the project in VS Code:
```bash
   code .
```
5. Install the following VS Code extensions (both from Microsoft):
   - Python
   - Jupyter
6. Open any notebook in `notebooks/`. When prompted to select a kernel, choose the one from this project's venv (it should show as `Python 3.12.x ('venv': venv)`).

## How to read this project

- Start with `docs/business_case.md` to understand the problem.
- `docs/data_dictionary.md` describes the source data.
- `notebooks/` contain the analysis in order (EDA → cleaning → feature engineering).
- `sql/` contains the data model and the queries that feed the Power BI dashboard.
- `docs/findings_and_recommendations.md` is the executive summary of what came out of the analysis.
- `docs/decision_log.md` documents the main design decisions taken along the way and why.

## Author

Lautaro Reche
[LinkedIn](https://www.linkedin.com/in/lautaroreche/)
[lautaroreche.com](https://www.lautaroreche.com)