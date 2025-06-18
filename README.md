# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branch Description:
This branch focuses on the initial steps of the CIND-820 Capstone project, including data sampling, statistical verification of representativeness, and exploratory data analysis (EDA) for the Retail Sales and Customer Behavior Analysis dataset (1,000,000+ records, 100+ features). These steps ensure a computationally efficient and representative dataset for subsequent preprocessing and analysis (RQ1: clustering, RQ2: profitability forecasting and statistical analysis, RQ3: predictive modeling).

---
Dataset Sampling:
- A subset of 30,000 records was extracted using simple random, systematic, and stratified sampling, prioritizing stratification on income_bracket and loyalty_program (Ngai et al., 2009).
- Representativeness was validated using Anderson-Darling tests for numerical features (e.g., total_transactions, avg_transaction_value) and Chi-square tests for categorical features (e.g., product_category, gender). P-values > 0.05 confirmed alignment with the full dataset (Field, 2018).
- Usage: Provided a manageable dataset for EDA, feature engineering, and all RQs.

Exploratory Data Analysis (EDA):
- Conducted using ydata-profiling to assess data integrity, confirming no missing values, identifying outliers (e.g., total_sales: $100–$9,999), and verifying balanced categorical distributions (e.g., gender, loyalty_program) (Jolliffe & Cadima, 2016).
Usage: Informed feature selection (RQ1), statistical test selection (RQ2), and predictive modeling (RQ3).

---

## Files:

---

## Deliverables:

