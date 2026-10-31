# Detecting Data Leakage in Cloud Storage with Interpretable Machine Learning

**Semester Project · Syrian Private University · Faculty of Artificial Intelligence Engineering · Academic Year 2026–2027**

**Prepared by:** Ghaith Jbili, Bayan Awad, Mohammed Ghazal
**Supervised by:** Dr. Wassim Janeidi, Eng. Jaafar Mahfouz

---

## 📄 Project Report

### [**➡️ Read the full report (PDF)**](report/Detecting_Data_Leakage_Report.pdf)

The report is the main deliverable of this project. It contains:

| Chapter | Contents |
|---|---|
| **Chapter 1: Project Overview and Theoretical Foundations** | Scientific problem and objectives, the reference article and its open questions, related works, cloud storage and data leakage, threat model and MITRE ATT&CK mapping, data loss prevention, decision trees, imbalanced learning, evaluation metrics, methodological data leakage, and the path from model to cloud service |
| **Chapter 2: Implementation Mechanism and Experimental Results** | Block diagram, flowcharts and pseudo-code, performance ceiling, model comparison, final test evaluation, threshold trade-off, feature importance and interpretable rules |

### Key results (held-out test set, 9,900 events)

| Model | Leakage recall | Precision | F1 | PR-AUC | MCC |
|---|---|---|---|---|---|
| Always "normal" (baseline) | 0.000 | – | 0.000 | 0.311 | 0.000 |
| Reference tree (Harahap & Hasibuan, 2025) | 0.101 | 0.550 | 0.171 | 0.452 | 0.127 |
| **Our final tree (θ\* = 0.416)** | **0.827** | 0.507 | **0.628** | **0.609** | **0.429** |

Our interpretable decision tree detects about **8 times more leakage events** than the reference model, evaluated with a leakage-safe procedure in which the test set is used only once. Even against the article’s tree read with integer codes (as its published splits imply), which reaches recall 0.298 on the same test set, the final tree catches about **2.8 times** as many leakage events.

---

## 📊 Seminar Presentation

- [**View the slides (PDF)**](presentation/Detecting_Data_Leakage_Seminar.pdf): opens directly in the browser
- [Download the PowerPoint file (.pptx)](presentation/Detecting_Data_Leakage_Seminar.pptx)

---

## 🧪 Practical Summary (Arabic)

- [**ملخّص القسم العملي — Practical Summary (PDF, Arabic)**](practical/Practical_Summary_AR.pdf): a short summary of the practical work: the idea, the data, the training process and the results.

---

## 💻 Code and Results

| Path | Contents |
|---|---|
| [`leakage_detection.ipynb`](leakage_detection.ipynb) | The full notebook, with outputs |
| [`results/`](results/) | Result tables (CSV) and figures (PNG) |
| [`models/final_tree.joblib`](models/) | Trained pipeline with its alarm threshold |
| [`docs/`](docs/) | Code walkthrough and simple guides (English and Arabic) |
| [`data/`](data/) | Where the Kaggle CSV goes (not included, see [`data/README.md`](data/README.md)) |
| [`requirements.txt`](requirements.txt) | Python packages |

### How to run

**Google Colab (easiest):** open `leakage_detection.ipynb` in Colab, run the first cell, upload `Data_Leakage_Detection.csv` when asked, then use *Runtime > Run all*.

**Locally:**

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
# put the CSV in data/raw/ (see data/README.md)
jupyter notebook leakage_detection.ipynb
```

A full run takes about 15 to 20 minutes.

**Tools:** Python, pandas, scikit-learn, imbalanced-learn, XGBoost, matplotlib, Google Colab.

---

## Reference article

P. Harahap and M. S. Hasibuan, "Detecting data leakage in cloud storage using decision tree classification," *Journal of Information Systems and Informatics*, vol. 7, no. 3, pp. 2516–2534, Sep. 2025, doi: [10.51519/journalisi.v7i3.1215](https://doi.org/10.51519/journalisi.v7i3.1215).
