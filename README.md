# Customer-Churn-Analysis-and-Prediction
A machine learning project that analyzes telecom customer data to understand churn drivers and predicts which customers are likely to leave.

Overview

This project uses the Telco Customer Churn dataset (7,043 customers, 21 features) to:


Explore patterns behind customer churn (tenure, charges, contract type, etc.)
Select the most predictive features using statistical tests and recursive feature elimination
Train and compare four classification models
Identify the top drivers of churn


Churn rate in the dataset: 26.54% (1,869 churned / 5,174 retained)

Dataset

The notebook expects a CSV file named Telco_Customer_Churn_Dataset (1) (1).csv in the same directory. Update the filename in the data-loading cell if your file is named differently.

Key columns include customer demographics (gender, senior citizen status, dependents), account info (tenure, contract type, payment method), services subscribed (internet, phone, streaming, security, tech support), and billing (monthly/total charges), with Churn as the target.

Workflow


Data cleaning — converted TotalCharges to numeric, filled missing values with the median, dropped the customerID column
Encoding — label-encoded binary columns, one-hot encoded multi-category columns
Exploratory analysis — churn distribution, tenure/charges histograms, correlation heatmap
Feature selection — ANOVA F-scores (SelectKBest) combined with Recursive Feature Elimination (RFE) and domain knowledge, narrowed down to the most relevant features
Modeling — trained four classifiers on an 80/20 stratified train-test split:

Logistic Regression
Decision Tree
Random Forest
Gradient Boosting



Evaluation — accuracy, precision, recall, F1-score, ROC-AUC, confusion matrices, and ROC curves for each model


Results

ModelAccuracyPrecisionRecallF1-ScoreROC-AUCLogistic Regression80.27%64.91%55.88%60.06%84.30%Decision Tree73.74%50.33%81.55%62.24%83.13%Random Forest76.22%53.92%71.66%61.54%83.98%Gradient Boosting80.70%66.56%54.81%60.12%84.29%

Gradient Boosting and Logistic Regression had the best overall accuracy and ROC-AUC, while the Decision Tree achieved the highest recall — useful if catching as many at-risk customers as possible matters more than precision.

Top churn drivers (Random Forest feature importance)


tenure
TotalCharges
MonthlyCharges
Contract_Two year
InternetService_Fiber optic


Customers with shorter tenure, higher monthly charges, fiber optic internet, and month-to-month contracts are most likely to churn.

Requirements

pandas
numpy
matplotlib
seaborn
scikit-learn

Install with:

bashpip install pandas numpy matplotlib seaborn scikit-learn

Usage


Clone this repository
Place the Telco Customer Churn CSV in the project directory
Open Customer_Churn_Analysis_and_Prediction.ipynb in Jupyter Notebook / JupyterLab
Run all cells from top to bottom


bashjupyter notebook Customer_Churn_Analysis_and_Prediction.ipynb

Project Structure

.
├── Customer_Churn_Analysis_and_Prediction.ipynb   # Main analysis notebook
├── Telco_Customer_Churn_Dataset.csv                # Dataset (not included — add your own)
└── README.md

License

This project is open source and available under the MIT License.
