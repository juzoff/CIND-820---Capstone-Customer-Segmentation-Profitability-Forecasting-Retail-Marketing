# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branch Description:
This branch focuses on the initial steps of the CIND-820 Capstone project, including data sampling, statistical verification of representativeness, and exploratory data analysis (EDA) for the Retail Sales and Customer Behavior Analysis dataset (1,000,000+ records, 100+ features). These steps ensure a computationally efficient and representative dataset for subsequent preprocessing and analysis (RQ1: clustering, RQ2: profitability forecasting and statistical analysis, RQ3: predictive modeling).

---
## Branch Components
Train-Test Partitioning:
- Split the 30,000-record sampled dataset into 70% training (21,000 rows) and 30% testing (9,000 rows) sets with a random state of 42 and shuffling enabled to ensure reproducibility and prevent data leakage.
- Usage: Provides unbiased datasets for model training and evaluation across all RQs.

Feature Engineering:
- Created binary features: high_value_purchase (avg_purchase_value > 75th percentile) and high_value_quantity (quantity > 75th percentile) to flag high-value transactions and bulk buyers (Fader & Hardie, 2009).
- Renamed total_sales to total_sales_over_lastyear for clarity.
- Usage: Enhances model interpretability and predictive power for RQ1, RQ2, and RQ3.

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








