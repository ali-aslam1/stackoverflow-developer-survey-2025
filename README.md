# Stack Overflow Developer Survey 2025 — AI Productivity Prediction

Predicting whether professional developers agree that AI tools and agents have increased their productivity, using the official 2025 Stack Overflow Developer Survey.

---

## 📌 Project Overview

With the rapid emergence of AI developer agents and assistants, this project investigates developer perceptions and productivity impacts. Using machine learning models, we formulate a classification pipeline to predict developer productivity sentiment (`Agree`/`Disagree` that AI tools increase productivity) based on their workflow, tooling, experience, compensation, and organization profile.

---

## 📊 Dataset & Access

Due to GitHub's file size limit (100 MB), the raw survey data (~140.9 MB) is not tracked in this repository.

* **Raw Survey Dataset (`survey_results_public.csv`)**: Available on Kaggle:  
  👉 **[Kaggle: Stack Overflow Developer Survey 2025 Dataset](https://www.kaggle.com/datasets/aliaslam25/stack-overflow-developer-survey-2025/)**
* **Official Survey Source**: [Stack Overflow Annual Developer Survey 2025](https://survey.stackoverflow.co/2025)
* **Survey Schema**: Provided in [`data/survey_results_schema.csv`](data/survey_results_schema.csv)
* **Survey Questions Reference**: Provided in [`docs/2025_Developer_Survey_Tool.pdf`](docs/2025_Developer_Survey_Tool.pdf)

> **To run the full pipeline from raw data:**  
> Download `survey_results_public.csv` from the Kaggle dataset link above and place it in the project root directory.

---

## 📁 Repository Structure

```text
stackoverflow-developer-survey-2025/
├── .gitignore                                      # Excludes .venv, raw CSV (>100MB), caches
├── README.md                                       # Comprehensive project documentation
├── requirements.txt                                # Python dependencies
│
├── data/
│   └── survey_results_schema.csv                   # Survey schema and column descriptions
│
├── docs/
│   └── 2025_Developer_Survey_Tool.pdf              # Full questionnaire & survey tool
│
├── phase2/                                         # Phase 2: Visualization & Preprocessing
│   ├── phase2_visualization_preprocessing.ipynb    # EDA, statistical analysis & cohort filtering
│   ├── phase2_preprocessed.csv                     # Filtered cohort intermediate dataset (~1.8 MB)
│   └── ML_Project_2.pdf                            # Phase 2 guidelines & rubric
│
├── phase3/                                         # Phase 3: Feature Engineering
│   ├── phase3_feature_engineering.ipynb            # Missingness handling, encoding & feature sets
│   ├── phase3_final.csv                            # Final preprocessed feature matrix (~4.4 MB)
│   └── ML_Project_3.pdf                            # Phase 3 guidelines & rubric
│
├── phase4/                                         # Phase 4: Model Exploration & Benchmarking
│   ├── phase4_methodology_results.ipynb            # Model comparison (LR, RF, XGBoost, SVM, KNN)
│   ├── results_model_comparison.csv                # Benchmark evaluation metrics
│   └── ML_Project_4.pdf                            # Phase 4 guidelines & rubric
│
├── phase5/                                         # Phase 5: Methodology Comparison & Advanced Modeling
│   ├── ai-productivity-prediction-phase-5-methodology.ipynb # Advanced modeling notebook
│   ├── phase5_research_paper.docx                  # Phase 5 research paper draft
│   ├── phase5_methodology_comparison.docx          # Detailed methodology analysis
│   └── ML_Project_5.pdf                            # Phase 5 guidelines & rubric
│
└── phase6/                                         # Phase 6: Final Research Paper
    └── phase6_research_paper.docx                  # Final published research paper document
```

---

## 🔬 Project Phases Summary

* **Phase 2 — Visualization & Preprocessing**:
  Filtered raw responses (49,123 respondents) to an active cohort of professional developers utilizing AI developer tools. Addressed missingness, target construction, and preliminary visualizations.
* **Phase 3 — Feature Engineering**:
  Engineered interaction terms, multi-select feature aggregations, compensation adjustments, and categorical encoding, producing a final model-ready dataset of 45 features across 9,502 developers.
* **Phase 4 — Methodology & Model Evaluation**:
  Benchmarked baseline and non-linear classifiers using 5-fold cross-validation evaluated on ROC-AUC, Macro-F1, Precision, and Recall.
* **Phase 5 — Advanced Methodology & Deep Dive**:
  Explored ensemble techniques, hyperparameter optimization, and in-depth performance analysis documented in the Phase 5 research paper.
* **Phase 6 — Final Research Paper**:
  Comprehensive research paper synthesis covering literature review, methodology, comparative analysis, error analysis, and implications for AI adoption in software development.

---

## 📈 Model Benchmark Results (Phase 4)

| Model | ROC-AUC | F1-macro | Accuracy | Precision-macro | Recall-macro |
|---|---|---|---|---|---|
| **Logistic Regression** | **0.8465** | 0.7414 | 0.7627 | 0.7347 | **0.7604** |
| **Random Forest** | 0.8457 | 0.7465 | 0.7997 | 0.7836 | 0.7303 |
| **SVM (RBF) [30% sample]** | 0.8402 | **0.7494** | **0.8034** | **0.7910** | 0.7321 |
| **XGBoost** | 0.8387 | 0.7443 | 0.7754 | 0.7411 | 0.7489 |
| **KNN ($k=11$)** | 0.8113 | 0.7199 | 0.7782 | 0.7521 | 0.7062 |
| **KNN ($k=5$)** | 0.7779 | 0.7034 | 0.7595 | 0.7227 | 0.6937 |

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/ali-aslam1/stackoverflow-developer-survey-2025.git
cd stackoverflow-developer-survey-2025
```

### 2. Set up the environment
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/macOS:
source .venv/bin/activate

pip install -r requirements.txt
```

### 3. Obtain Data
To rerun preprocessing from the raw dataset, download `survey_results_public.csv` from [Kaggle](https://www.kaggle.com/datasets/aliaslam25/stack-overflow-developer-survey-2025/) and place it in the project root. The preprocessed files (`phase2/phase2_preprocessed.csv` and `phase3/phase3_final.csv`) are already included in the repository so you can jump straight into modeling!
