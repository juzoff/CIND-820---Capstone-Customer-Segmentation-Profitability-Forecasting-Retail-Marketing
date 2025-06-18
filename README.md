# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branch Description:
This branch focuses on the initial steps of the CIND-820 Capstone project, including data sampling, statistical verification of representativeness, and exploratory data analysis (EDA) for the Retail Sales and Customer Behavior Analysis dataset (1,000,000+ records, 100+ features). These steps ensure a computationally efficient and representative dataset for subsequent preprocessing and analysis (RQ1: clustering, RQ2: profitability forecasting and statistical analysis, RQ3: predictive modeling).

---
## Branch Components
Dataset Sampling:
- A subset of 30,000 records was extracted using simple random, systematic, and stratified sampling, prioritizing stratification on income_bracket and loyalty_program (Ngai et al., 2009).
- Representativeness was validated using Anderson-Darling tests for numerical features (e.g., total_transactions, avg_transaction_value) and Chi-square tests for categorical features (e.g., product_category, gender). P-values > 0.05 confirmed alignment with the full dataset (Field, 2018).
- Usage: Provided a manageable dataset for EDA, feature engineering, and all RQs.

Exploratory Data Analysis (EDA):
- Conducted using ydata-profiling to assess data integrity, confirming no missing values, identifying outliers (e.g., total_sales: $100–$9,999), and verifying balanced categorical distributions.
- Usage: Informed feature selection (RQ1), statistical test selection (RQ2), and predictive modeling (RQ3).

Temporal Feature Extraction:
- Extracted month and year from datetime columns for trend analysis.
- Dropped original datetime columns to reduce dimensionality (Fader & Hardie, 2009).
- Usage: Captures seasonal and temporal patterns for RQ1, RQ2, and RQ3.

Outlier Detection:
- Used Interquartile Range (IQR) method to identify outliers in numerical columns.
- Usage: Informs subsequent outlier management strategies for robust modeling.

---
## Data Preprocessing Present:
- Split dataset into 70% training and 30% testing sets.
- Engineered binary features (high_value_purchase, high_value_quantity) and renamed total_sales.
- Extracted temporal features from datetime columns and dropped original dates.
- Detected outliers using IQR, identifying high-value transactions and discounts.

---
## Files:
- Data_Preprocessing_SYSTEMATIC.ipynb: Google Colab Notebook for preprocessing the systematic sampled dataset.
- Data_Preprocessing_SRS.ipynb: Google Colab Notebook for preprocessing the simple random sampled dataset.
- Data_Preprocessing_STRATIFIED.ipynb: Google Colab Notebook for preprocessing the stratified sampled dataset.
- Systematic_train_data.csv: Training dataset after preprocessing (systematic sampling).
- Systematic_test_data.csv: Testing dataset after preprocessing (systematic sampling).
- SRS_train_data.csv: Training dataset after preprocessing (simple random sampling).
- SRS_test_data.csv: Testing dataset after preprocessing (simple random sampling).
- STRATIFIED_train_data.csv: Training dataset after preprocessing (stratified sampling).
- STRATIFIED_test_data.csv: Testing dataset after preprocessing (stratified sampling).








