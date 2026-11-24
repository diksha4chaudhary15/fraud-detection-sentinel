# SentinelAI: Fraud Detection in Digital Payments

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-Web%20Framework-lightgrey.svg)](https://flask.palletsprojects.com/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange.svg)](https://scikit-learn.org/)

An end-to-end Machine Learning web application that detects fraudulent transactions in digital payments using an **ensemble learning approach**. The system combines multiple classification models (Logistic Regression, Random Forest, and K-Nearest Neighbors) using a **Stacking Classifier** meta-model to achieve robust, high-accuracy fraud detection.

---

## Key Features

- **Ensemble Machine Learning Architecture**: Leverages multiple diverse classifiers combined with a meta-learner to maximize fraud detection sensitivity while keeping false positives low.
- **Handling Imbalanced Data**: Employs **SMOTE** (Synthetic Minority Over-sampling Technique) to address class imbalance inherent in financial transaction datasets.
- **Interactive Web Interface**: A modern dark-mode dashboard built with Flask, CSS glassmorphism, and responsive UI components.
- **Transaction Simulator**:
  - Direct transaction inspection and querying from balanced transaction logs.
  - Random transaction generator for testing legitimate vs. fraudulent patterns.
  - Real-time prediction display with risk level classification.

---

## Machine Learning Pipeline

1. **Preprocessing & Feature Engineering**:
   - Maps raw transaction features to interpretable indicators (`distance_from_home`, `time_since_last_tx`, `Amount`, `email_domain_risk`, `location_city`, `device_type`, `user_risk_score`, `merchant_category`, `daily_tx_amount`, `contactless_used`).
   - Normalization using `StandardScaler`.
   - Balanced sampling and SMOTE augmentation on minority class transactions.
2. **Base Classifiers**:
   - **Logistic Regression** (Linear baseline)
   - **Random Forest** (Tree-based ensemble)
   - **K-Nearest Neighbors (KNN)** (Instance-based clustering)
3. **Meta-Learner**:
   - **Stacking Classifier** trained on the probability outputs of the base models.

---

## Project Structure

```text
MINOR PROJECT VS/
│── app.py                    # Flask web application & prediction API
│── train_models.py           # Model training & serialization pipeline
│── lr.py                     # Logistic Regression standalone module & evaluation
│── rf.py                     # Random Forest standalone module & evaluation
│── knn.py                    # K-Nearest Neighbors module & evaluation
│── min.py                    # Ensemble & evaluation script
│── rename_features.py        # Feature mapping & dataset preprocessing helper
│── generate_dataset.py       # Synthetic/balanced data generation script
│── requirements.txt          # Python dependencies
│── accurate_ensemble_plot.png# Model performance visualization
│── comparison_plot.png       # Classifier comparison plot
│── templates/
│   └── index.html            # Frontend dashboard interface
└── static/
    ├── style.css             # UI styling & glassmorphic theme
    └── script.js             # Client-side API handling & dynamic updates
```

> **Note**: Large dataset files (`*.csv`) and pre-trained weights (`*.pkl`) are excluded from version control via `.gitignore` to comply with GitHub file size limits.

---

## Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/diksha4chaudhary15/<repo-name>.git
cd <repo-name>
```

### 2. Create and Activate a Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Train the Models (Optional if weights already present)
```bash
python train_models.py
```

### 5. Launch the Application
```bash
python app.py
```
Open your browser and navigate to `http://127.0.0.1:5000` to interact with the SentinelAI dashboard.

---

## Author

- **Diksha Chaudhary** - GitHub: [@diksha4chaudhary15](https://github.com/diksha4chaudhary15)
