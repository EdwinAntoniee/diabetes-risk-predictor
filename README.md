# Diabetes Risk Predictor — End-to-end machine learning web app for diabetes risk prediction

![Frontend](https://img.shields.io/badge/Frontend-Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![AI/ML](https://img.shields.io/badge/AI%2FML-Scikit--Learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Type](https://img.shields.io/badge/Type-Group%20Project-2563EB?style=flat)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat)
![Academic](https://img.shields.io/badge/Academic-Course%20Assignment-blueviolet?style=flat)
![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat&logo=pandas&logoColor=white)

---
🌐 **Live Demo** — [View Live](https://diabetesprediction-program-assignment-ml.streamlit.app/)
---

## Project Overview
Diabetes Risk Predictor is an interactive clinical machine learning web application that predicts diabetes likelihood from metabolic measurements using the Pima Indians Diabetes Dataset. It streamlines the diagnostic workflow into a guided sequential pipeline covering exploratory data analysis, dynamic data preprocessing, model benchmarking, and real-time patient assessment. The tool is designed for healthcare analysts and practitioners seeking an accessible, transparent diagnostic screening aid.

## Key Features
- Explore diagnostic distributions using automated univariate, bivariate, and multivariate correlation heatmaps
- Preprocess medical indicators dynamically with customizable missing value imputation and scaling strategies
- Train and benchmark four classification models: Random Forest, SVM, Logistic Regression, and KNN
- Tune algorithm hyperparameters directly from the interactive control interface
- Evaluate predictive performance with confusion matrices, accuracy, precision, recall, and F1 metrics
- Generate real-time patient risk predictions with confidence probability scoring and clinical alerts

## My Roles & Contributions
- **Frontend & UI/UX**
  - Architected and built the full interactive web application using Streamlit with a sequential multi-stage workflow.
  - Implemented dynamic user inputs, reactive data tables, and diagnostic plotting components for real-time visualization.
  - Developed the end-to-end patient inference interface with risk classification banners and probability readouts.
- **Deployment**
  - Structured application configuration, environment dependencies (`requirements.txt`), and reproducible local launch routines.
  - Designed the session-state architecture to maintain data persistence across multi-step pipeline navigation.
- **Quality Assurance & Pipeline Review**
  - Audited teammates' data pipelines to identify and resolve critical data preparation and logical defects.
  - Corrected invalid feature imputation logic, ensuring discrete variables such as `Pregnancies` were not mistakenly imputed.
  - Enforced strict train/test split isolation across models to prevent data leakage between evaluation and training sets.

## Architecture
The application implements an end-to-end machine learning and inference pipeline:

```mermaid
flowchart LR
    A[Pima Indians Dataset] --> B[Exploratory Data Analysis]
    B --> C[Preprocessing & Imputation]
    C --> D[Model Training & Tuning]
    D --> E[Model Benchmarking & Evaluation]
    E --> F[Inference Engine]
    F --> G[Risk Prediction & Probability]
```

1. **Ingestion & Validation**: Loads baseline diagnostic records and handles invalid zero-values in biological metrics (`Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, `BMI`).
2. **Preprocessing**: Splits data with stratified sampling, applies median imputation on physiological predictors, and fits feature scalers (`StandardScaler`, `MinMaxScaler`, `RobustScaler`).
3. **Model Training**: Fits Random Forest, Support Vector Machine, Logistic Regression, or K-Nearest Neighbors on transformed training sets.
4. **Validation & Inference**: Computes classification performance matrices on test data and executes inference on user-submitted patient profiles through fitted transformers.

## Folder Structure
```
Machine-Learning-FinalProject/
├── data/
│   ├── cleaned_data.csv          # Preprocessed baseline dataset
│   ├── X_train_original.csv      # Unscaled feature training set
│   ├── X_test_original.csv       # Unscaled feature testing set
│   ├── X_train_scaled.csv        # Scaled feature training set
│   ├── X_test_scaled.csv         # Scaled feature testing set
│   ├── y_train.csv               # Training target labels (Outcome)
│   └── y_test.csv                # Testing target labels (Outcome)
├── Model/
│   ├── diabetes_scaler.pkl       # Fitted feature scaler object
│   ├── knn_model.pkl             # Trained K-Nearest Neighbors model
│   ├── logistic_regression_model.pkl # Trained Logistic Regression model
│   ├── random_forest_model.pkl   # Trained Random Forest model
│   └── svm_model.pkl             # Trained Support Vector Machine model
├── plot/
│   ├── eval_confusion_matrix.png # Confusion matrix visualizations
│   ├── eval_cross_validation.png # Cross-validation score distribution
│   ├── eval_feature_importance.png # Feature importance ranking chart
│   ├── eval_metrics_comparison.png # Comparative model evaluation plot
│   └── eval_roc_curve.png        # ROC curves across all classifiers
├── .gitignore                    # Excludes media, documents, and caches
├── diabetes.csv                  # Raw Pima Indians Diabetes dataset
├── EDA.ipynb                     # Exploratory data analysis notebook
├── evaluation.ipynb              # Model evaluation and comparison notebook
├── main.py                       # Streamlit web application entry point
├── model.ipynb                   # Model experimentation notebook
├── README.md                     # Project documentation
└── requirements.txt              # Application Python dependencies
```

## Installation

### Prerequisites
- Python 3.10 or higher
- Git

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/EdwinAntoniee/diabetes-risk-predictor.git
   cd diabetes-risk-predictor
   ```

2. Create and activate a virtual environment:
   - **Windows (PowerShell):**
     ```powershell
     python -m venv venv
     .\venv\Scripts\Activate.ps1
     ```
   - **macOS / Linux:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```

3. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Launch the application:
   ```bash
   streamlit run main.py
   ```
