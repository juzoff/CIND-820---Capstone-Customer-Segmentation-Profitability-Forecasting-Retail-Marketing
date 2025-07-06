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
- Conducted using ydata-profiling to assess data integrity, confirming no missing values, identifying outliers, and verifying balanced categorical distributions.
- Usage: Informed feature selection (RQ1), statistical test selection (RQ2), and predictive modeling (RQ3).

Visualization:
- Table visualizing the statistical verification for the 3 sampled datasets.

---
## Data Preprocessing Present:
- Extracted a 30,000-record sample using simple random, systematic, and stratified sampling to ensure computational efficiency.
- Validated sample representativeness with Anderson-Darling and Chi-square tests.
- Conducted EDA using ydata-profiling to confirm no missing values, identify outliers, and guide feature engineering.

---
## Findings/Results/Insights
- Simple Random Sampling (SRS):
  - Results: 2 attributes with p ≤ 0.05 (promotion_id: p=0.0036, product_category: p=0.041); 6 with p ≤ 0.10 (incl. avg_transaction_value: p=0.0531). Saved to srs_ks_results.csv, srs_chi_square_results.csv.
  - Insights: Most representative (fewest differences). Minor product_category bias may affect RQ1 segmentation. avg_transaction_value (~0.61% mean increase) has minimal impact.
  - Implications: Ideal for unbiased RQ1 clustering and RQ3 machine learning. Monitor product_category in RQ2.
- Stratified Sampling:
  - Results: 3 attributes with p ≤ 0.05 (transaction_id: p=0.0204, max_single_purchase_value: p=0.0230, customer_state: p=0.035); 7 with p ≤ 0.10 (incl. payment_method: p=0.064). Saved to stratified_ks_results.csv, stratified_chi_square_results.csv.
  - Insights: Moderately representative, perfect for income_bracket (p=1.0). max_single_purchase_value and customer_state may bias high-value and regional analyses.
  - Implications: Strong for income-driven RQ1 clustering and RQ3 modeling. Validate biases in RQ2 profitability.
- Systematic Sampling:
  - Results: 3 attributes with p ≤ 0.05 (customer_id: p=0.0056, product_material: p=0.007, product_brand: p=0.020); 10 with p ≤ 0.10 (incl. product_return_rate: p=0.0537). Saved to systematic_ks_results.csv, systematic_chi_square_results.csv.
  - Insights: Least representative due to ordering bias (customer_id). product_material and product_brand may skew product marketing insights.
  - Implications: Risky for RQ1 and RQ3 due to bias. Requires validation before use.
- Comparative Insights:
  - SRS is most representative (2 at p ≤ 0.05, 6 at p ≤ 0.10), best for RQ1 and RQ3.
  - Stratified excels for income-based RQ2 and RQ3 (3 at p ≤ 0.05, 7 at p ≤ 0.10).
  - Systematic is least reliable (3 at p ≤ 0.05, 10 at p ≤ 0.10). 

---
## Files:
- Collab notebook (CAPSTONE_Three_Sampling_Methods,_Statistical_Verification,_EDA.ipynb)
- 4 html reports via ydata.profiling (Full Dataset, Simple Random Sampling Dataset, Stratified Dataset, Systematic Dataset)
- 3 comparison reports (full dataset vs the 3 other sampled datasets)
- Excel file visualizing the statistical verification for the 3 sampled datasets (SamplingMethods-Statistical Verification.xlsx)
- Project Approach - Steps - Process Map.png (Process Map of Project)


