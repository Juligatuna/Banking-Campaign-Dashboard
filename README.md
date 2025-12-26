# Banking Campaign Dashboard

A Tableau dashboard analyzing a bank's marketing campaign to convert clients into fixed deposit account owners. This project uses a Kaggle dataset and provides actionable insights to optimize campaign strategy.

## Project Description

The dashboard explores customer demographics, call patterns, and campaign effectiveness. It highlights key trends that can help marketing teams increase conversion rates.

**Dataset:** [Kaggle Bank Marketing Dataset](https://www.kaggle.com/datasets/rouseguy/bank-marketing)

## 💡 Insights & Recommendations

- **Conversion Rate:** Overall 47.38%, indicating strong campaign performance.
- **Customer Targeting:** Single and educated clients respond better — target them with tailored offers.
- **Contact Method:** Cellular calls outperform telephone contacts — prioritize mobile outreach.
- **Call Duration:** 3–6 minute calls achieve the highest conversions; avoid very short or very long calls.
- **Contact Attempts:** 2–4 attempts are optimal; repeated calls show diminishing returns.
- **Seasonality:** Peak months show stronger results — align campaigns accordingly.
- **Actionable Advice:** Focus on targeted communication and agent training to sustain high conversion efficiency.

## 📂 Repository Structure

```bash
Banking-Campaign-Dashboard/
│
├─ data/                 ← Original dataset (CSV/Excel) or link to Kaggle
│   └─ bank_campaign.csv
│
├─ workbook/             ← Tableau workbook
│   └─ Banking_Campaign_Dashboard.twbx
│
├─ images/               ← Screenshots of dashboard (for GitHub preview)
│   ├─ conversion_rate.png
│   └─ call_duration_analysis.png
│
├─ export/               ← Optional PDF or exported images of full dashboard
│   └─ Banking_Campaign_Dashboard.pdf
│
├─ model/                ← Optional predictive modeling
│   ├─ campaign_model.ipynb        ← Notebook showing model building (logistic regression, decision tree, etc.)
│   ├─ model.pkl                   ← Serialized trained model (optional)
│   └─ predictions.csv             ← Sample predicted probabilities for customers
│
├─ README.md             ← Project description, insights, and instructions
└─ requirements.txt      ← Python dependencies if using a notebook
```

## ⚡ How to Use

1. Clone the repository:

```bash
git clone https://github.com/Juligatuna/Banking-Campaign-Dashboard.git
```
2. Open the .twbx file in Tableau Desktop to interact with the dashboard.
3. Alternatively, view exported images/PDFs in the images/ or export/ folder for a static overview

## 🧠 Predictive Modeling & Model Evolution
This project followed an iterative modeling approach to identify the most effective algorithm for predicting customer conversion to fixed deposit accounts.
1. **Modeling Roadmap**
I progressed through three primary stages to address data complexity and class imbalance:
`Baseline: Logistic Regression` – Established a foundational linear relationship between customer attributes and conversion.
`Intermediate: BalancedRandomForestClassifier` – Introduced ensemble learning with built-in undersampling to better handle the majority-minority class gap.
`Final Model: XGBoost (Extreme Gradient Boosting)` – My final model. Utilized `stratified sampling`, `feature scaling`, and the `scale_pos_weight` parameter to optimize for high recall in a highly imbalanced environment.
2. **Feature Engineering & Selection**
Key predictors used across all models included:
`Demographics`: Age, marital status, education level.
`Financial Status`: Account balance (processed for outliers).
`Communication Data`: Contact type, number of campaign attempts (dropping duration to prevent data leakage during real-time prediction).
`Temporal Trends`: Month and seasonality of the campaign.
3. **Model Performance (XGBoost)**
The final model was tuned to prioritize Recall, ensuring the bank captures as many potential "Yes" conversions as possible.
Metric	Score
Accuracy	0.73
ROC-AUC	0.72
Precision	0.69
Recall	0.88
F1-Score	0.77
4. **Project Deliverables**
deposit_predictions_2025.csv: Contains original customer data, predicted labels, and the raw probability of conversion for every lead.
xbg_deposit_model.pkl: The serialized XGBoost model ready for production deployment.
