# Detecting Data Leakage in Cloud Storage with Interpretable Machine Learning

A leakage-safe re-evaluation and improvement of the decision-tree model from
Harahap & Hasibuan (2025) for detecting data leakage in cloud storage.

## What this project does

- Re-checks the reference paper on the same Kaggle dataset with a strict evaluation:
  the data are split once, all preprocessing is fitted on training folds only,
  and the test set is used a single time.
- Measures the performance ceiling the attributes allow.
- Tunes an interpretable decision tree and compares it with Random Forest and XGBoost,
  and class weighting with SMOTEN and random resampling.
- Chooses an alarm threshold for the security trade-off between missed leaks and false alarms.
- Explains the model with IF-THEN rules and permutation importance.

## Repository structure

| Path | Contents |
|---|---|
| `leakage_detection.ipynb` | The full notebook, with outputs |
| `data/` | Where the Kaggle CSV goes (not included, see `data/README.md`) |
| `results/` | Result tables (CSV) and figures (PNG) |
| `models/final_tree.joblib` | Trained pipeline with its alarm threshold |
| `docs/` | Code walkthrough and simple guides (English and Arabic) |
| `requirements.txt` | Python packages |

## How to run

**Google Colab (easiest):** open `leakage_detection.ipynb` in Colab, run the first cell,
upload `Data_Leakage_Detection.csv` when asked, then use *Runtime > Run all*.

**Locally:**

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
# put the CSV in data/raw/ (see data/README.md)
jupyter notebook leakage_detection.ipynb
```

A full run takes about 15 to 20 minutes.

## Tools

Python, pandas, scikit-learn, imbalanced-learn, XGBoost, matplotlib, Google Colab.

## Reference

Harahap, P., & Hasibuan, M. S. (2025). Detecting Data Leakage in Cloud Storage Using Decision Tree
Classification. *Journal of Information Systems and Informatics*, 7(3).
https://doi.org/10.51519/journalisi.v7i3.1215
