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

![image](https://github.com/user-attachments/assets/da401351-956b-42db-be44-254034b920d4)
---
## Findings/Results/Insights
- Chi-Square Analysis:
  - Results: 17 categorical attributes significantly associated with clusters (p < 0.05), e.g., last_purchase_month (Cramér’s V: 0.1526, moderate), promotion_end_month (0.1469, moderate), product_manufacture_month (0.1428, moderate). Non-significant: churned (p=0.9803, Cramér’s V: 0.0014). Saved to chi_square_results.csv, chi_square_bar_plot.png.
  - Insights: Temporal attributes (last_purchase_month, promotion_end_month) strongly influence cluster differentiation, guiding RQ3 feature selection. Weak associations (e.g., churned) suggest limited predictive value.
  - Implications: Prioritize temporal and purchase-related features for RQ3 machine learning.
![image](https://github.com/user-attachments/assets/df027c34-b86a-4db9-b419-0d9ced1b5f61)

- Normality Testing:
  - Results: All numeric attributes (e.g., customer_support_calls, product_review_count) non-normal (Anderson-Darling statistic: 74.8782–89.3025, p < 0.05, right-skewed). Saved to normality_results.csv, normality_histograms.png.
  - Insights: Non-normal (log-normal/gamma) distributions justify transformations (e.g., log) for RQ3 modeling.
  - Implications: Apply log-transformations to numeric features in RQ3 to stabilize variance.

- Kruskal-Wallis Test:
  - Results: Significant median differences (p < 0.05) in customer_support_calls (H: 1606.3266, Eta-Squared: 0.0764), product_review_count (H: 1625.4439, 0.0773), days_since_last_purchase (H: 1404.1092, 0.0668). Non-significant: quantity (p=0.8816). Saved to kruskal_wallis_results.csv.
  - Insights: Cluster 0’s high engagement (customer_support_calls, product_review_count) drives differentiation, critical for RQ3 feature selection.
  - Implications: Focus on engagement metrics for predictive modeling.
![image](https://github.com/user-attachments/assets/ef2c4049-55c5-4c8d-9765-26c2a6d0a761)

- Friedman Tests:
  - Results:
    - Promotion Channel: Significant for total_transactions (p=0.0498, Cluster 0: ~57–58), total_discounts_received (p=0.0498), total_returned_value (p=0.0498). Non-significant for avg_transaction_value (p=0.0970).
    - Product Category: Significant for total_transactions (p=0.0067, Cluster 0: ~56.8–57.8, highest in Groceries), avg_transaction_value (p=0.0224), total_discounts_received (p=0.0067), total_returned_value (p=0.0067).
    - Promotion Type: Significant for total_transactions (p=0.0498, Cluster 0: ~56–58, highest in Buy One Get One Free), total_discounts_received (p=0.0498), total_returned_value (p=0.0498).
    - Season: Significant for total_transactions (p=0.0183, Cluster 0: ~56.5–58.9, highest in Winter), avg_transaction_value (p=0.0388), total_discounts_received (p=0.0183).
  - Insights: Cluster 0’s high transaction frequency (e.g., 58.34 for Buy One Get One Free, 58.91 in Winter) and engagement drive profitability across channels, categories, and seasons.
  - Implications: Target Cluster 0 with digital and seasonal campaigns for RQ2 profitability.

- Net Revenue (Cluster 0):
  - Results:
    - Promotion Channel: Online ($14,258.55), Social Media ($14,250.46), In-store ($13,942.04).
    - Product Category: Groceries ($14,395.04), Clothing ($14,349.65), Electronics ($13,682.12).
    - Promotion Type: Buy One Get One Free ($14,561.83), Flash Sale ($14,031.12), 20% Off ($13,847.37).
    - Season: Winter ($14,626.67), Fall ($14,322.39), Summer ($13,783.68).
  - Insights: Groceries, Clothing, Buy One Get One Free, and Winter/Fall campaigns maximize Cluster 0 revenue, driven by high transactions and low returns.
  - Implications: Prioritize digital promotions (Online, Social Media), Groceries/Clothing, and Buy One Get One Free in Winter/Fall for RQ2 profitability.
![image](https://github.com/user-attachments/assets/e96331af-6721-4b49-babe-0b6005f97248)

![image](https://github.com/user-attachments/assets/f706779d-2e8f-4cfa-b306-29c74212c672)

- Comparative Insights:
  - Cluster 0’s high engagement (product_review_count, customer_support_calls) and transaction frequency (total_transactions) drive superior revenue ($14,258.55 Online, $14,626.67 Winter), making it the focus for RQ2 profitability and RQ3 modeling. Temporal attributes (last_purchase_month) and engagement metrics are key predictors for RQ3. Digital channels, Groceries/Clothing, and Buy One Get One Free promotions in Winter/Fall optimize marketing strategies.

---
## Files:
- SRS - RQ2 - Statistical Analysis - Part I: Google Colab Notebook for Chi-Square, normality analyses, and Kruskal-Wallis tests.
- CAPSTONE - Statistical Analysis VIS: Google Colab Notebook visualizing/highlighting attributes with p-value less than or equal to .10.
- Stratified - RQ2 - Statistical Analysis - Part II: Google Colab Notebook for Friedman tests, revenue calculations, and visualizations.
- Project Approach - Steps - Process Map.png (Process Map of Project)







