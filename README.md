## 📡 Telco Customer Churn Prediction
📖 Project Overview
Customer churn (attrition) is a critical metric in the telecommunications industry. Acquiring a new customer is significantly more expensive than retaining an existing one.

This project aims to build an End-to-End Machine Learning pipeline to predict customer churn probability based on demographic, service, and account information. The solution assists business teams in identifying high-risk customers and proactively offering retention incentives.

## 🚀 Key Features
End-to-End Pipeline: From raw data processing to model deployment.

Imbalanced Data Handling: Implemented SMOTE (Synthetic Minority Over-sampling Technique) to address the significant class imbalance, improving the model's ability to detect churners.

Robust Preprocessing: Automated pipeline for One-Hot Encoding, Feature Scaling (MinMax), and Missing Value imputation.

Model Optimization: Hyperparameter tuning using GridSearchCV to maximize Recall.

Confidence Scoring: The prediction system outputs not just the class (Churn/No Churn) but also a Probability Score, enabling tiered intervention strategies.

Stress Testing: Validated model performance against conflicting edge cases (e.g., Loyal customers vs. High-risk contract types).

## 📊 Dataset
Source: Telco Customer Churn - Kaggle

Size: 7043 rows, 21 features.

Target Variable: Churn (Yes/No).

## 🛠️ Technologies Used
Language: Python

Data Manipulation: Pandas, NumPy

Visualization: Matplotlib, Seaborn

Machine Learning: Scikit-learn, Imbalanced-learn

Model Persistence: Joblib

## ⚙️ Methodology
1. Exploratory Data Analysis (EDA)
Investigated correlations and distributions. Key insights revealed:

Contract Type: Customers with "Month-to-month" contracts have the highest churn rate.

Service Issue: "Fiber optic" users churn significantly more than DSL users, suggesting potential service quality or pricing issues.

Payment: Electronic check payers are more likely to leave.

2. Feature Engineering & Preprocessing
Converted TotalCharges to numeric and handled missing values.

Applied One-Hot Encoding for categorical variables.

Scaled numerical features (tenure, MonthlyCharges, TotalCharges) to [0, 1] range.

SMOTE Application: Applied only on the Training Set to prevent data leakage.

3. Model Development
Compared Logistic Regression (Baseline) vs. Random Forest Classifier.

Selected Model: Random Forest (Optimized).

Metric Focus: Prioritized Recall (Sensitivity) for the positive class (Churn), as missing a potential churner is more costly than a false alarm.

## 📈 Results & Performance
Recall (Churn Class): ~80% (Achieved after SMOTE & Tuning).

Top Predictors:

Contract_Month-to-month

TotalCharges

TechSupport_No

(You can insert a screenshot of your Feature Importance plot here)

Edge Case Analysis
The model demonstrates nuanced understanding of customer behavior:

Loyal Case: High tenure + 2-year contract → < 5% Churn Risk.

Conflicted Case: High tenure (Loyal) but Month-to-month contract (Risky) → ~61% Churn Risk.

Insight: Even long-term customers are at risk if they are on unstable contract terms.

## 📂 Project Structure
├── data/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
├── notebooks/
│   ├── Churn_Analysis_Modeling.ipynb   # Training & Evaluation
│   └── Prediction_Demo.ipynb           # Testing with new data
├── models/
│   ├── churn_prediction_model.pkl      # Saved Model
│   ├── scaler.pkl                      # Saved Scaler
│   └── model_columns.pkl               # Feature columns mapping
├── README.md
└── requirements.txt
## 💻 How to Run
Clone the repository:

```Bash

git clone https://github.com/yourusername/customer-churn-prediction.git
```
Install dependencies:

```Bash

pip install -r requirements.txt
```
Run the analysis notebook or use the prediction script.
