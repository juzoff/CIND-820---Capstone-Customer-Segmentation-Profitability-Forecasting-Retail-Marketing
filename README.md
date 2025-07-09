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

![image](https://github.com/user-attachments/assets/9202f0bf-03b3-49f7-847b-20f6ddc9b934)

---
## Findings/Results/Insights
- Simple Random Sampling (SRS):
  - Results: Loaded Simple_Random_Sample.csv (30,000 rows, 78 attributes); split into 70% train (21,000 rows), 30% test (9,000 rows). Added high_value_purchase (>75th percentile avg_purchase_value), high_value_quantity (>75th percentile quantity); renamed total_sales to total_sales_over_lastyear. Binned date columns (e.g., transaction_date) to month/year; dropped originals. No outliers in temporal attributes (e.g., days_since_last_purchase, transaction_month) via IQR method. Saved to srsstat_train_data.csv, srsstat_test_data.csv.
  - Insights: Clean temporal distributions ensure reliable clustering (RQ1). Feature engineering enhances high-value customer identification (RQ3). No missing values support robust analysis.
  - Implications: Ideal for unbiased RQ1 clustering and RQ3 modeling due to clean data.

- Stratified Sampling:
  - Results: Loaded Stratified_Sample.csv (30,000 rows, 78 attributes); split into 70% train (21,000 rows), 30% test (9,000 rows). Added high_value_purchase, high_value_quantity; renamed total_sales. Binned date columns; dropped originals. No outliers in key attributes (e.g., age, unit_price, avg_purchase_value) via IQR method. Saved to stratified_train_data.csv, stratified_test_data.csv.
  - Insights: Stable distributions support income-based segmentation (RQ1). Feature engineering aids high-value customer prediction (RQ3). No missing values ensure reliability.
  - Implications: Strong for income-driven RQ1 and RQ3 analyses, leveraging perfect income_bracket fidelity.

- Systematic Sampling:
  - Results: Loaded Systematic_Sample.csv (30,000 rows, 78 attributes); split into 70% train (21,000 rows), 30% test (9,000 rows). Added high_value_purchase, high_value_quantity; renamed total_sales. Binned date columns; dropped originals. No outliers in key attributes (e.g., customer_id, membership_years) via IQR method. Saved to systematic_train_data.csv, systematic_test_data.csv.
  - Insights: Clean distributions, but potential ordering bias (e.g., customer_id) requires validation. Feature engineering supports RQ1 and RQ3.
  - Implications: Suitable for RQ1 and RQ3 but needs bias validation due to systematic sampling risks.

- Comparative Insights:
  - All methods yield clean datasets with no outliers or missing values, ensuring robust RQ1 clustering and RQ3 modeling.
---
## Files:
- Data_Preprocessing_SYSTEMATIC.ipynb: Google Colab Notebook for preprocessing the systematic sampled dataset
- Data_Preprocessing_SRS.ipynb: Google Colab Notebook for preprocessing the simple random sampled dataset
- Data_Preprocessing_STRATIFIED.ipynb: Google Colab Notebook for preprocessing the stratified sampled dataset
- Systematic_train_data.csv: Training dataset after preprocessing (systematic sampling)
- Systematic_test_data.csv: Testing dataset after preprocessing (systematic sampling)
- SRS_train_data.csv: Training dataset after preprocessing (simple random sampling)
- SRS_test_data.csv: Testing dataset after preprocessing (simple random sampling)
- STRATIFIED_train_data.csv: Training dataset after preprocessing (stratified sampling)
- STRATIFIED_test_data.csv: Testing dataset after preprocessing (stratified sampling)
- Project Approach - Steps - Process Map.png (Process Map of Project)








