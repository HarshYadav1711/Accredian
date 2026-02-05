# Fraud Detection in Financial Transactions

A comprehensive data science project demonstrating end-to-end fraud detection using machine learning, with a focus on interpretability, business reasoning, and stakeholder-friendly communication.

## 📋 Project Overview

This project analyzes **6.3 million synthetic financial transactions** to identify fraudulent activity patterns and build predictive models. The analysis prioritizes clarity and business impact over unnecessary complexity.

### Key Findings

| Metric | Value |
|--------|-------|
| Dataset Size | 6,362,620 transactions |
| Fraud Rate | 0.13% (8,213 cases) |
| Fraud Types | TRANSFER, CASH_OUT only |
| Best Model | Random Forest (ROC-AUC: 0.9989) |

### Top Fraud Indicators
1. **Account Emptying** — Origin balance reduced to zero
2. **High Transaction Amount** — Larger than typical transactions
3. **Balance Discrepancies** — Calculation errors in balance updates

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/fraud-detection.git
cd fraud-detection

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook fraud_detection_analysis.ipynb
```

---

## 📁 Project Structure

```
fraud-detection/
├── fraud_detection_analysis.ipynb   # Main analysis notebook
├── Fraud.csv                         # Dataset (not included - see Data section)
├── Data Dictionary.txt               # Feature descriptions
├── requirements.txt                  # Python dependencies
├── LICENSE                           # MIT License
└── README.md                         # This file
```

---

## 📊 Dataset

**Source**: [PaySim Synthetic Financial Dataset](https://www.kaggle.com/datasets/ealaxi/paysim1)

The dataset simulates mobile money transactions based on real transaction patterns. Due to file size (~493MB), please download it separately from Kaggle.

### Features

| Feature | Description |
|---------|-------------|
| `step` | Time unit (1 step = 1 hour, 744 total = 30 days) |
| `type` | Transaction type: CASH-IN, CASH-OUT, DEBIT, PAYMENT, TRANSFER |
| `amount` | Transaction amount |
| `nameOrig` | Origin customer ID |
| `oldbalanceOrg` | Origin balance before transaction |
| `newbalanceOrig` | Origin balance after transaction |
| `nameDest` | Destination customer/merchant ID |
| `oldbalanceDest` | Destination balance before transaction |
| `newbalanceDest` | Destination balance after transaction |
| `isFraud` | Target variable (1 = fraud, 0 = legitimate) |
| `isFlaggedFraud` | System flag for transfers > 200,000 |

---

## 🔬 Methodology

### 1. Data Preparation
- Memory-efficient loading with dtype optimization
- Focused analysis on fraud-relevant transactions (TRANSFER, CASH_OUT)
- Feature engineering: balance changes, error detection, account emptying flags

### 2. Class Imbalance Handling
- SMOTE (Synthetic Minority Over-sampling Technique)
- Class-weighted models

### 3. Models
| Model | Purpose |
|-------|---------|
| Logistic Regression | Interpretable baseline with coefficient analysis |
| Random Forest | Non-linear patterns with feature importance |

### 4. Evaluation Metrics
- Precision, Recall, F1-Score
- ROC-AUC
- Confusion Matrix
- Business cost analysis (false positives vs. false negatives)

---

## 📈 Results

### Model Performance

| Model | Precision (Fraud) | Recall (Fraud) | F1-Score (Fraud) | ROC-AUC |
|-------|-------------------|----------------|------------------|-------|
| Logistic Regression | 0.07 | 0.96 | 0.13 | 0.9925 |
| Random Forest | 1.00 | 1.00 | 1.00 | 0.9989 |

> **Note**: All metrics above are generated directly from the notebook code. Logistic Regression achieves high recall but low precision (many false positives), while Random Forest achieves exceptional performance on this dataset.

### Business Recommendations
- **Real-time monitoring** for account-emptying transactions
- **Risk-based authentication** with tiered verification
- **Adaptive rules** using model probability scores
- **Customer education** on fraud prevention

---

## 🛠️ Technologies Used

- **Python 3.x**
- **pandas** — Data manipulation
- **numpy** — Numerical operations
- **matplotlib & seaborn** — Visualization
- **scikit-learn** — Machine learning
- **statsmodels** — Multicollinearity analysis (VIF)
- **imbalanced-learn** — SMOTE for class imbalance

---

## 📝 Notebook Sections (Aligned with Accredian Questions)

| Section | Topic | Accredian Question |
|---------|-------|-------------------|
| 1 | Problem Understanding | — |
| 2 | Data Overview | — |
| 3 | Data Cleaning (missing values, outliers, VIF) | **Question 1** |
| 4 | Feature Selection & Reasoning | **Questions 2, 3** |
| 5 | Model Training | **Question 2** |
| 6 | Model Evaluation | **Question 4** |
| 7 | Key Fraud Indicators | **Questions 5, 6** |
| 8 | Prevention Strategy | **Question 7** |
| 9 | Measuring Effectiveness | **Question 8** |
| 10 | Conclusion | — |

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Acknowledgments

- [PaySim Dataset](https://www.kaggle.com/datasets/ealaxi/paysim1) by E. Lopez-Rojas
- Inspired by real-world fraud detection challenges in financial services
