# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branch Description:
This branch focuses on the initial steps of the CIND-820 Capstone project, including data sampling, statistical verification of representativeness, and exploratory data analysis (EDA) for the Retail Sales and Customer Behavior Analysis dataset (1,000,000+ records, 100+ features). These steps ensure a computationally efficient and representative dataset for subsequent preprocessing and analysis (RQ1: clustering, RQ2: profitability forecasting and statistical analysis, RQ3: predictive modeling).

---
## Branch Components
Dataset Sampling:
- A subset of 30,000 records was extracted using simple random, systematic, and stratified sampling.
- Representativeness was validated using Anderson-Darling tests for numerical features (e.g., total_transactions, avg_transaction_value) and Chi-square tests for categorical features (e.g., product_category, gender). P-values > 0.05 confirmed alignment with the full dataset (Field, 2018).
- Usage: Provided a manageable dataset for EDA, feature engineering, and all RQs.

Exploratory Data Analysis (EDA):
- Conducted using ydata-profiling to assess data integrity, confirming no missing values, identifying outliers (e.g., total_sales: $100–$9,999), and verifying balanced categorical distributions.
- Usage: Informed feature selection (RQ1), statistical test selection (RQ2), and predictive modeling (RQ3).

---
## Data Preprocessing Present:
- Extracted a 30,000-record sample using simple random, systematic, and stratified sampling to ensure computational efficiency.
- Validated sample representativeness with Anderson-Darling and Chi-square tests, achieving p-values > 0.05.
- Conducted EDA using ydata-profiling to confirm no missing values, identify outliers, and guide feature engineering.

---
## Files:
- Collab notebook (CAPSTONE_Three_Sampling_Methods,_Statistical_Verification,_EDA.ipynb)
- 4 html reports via ydata.profiling (Full Dataset, Simple Random Sampling Dataset, Stratified Dataset, Systematic Dataset)
- 3 comparison reports (full dataset vs the 3 other sampled datasets)
- Excel file visualizing the statistical verification for the 3 sampled datasets (SamplingMethods-Statistical Verification.xlsx)
- Project Approach - Steps - Process Map.png (Process Map of Project)


