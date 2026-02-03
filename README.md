# Customer Churn Prediction (End-to-End ML Project)

---

## 📌 Project Overview
Customer churn is a critical challenge for subscription-based businesses. This project builds an end-to-end machine learning pipeline to predict customer churn using demographic, service, and billing data.

The goal is not only to build accurate models, but to optimize recall for churners, ensuring that at-risk customers are identified early for proactive retention.

---

## 🗂️ Dataset

- Dataset: Telco Customer Churn Dataset(Kaggle)
- Target variable: `Churn Label`
  - `1` → Customer churned
  - `0` → Customer retained

The dataset contains customer demographics, service subscriptions, contract details, and billing information.

---

## 🔍 Exploratory Data Analysis (EDA)

EDA was conducted in multiple stages:
- Dataset structure and data type inspection
- Missing value analysis
- Target distribution analysis (class imbalance)
- Categorical cardinality analysis to identify:
  - Identifier-like columns
  - High-cardinality categorical features
  - Potential sources of target leakage

This step was critical in ensuring modeling decisions were based on valid, predictive features.

---

## 🧹 Data Cleaning

Based on EDA findings, the following columns were removed:
- **Identifiers:** `CustomerID`, `Zip Code`
- **Leakage-prone features:** `Churn Value`, `Churn Score`, `Churn Reason`, `CLTV`
- **High-cardinality location features:** `City`, `State`, `Country`, `Lat Long`, `Latitude`, `Longitude`

Additional steps included:
- Converting `Total Charges` from string to numeric
- Removing a small number of rows with invalid numeric values

---

## 🧠 Feature Engineering
- Binary encoding of the target variable
- One-hot encoding of categorical features
- Stratified train–test split to preserve class distribution
- Feature scaling applied where appropriate

---

## 🤖 Modeling Approach
1️⃣ **Logistic Regression (Baseline)**
- Used as a simple, interpretable baseline
- Achieved reasonable accuracy
- Reached ~60% recall for churners
- Highlighted the limitations of linear models for this problem


2️⃣ **Random Forest Classifier**
- Captured non-linear relationships and feature interactions
- Evaluated using ROC–AUC to assess class separability
- Initially underperformed at the default decision threshold due to class imbalance

---

## 📈 Threshold Tuning & Evaluation

- ROC–AUC: `0.84`, indicating strong separability between churners and non-churners
- Decision threshold adjusted from 0.5 to 0.35 to prioritize recall

Final Results (Threshold-Tuned Random Forest)
| Metric (Churn Class) | Value |
|:----|----:|
| Precision	| 0.55 |
| Recall |	0.71 |
| F1-score	| 0.62 |

This adjustment significantly improved the model’s ability to identify at-risk customers, which is critical in churn prevention scenarios.

---

## 🏆 Key Takeaways

- Perfect accuracy is often a warning sign, not a success
- Early detection of target leakage is essential
- Accuracy alone is misleading for imbalanced datasets
- ROC–AUC and recall are more informative for churn problems
- Threshold tuning can deliver substantial business value
- Model selection should be driven by cost-sensitive objectives

---

## ▶️ How to Run This Project

1. **Clone the Repository**
```bash
git clone https://github.com/JessicaComfortGrant/Customer_Churn_Prediction.git
```

2. **Navigate into the project folder:**
```bash
cd Customer_Churn_Prediction
```

 3. **Set Up a Virtual Environment (Optional but Recommended)**
```bash
python -m venv venv
```

4. **Activate the environment:**

- Windows
```bash
venv\Scripts\activate
```

- macOS / Linux
```bash
source venv/bin/activate
```

5. **Install Dependencies**
```bash
pip install -r requirements.txt
```

6. **Run the Notebook**

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open:
```bash
notebooks/customer_churn_analysis.ipynb
```

7. **Run all cells top to bottom to reproduce the analysis and results.**

---

## 🛠️ Tools & Libraries
- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## 📁 Project Structure
```powershell
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
```
---

## 🚀 Conclusion

This project emphasizes methodology over metrics. By combining careful EDA, leakage prevention, and business-aware evaluation, the final model provides actionable insights rather than misleading performance.

---

## Author

**Jessica Comfort Grant**

Aspiring Data Scientist | Machine Learning Enthusiast

LinkedIn: www.linkedin.com/in/jessica-comfort-grant-91094b21b

Feel free to connect or explore the notebook for a detailed walkthrough of the analysis and modeling process.
