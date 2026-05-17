# Decision Log

A running list of the main design decisions taken during this project, with a short reason for each one. Newest entries on top.

The point of this document is to make trade-offs visible: many decisions in a data project are not obvious from the final code, and writing them down forces a clear rationale.

---

## 2026-05-17 — Development environment

Chose VS Code with the Microsoft Python and Jupyter extensions over Jupyter Lab in the browser.

Reason: the same editor is used for notebooks, SQL files and Python scripts in this project, so keeping everything in one place reduces context switching.

## 2026-05-17 — No plotting libraries in Python

Removed `matplotlib` and `seaborn` from `requirements.txt`. EDA in Python uses numbers and tables only.

Reason: all visualisation in this project is done in Power BI. Plotting in Python would duplicate effort and create two sources of truth for the same charts.

## 2026-05-17 — Scope limited to hard churn (v1)

The business case originally promised analysis of both hard churn (`Exited` flag) and soft churn (silent attrition). The source dataset is a point-in-time snapshot with no transactional history, so soft churn cannot be measured from this data alone.

Reason: v1 of the project is limited to hard churn.

## 2026-05-17 — Stack confirmation

Final stack: Python + Pandas (EDA / cleaning / feature engineering), PostgreSQL (data modeling), Power BI (dashboard). Removed earlier mention of "synthetic data generation in NumPy" from the business case, since transactions are out of scope for v1.

---

## How to use this file

Add a new entry every time a decision is taken that another person reading the repo would otherwise have to reverse-engineer from the code. Format:

```
## YYYY-MM-DD — Short title

What was decided.

Reason: one or two sentences.
```