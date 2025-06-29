# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branch Description:
This branch implements statistical analyses for RQ2 (profitability forecasting) in the CIND-820 Capstone project, focusing on understanding relationships between customer clusters, categorical/numeric attributes, and revenue metrics across promotion channels, product categories, and promotion types. It uses the preprocessed training and testing datasets from the Data Preprocessing branch (stratified sampling) to perform Chi-Square tests, Anderson-Darling normality tests, Kruskal-Wallis tests, Friedman tests, and revenue calculations. Visualizations (bar plots, box plots) highlight significant associations and revenue trends. The steps are executed in Google Colab Notebooks, providing insights into factors influencing profitability for retail marketing strategies.

---
## Branch Components
Data Loading:
- Loaded stratified sampled training (srsstat_train_data.csv) and testing (srsstat_test_data.csv) datasets using pandas.read_csv with encoding='ascii'.
- Usage: Ensures consistent data access for statistical analyses (RQ2).

Chi-Square Analysis:
- Performed Chi-Square tests to assess associations between categorical attributes (e.g., last_purchase_month, gender, promotion_type) and clusters, calculating Cramér’s V for effect size (e.g., store_zip_code: Cramér’s V=0.9448, p=0.4677).
- Usage: Identifies significant categorical predictors of cluster membership for RQ2, with attributes having p<0.10 retained for future modeling (RQ3).

Normality Check:
- Conducted Anderson-Darling tests on numeric attributes (e.g., customer_support_calls, total_transactions) to assess normality, with skewness and kurtosis calculated (e.g., non-normal distributions confirmed for most attributes).
- Usage: Informs appropriate statistical methods (non-parametric tests) for RQ2 analyses.

Kruskal-Wallis Analysis:
- Applied Kruskal-Wallis tests to compare numeric attributes (e.g., product_review_count, days_since_last_purchase) across clusters, calculating Eta-Squared for effect size (e.g., product_review_count: H=1625.4439, p=0.0000, Eta-Squared=0.0773).
- Usage: Identifies numeric attributes with significant differences across clusters for RQ2.

Friedman Tests (Promotion Channels):
- Performed Friedman tests to assess differences in total_transactions, avg_transaction_value, total_discounts_received, and total_returned_value across clusters within promotion channels (e.g., In-store, Online, Social Media). Significant differences found for total_transactions (p=0.0498), total_discounts_received (p=0.0498), and total_returned_value (p=0.0498).
- Usage: Evaluates promotion channel effectiveness for RQ2 profitability.

Friedman Tests (Product Categories):
- Conducted Friedman tests to compare total_transactions, avg_transaction_value, total_discounts_received, and total_returned_value across clusters within product categories (e.g., Clothing, Electronics). Significant differences found for total_transactions (p=0.0067), avg_transaction_value (p=0.0224), total_discounts_received (p=0.0067), and total_returned_value (p=0.0067).
- Usage: Identifies product category-specific profitability drivers for RQ2.

Friedman Tests (Promotion Types):
- Applied Friedman tests to evaluate total_transactions, avg_transaction_value, total_discounts_received, and total_returned_value across across clusters within promotion types, with significant differences found (p<0.05).
- Usage: Assesses promotion type impact on profitability for RQ2.

Friedman Tests (seasons):
- Applied Friedman tests to evaluate total_transactions, avg_transaction_value, total_discounts_received, and total_returned_value across across clusters within seasons, with significant differences found (p<0.05).
- Usage: Assesses seasonal impact on profitability for RQ2.

Revenue Calculation:
- Calculated total sales revenue for Cluster 0 (most profitable cluster identified) by promotion channels, product categories, promotion types, and seasons using the formula: total_sales_revenue = (avg_transaction_value * total_transactions - total_returned_value - total_discounts_received). Example: Cluster 0, Social Media: $14250.46; Groceries: $14395.04.
- Usage: Quantifies profitability for the most profitable cluster identified in RQ2 - Monte Carlo Simulation, supporting marketing strategy optimization and project goals focused on retaining and appealing to this target group.

Visualizations:
- Created horizontal bar plots for Chi-Square and Kruskal-Wallis results (p-values, Cramér’s V/eta-squared), color-coded by significance (p<0.05, p<0.10). Generated box plots for Friedman test results (e.g., total_transactions by promotion channel/product category) and bar plots for Cluster 0 revenue by promotion channel/product category.
- Usage: Communicates statistical findings and revenue insights for RQ2 to stakeholders.

---
## Data Preprocessing Present:
- No additional preprocessing performed; relied on preprocessed stratified sampled datasets from Data Preprocessing branch.
- Handled missing values by dropping NaN rows in Friedman test analyses.
- Filtered categorical/numeric columns to ensure compatibility with dataset attributes.

---
## Findings/Results/Insights

---
## Files:
- SRS - RQ2 - Statistical Analysis - Part I: Google Colab Notebook for Chi-Square, normality analyses, and Kruskal-Wallis tests.
- CAPSTONE - Statistical Analysis VIS: Google Colab Notebook visualizing/highlighting attributes with p-value less than or equal to .10.
- Stratified - RQ2 - Statistical Analysis - Part II: Google Colab Notebook for Friedman tests, revenue calculations, and visualizations.
- Project Approach - Steps - Process Map.png (Process Map of Project)







