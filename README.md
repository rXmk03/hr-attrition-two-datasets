# COSC2816 – Individual Task 1

Case Studies in Data Science, RMIT, Semester 2 2026.
Student: s4239310

## Project

Analysis supporting Individual Task 1, Part 1. The chosen data science role is
Senior Data Scientist, People Analytics (Commonwealth Bank of Australia, REQ259561).
Two publicly available workforce datasets are analysed with two machine learning
algorithms to generate insights relevant to that role.

## Datasets

| Dataset | Source | Rows | Target |
| --- | --- | --- | --- |
| IBM HR Analytics Employee Attrition & Performance | Kaggle | 1,470 | `Attrition` (binary) |
| Adult / Census Income | UCI ML Repository | 48,842 | income >$50K (binary) |

TODO: confirm row counts and class balance after loading.

## Models

TODO: describe the two algorithms used and why one differs from previous coursework.

## Repository structure

```
notebooks/    analysis notebooks
data/         raw data files
figures/      exported charts used in the report appendix
ai-log.txt    running record of generative AI use (Condition 3)
```

## How to run

```bash
pip install -r requirements.txt
jupyter notebook
```

Run the notebooks in `notebooks/` in order.

## Notes

TODO: write up at the end - key findings, anything that went wrong, reproducibility notes.
