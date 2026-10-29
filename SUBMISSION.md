# Project Submission — Credit Card Fraud Detection

## Required submission links

**GitHub repository (public):** https://github.com/ayoawo123/credit-card-fraud-detection-ml

**Published Medium article (user-provided URL):** https://medium.com/@ayobamiawogboro123/99-83-accurate-zero-fraud-caught-heres-the-catch-4723a7b49b1c

**Blog headline:** 99.83% Accurate. Zero Fraud Caught. Here's the Catch.

**Notebook:** [fraud_detection_analysis.ipynb](notebooks/fraud_detection_analysis.ipynb)

## Project description

This project follows CRISP-DM to study the rare-event classification problem of
credit card fraud using the public ULB/Worldline dataset. It answers four business
questions on fraud incidence, transaction amounts, predictive performance, and
the interpretation of a held-out prediction. It compares class-weighted Logistic
Regression and Random Forest using recall, precision, F1, ROC AUC, average
precision, and confusion matrices.

## Rubric alignment

| Criterion | Submission evidence |
|---|---|
| PEP 8 readability and logical structure | Notebook uses descriptive `snake_case` variable/function names, separated imports, organized Markdown and code cells, and explicitly numbered CRISP-DM sections. |
| Executable Jupyter Notebook | All analysis code is in `notebooks/fraud_detection_analysis.ipynb`; run all cells with the source CSV installed as documented below. |
| Formal documentation, docstrings, DRY | Reusable `load_transactions`, `clean_transactions`, `save_figure`, `build_models`, and `evaluate_classifier` functions each have a docstring. |
| CRISP-DM | All six phases described and implemented in notebook and README. |
| Missing and categorical values | Zero source missing values; exact duplicates dropped; all predictors numeric, binary target encoded as 0/1; no categorical encoding required; class weights and stratified split documented. |
| 3–5 answered business questions | Four explicitly asked and answered with charts, tables, and statistics in the notebook. |
| Public GitHub repository | The link above is the submission repository. |
| README | Documents motivation, libraries, files, results, reproducibility, limitations, acknowledgments. |
| Nontechnical public blog | Medium article link above; accessible language, attention-grabbing headline, dataset statistics and study findings. |
| Article structure and evidence | Short paragraphs; supporting visuals and statistics. Confirm the live Medium version has the model comparison chart, figure captions and correct attribution. |

## Key reported findings

- 284,807 source transactions, including 492 fraud cases (0.173%).
- 1,081 exact duplicate records removed before training.
- Original transaction-amount medians: 9.25 (fraud), 22.00 (legitimate);
  source currency unspecified.
- On 56,746 held-out transactions (95 fraud), Logistic Regression detected
  83 frauds and generated 1,389 false alerts.
- Random Forest detected 69 frauds with 2 false alerts.
- The majority-class baseline would obtain ~99.83% accuracy but 0% fraud recall.

## Reproducibility and limitation

The large source CSV is not committed. Download `creditcard.csv` from:
https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
and place it at `data/creditcard.csv`. Then:

```bash
python -m pip install -r requirements.txt
cd notebooks
jupyter lab
```

Open the notebook and choose Run All. The source data is anonymized and
historical, and the models are proof-of-concept classifiers. The random
train/test split does not establish robustness to temporal drift.
No published metric is evidence of real-world deployment readiness.

## Academic integrity

Original analysis code and explanatory writing are included. The public
ULB/Worldline dataset is attributed; any externally sourced data or further
code adaptations must be cited. Do not claim a production-ready detector.

## Publication verification

The Medium URL was provided by the author. Its independent anonymous-browser
accessibility could not be verified automatically. Before submitting, confirm
the full article and embedded images load in a signed-out browser window.
