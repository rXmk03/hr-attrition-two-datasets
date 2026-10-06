# HR attrition 



## Project

Analysis supporting Individual Task 1, Part 1. The chosen data science role is
Senior Data Scientist, People Analytics (Commonwealth Bank of Australia, REQ259561).

Two publicly available workforce datasets are analysed with two machine learning
algorithms to identify which factors predict an employee leaving, and to evaluate how
reliably those factors can be recovered from each source.

## Datasets

| Dataset | Source | Rows (used) | Target | Minority class |
| --- | --- | --- | --- | --- |
| IBM HR Analytics Employee Attrition | [Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) | 1,470 | `Attrition` (Yes/No) | 16.1% |
| HR Analytics (employee turnover) | [Kaggle](https://www.kaggle.com/datasets/giripujar/hr-analytics) | 11,991 | `left` (0/1) | 16.6% |

Both measure the same outcome — whether an employee left — at two different
organisations, so findings from one can be tested against the other. See
`data/README.md` for attributes, licences and download dates.

## Models

**Random Forest** and a **Multi-layer Perceptron (MLP) neural network**.

The MLP is the model that differs from previous coursework, as required by the brief.
Random Forest is retained because its feature importances are directly interpretable,
which supports the responsible-AI and explainability requirements in the job
advertisement.

## Method

The same protocol is applied to both datasets so results are comparable:

1. Inspect — shape, missing values, placeholder strings, value ranges, distinct counts,
   duplicates
2. Drop constant and identifier columns, then de-duplicate
3. One-hot encode categoricals with `drop_first=True`
4. Stratified 80/20 split, `random_state=42`
5. Fit Random Forest and MLP (scaler fitted on training data only, inside a Pipeline)
6. Compare `class_weight='balanced'`, then sweep the decision threshold
7. Permutation importance on both models, so rankings are measured the same way
8. Effect-size checks on the top features, plus a correlation check

## Repository structure

```
notebooks/01_analysis.ipynb   full analysis, both datasets
data/                         raw data files and their documentation
figures/                      exported charts used in the report appendix
requirements.txt              dependencies
```

Submission artefacts — the report appendix, the job advertisement, the exported
notebook, and the record of generative AI use — are kept outside this repository and
submitted through Canvas.

## How to run

```bash
pip install -r requirements.txt
jupyter notebook
```

Open `notebooks/01_analysis.ipynb`. **Set the `REPO` constant in the setup cell to your
local clone path before running** — the notebook asserts the data folder exists and will
stop immediately if it does not. Then run all cells in order.

## Notes on reproducibility

- `random_state=42` is fixed throughout, so results are repeatable.
- The MLP is non-deterministic without a fixed seed; the seed is set inside the Pipeline.
- Permutation importance uses `n_repeats=10` on the smaller dataset and `n_repeats=5` on
  the larger one for runtime.
- Both datasets are believed to be synthetic. IBM state theirs is fictional, and the
  second dataset's near-perfect separability is not characteristic of real workforce
  data. This limits how far any finding generalises.

Process notes, including problems encountered and how they were resolved, are in
section 4 of the notebook.
