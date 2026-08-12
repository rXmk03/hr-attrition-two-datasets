# Data

Raw data files for Individual Task 1. Both datasets are publicly available.

## 1. IBM HR Analytics Employee Attrition & Performance

- Source: https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset
- File: `WA_Fn-UseC_-HR-Employee-Attrition.csv`
- 1,470 rows, 35 attributes
- Target: `Attrition` (Yes/No) — 237 left (16.1%), 1,233 stayed (83.9%)
- Missing values: none
- Duplicate rows: none
- Access: free Kaggle account required
- Downloaded on: 11-08-2026

Attribute groups: demographic (`Age`, `Gender`, `MaritalStatus`), role (`JobRole`,
`JobLevel`, `Department`), compensation (`MonthlyIncome`, `PercentSalaryHike`,
`StockOptionLevel`), tenure (`YearsAtCompany`, `YearsInCurrentRole`,
`TotalWorkingYears`), satisfaction ratings (`JobSatisfaction`, `WorkLifeBalance`,
`EnvironmentSatisfaction`), workload (`OverTime`, `BusinessTravel`).

Columns removed: `EmployeeCount`, `Over18`, `StandardHours` (each has a single distinct
value) and `EmployeeNumber` (a row identifier).

**This is a fictional dataset created by IBM data scientists, not a real workforce.**

## 2. HR Analytics (employee turnover)

- Source: https://www.kaggle.com/datasets/giripujar/hr-analytics
- File: `HR_comma_sep.csv`
- 14,999 rows raw, 10 attributes
- **3,008 duplicate rows (20.1%) removed → 11,991 rows used**
- Target: `left` (0/1) — 23.8% before de-duplication, **16.6% after**
- Missing values: none
- Access: free Kaggle account required
- Downloaded on: 12-08-2026

Attributes: `satisfaction_level` (0–1), `last_evaluation` (0–1), `number_project`,
`average_montly_hours`, `time_spend_company` (years), `Work_accident`,
`promotion_last_5years`, `Department` (10 levels), `salary` (low/medium/high).

No columns were removed — none was constant and none was an identifier.

Note: `average_montly_hours` is spelled as in the source file. The removed duplicates
were disproportionately leavers, which is why the class balance shifted by seven points.

## Comparability

Both datasets record whether an employee left, at two different organisations.
Overlapping constructs:

| Concept | Dataset 1 | Dataset 2 |
| --- | --- | --- |
| Outcome | `Attrition` | `left` |
| Tenure at employer | `YearsAtCompany` | `time_spend_company` |
| Pay | `MonthlyIncome` | `salary` band |
| Satisfaction | `JobSatisfaction` (1–4) | `satisfaction_level` (0–1) |
| Performance | `PerformanceRating` | `last_evaluation` |
| Department | `Department` | `Department` |
| Workload | `OverTime` (binary) | `average_montly_hours` (continuous) |

Workload is measured differently in each — a flag versus a count — so direction is
comparable between the two but shape is not.

## Citations

Pavansubhash. 2017. IBM HR Analytics Employee Attrition & Performance [Dataset]. Kaggle.
https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset

Giri Pujar. HR Analytics [Dataset]. Kaggle.
https://www.kaggle.com/datasets/giripujar/hr-analytics
