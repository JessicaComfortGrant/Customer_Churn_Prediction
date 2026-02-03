# Customer Churn Prediction

Customer churn is a critical challenge for subscription-based businesses. This project builds an end-to-end machine learning pipeline to predict customer churn using demographic, service, and billing data.

The goal is not only to build accurate models, but to optimize recall for churners, ensuring that at-risk customers are identified early for proactive retention.

---

## 🎯 Project Objectives

Perform structured Exploratory Data Analysis (EDA)

Detect and prevent target leakage

Engineer clean, model-ready features

Build and compare baseline and advanced models

Optimize decision thresholds based on business cost trade-offs

---

## 🗂️ Dataset

**Source: Telco Customer Churn Dataset**

Target variable: Churn Label

1 → Customer churned

0 → Customer retained

The dataset includes:

Customer demographics

Service subscriptions

Contract details

Billing and payment information

---

## 🔍 Exploratory Data Analysis (EDA)

Key EDA steps included:

Dataset structure and data types inspection

Missing value analysis

Target distribution analysis (class imbalance)

Categorical cardinality analysis to identify:

Identifier columns

High-cardinality categorical features

Potential leakage sources

This step revealed several non-predictive and leakage-prone columns, which were removed before modeling.

🧹 Data Cleaning

The following columns were dropped based on EDA findings:

Identifiers: CustomerID, Zip Code

Leakage features: Churn Value, Churn Score, Churn Reason, CLTV

High-cardinality location features: City, State, Country, Lat Long, Latitude, Longitude

Additional steps:

Converted Total Charges from string to numeric

Removed a small number of rows with invalid numeric values

🧠 Feature Engineering

Binary target encoding for Churn Label

One-hot encoding for categorical features

Train–test split with stratification

Feature scaling applied only where required

🤖 Models Trained
1️⃣ Logistic Regression (Baseline)

Purpose:

Establish a simple, interpretable baseline

Performance highlights:

Accuracy: ~81%

Churn Recall: ~60%

This model performed reasonably but missed a significant portion of churners.

2️⃣ Random Forest Classifier

Enhancements:

Captured non-linear relationships

Used class weighting to address imbalance

Initial performance at default threshold (0.5):

Recall was lower than Logistic Regression

However, further evaluation revealed strong separability.

📈 Model Evaluation & Threshold Tuning

ROC–AUC: 0.84 (strong discriminative ability)

Decision threshold tuned from 0.5 → 0.35

Final Threshold-Tuned Random Forest Results
Metric	Churn Class (1)
Precision	0.55
Recall	0.71
F1-score	0.62

📌 Business interpretation:
The tuned model identifies ~71% of churners, significantly reducing false negatives. Although false positives increase, this trade-off is acceptable in churn prevention scenarios where missing at-risk customers is more costly.

🏆 Final Model Choice

Threshold-tuned Random Forest was selected as the final model because:

It achieves the highest churn recall

It maintains a strong ROC–AUC

It aligns better with real-world business objectives

🛠️ Tech Stack

Python

pandas, NumPy

scikit-learn

matplotlib, seaborn

Jupyter Notebook

📁 Project Structure
Customer_Churn_Prediction/
│
├── Data/
│   └── Telco_customer_churn.xlsx
│
├── notebooks/
│   └── customer_churn_analysis.ipynb
│
├── requirements.txt
├── .gitignore
└── README.md

🚀 Key Takeaways

Perfect metrics are often a red flag

Early detection of data leakage is critical

ROC–AUC and recall are more meaningful than accuracy for churn

Threshold tuning can dramatically improve business value

📬 Contact

Jessica Comfort Grant
Aspiring Data Scientist | Machine Learning Enthusiast

Feel free to connect or explore the notebook for a detailed walkthrough of the analysis and modeling process.
