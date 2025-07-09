# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branch Description:
This branch implements preprocessing and analysis for RQ1 (customer segmentation via K-Means clustering) and RQ2 (profitability forecasting via Monte Carlo simulation) in the CIND-820 Capstone project. It uses the preprocessed training and testing datasets from the Data Preprocessing branch (simple random sampling, SRS) to perform encoding, scaling, dimensionality reduction, clustering, and Monte Carlo simulation for revenue forecasting per cluster. The steps are executed in a Google Colab Notebook, preparing data for actionable retail marketing insights.

---
## Branch Components
Handling Missing Values:
- Imputed missing numerical values with mean and categorical values with mode using SimpleImputer in a preprocessing pipeline (Hastie et al., 2009).
- Usage: Ensures complete datasets for clustering (RQ1) and Monte Carlo simulation (RQ2).

Categorical Encoding:
- One-hot encoded categorical variables (e.g., gender, product_category) using OneHotEncoder with drop='first' to avoid multicollinearity and handle_unknown='ignore' for robustness, grouping rare categories (Hastie et al., 2009).
- Usage: Prepares categorical data for K-Means clustering (RQ1).

Numerical Scaling:
- Standardized numerical features (e.g., total_transactions, avg_purchase_value) to mean = 0, standard deviation = 1 using StandardScaler, fitted on training data to prevent leakage.
- Usage: Supports distance-based K-Means clustering (RQ1).

Dimensionality Reduction:
- Applied Principal Component Analysis (PCA) to reduce preprocessed features to 2 components (PC1, PC2) capturing key variance, with loadings analyzed to identify top contributors (e.g., product_review_count, days_since_last_purchase).
- Usage: Reduces dimensionality for efficient K-Means clustering (RQ1).

K-Means Clustering:
- Performed K-Means clustering on training data, determining optimal clusters (k=3) using Elbow method and silhouette scores. Clusters were assigned to training and testing sets, with characteristics visualized via PCA scatter plots and heatmaps.
- Usage: Segments customers for RQ1, providing clusters for RQ2 analysis.

Normality Check for Monte Carlo Simulation:
- Conducted Anderson-Darling tests on variables (total_transactions, avg_transaction_value, total_returned_value, total_discounts_received) per cluster, confirming non-normal distributions (log-normal or gamma suggested).
- Usage: Informs distribution assumptions for Monte Carlo simulation (RQ2).

Monte Carlo Simulation:
- Simulated total sales revenue per cluster using the formula: total_sales_revenue = (avg_transaction_value * total_transactions - total_returned_value - total_discounts_received) * (1 - churned). Used log-normal distributions for continuous variables, Poisson for total_transactions, and binomial for churn, with 100,000 simulations.
- Usage: Estimates probabilistic revenue ranges for RQ2, supporting profitability forecasting.

Mean Revenue Analysis:
- Calculated mean total sales revenue and 5th/95th percentiles per cluster across sampling methods (SRS, stratified, systematic), e.g., SRS Cluster 0: $8739.37 (95th: $36540.89), Stratified Cluster 1: $8195.98 (95th: $33019.36).
- Usage: Quantifies revenue potential for RQ2, enabling comparison across sampling methods. Used in identifying most profitable cluster across sampled datasets.

Non-Churned Revenue Analysis:
- Computed mean non-churned revenue per cluster across sampling methods, e.g., SRS Cluster 0: $17064.81, Systematic Cluster 2: $15881.39.
- Usage: Highlights revenue from retained customers for RQ2, informing retention strategies. Used in identifying most profitable cluster across sampled datasets.

Churn Sensitivity Analysis:
- Analyzed mean revenue under varying churn rates (10% to 90%) per cluster and sampling method, e.g., SRS Cluster 0 at 10% churn: $15416.33, at 90% churn: $1695.87.
- Usage: Assesses revenue sensitivity to churn for RQ2, guiding marketing interventions. Used in identifying most profitable cluster across sampled datasets.

Plots to Visualize Cluster Attribute Profiles with Key PCA Loadings:
- Generated parallel coordinates plots to visualize standardized attribute profiles (e.g., product_review_count, distance_to_store, online_purchases) for each cluster, annotated with the highest PCA loadings identified (e.g., product_review_count PC1: 0.352, PC2: 0.033) to highlight key drivers.
- Usage: Clarifies cluster characteristics (e.g., Cluster 0: high engagement, distant store access; Cluster 1: in-store bulk purchases; Cluster 2: discount-driven, low frequency) for RQ1, aiding stakeholder interpretation.
  
Visualizations:
- Created bar plots for mean total sales revenue (with 5th/95th percentiles) and non-churned revenue, line plots for churn sensitivity, and parallel coordinates plots to visualize cluster attribute profiles with PCA loadings (e.g., product_review_count PC1: 0.352, PC2: 0.033).
- Usage: Communicates cluster characteristics and revenue insights for RQ1 and RQ2 to stakeholders.

---
## Data Preprocessing Present:
- Imputed missing values with mean (numerical) and mode (categorical).
- One-hot encoded categorical variables and standardized numerical features.
- Reduced dimensionality to 2 PCA components for clustering.
- Checked normality of Monte Carlo input variables, confirming log-normal distributions.

![image](https://github.com/user-attachments/assets/661b171c-3cbd-4ac4-959b-b11eb57e9b38)

---
## Findings/Results/Insights

- Clustering (RQ1) - SRS, Stratified & Systematic Datasets:
  - Results: All three datasets confirmed 3 optimal clusters via silhouette scores and elbow method. 
  - Insights: Consistent cluster structures validate segmentation across sampling methods.

![image](https://github.com/user-attachments/assets/af7a3545-c16a-4ca4-8084-d387863be39e)
![image](https://github.com/user-attachments/assets/8307e6a8-a0e5-4699-b119-8c22153907df)
![image](https://github.com/user-attachments/assets/d5522df3-07b1-43fc-8365-126ade4ddcc2)


- Monte Carlo Simulation (RQ2) - SRS Dataset:
  - Results: Cluster 0: Highest mean revenue ($8,739.37), non-churned $17,064.81 (5th-95th: $0.00–$36,540.89). Cluster 1: $6,184.55 (non-churned $12,200.96). Cluster 2: $7,135.47 (non-churned $13,991.38). Churn sensitivity: 89% revenue drop at 90% churn (Cluster 0: $15,416.33 at 10% to $1,695.87 at 90%). Non-normal distributions confirmed (Anderson-Darling statistics: 74.8782–89.3025). Saved to srs_monte_carlo_results.csv.
  - Insights: Cluster 0’s high revenue and churn sensitivity prioritize retention strategies. Non-normal distributions support log-normal assumptions.
  - Implications: Guides RQ2 profitability forecasting and RQ3 feature selection (e.g., total_transactions).

![image](https://github.com/user-attachments/assets/5eab3026-35bb-4e60-8bd9-d11b32fb33df)


- Monte Carlo Simulation (RQ2) - Stratified & Systematic Datasets:
  - Results: Stratified: Cluster 0 ($7,001.12), Cluster 1 ($8,195.98), Cluster 2 ($6,106.06). Systematic: Cluster 0 ($7,000.56), Cluster 1 ($6,602.32), Cluster 2 ($7,809.46). Saved to stratified_monte_carlo_results.csv, systematic_monte_carlo_results.csv.
  - Insights: SRS’s higher Cluster 0 revenue reflects its representativeness. Stratified and Systematic show consistent trends but lower revenue.
  - Implications: SRS is preferred for RQ2; Stratified suits income-focused analyses.

- Comparative Insights:
  - SRS’s Cluster 0 is the high-value segment ($8,739.37), ideal for RQ2 statistical analysis and RQ3 machine learning models due to unbiased sampling. Stratified supports income-driven analyses, while Systematic requires bias validation. High churn sensitivity across datasets emphasizes retention strategies for RQ2 and predictive features (e.g., days_since_last_purchase) for RQ3.

- Further Clustering Insights (RQ1) - SRS Dataset:
  - Results: K-Means with PCA (2 components) identified 3 optimal clusters via silhouette scores and elbow method. 
    - Cluster 0 (Multi-Channel High-Frequency Engaged Shoppers with Distant Store Access): Represents customers who shop frequently across online, in-store, and social media channels, live farther from stores, and engage actively with the brand.
      - PCA Loadings: 
        - High PC1 loadings for num__product_review_count (0.351882), num__days_since_last_purchase (0.320798), and num__customer_support_calls (0.233369) indicate strong engagement. High PC2 loadings for num__distance_to_store (0.305939), num__last_purchase_month (0.272100), and num__total_transactions (0.260227) reflect frequent digital purchases and distant store locations.
      - PCA1/PCA2 for Each Individual Attribute:
        -  num__distance_to_store (0.300149 from PC2), num__online_purchases (0.223115 from PC2), num__product_review_count (0.167017 from PC1), and num__total_transactions (0.255302 from PC2) confirm high digital engagement and transaction frequency.
      - Sales Revenue
        - Balanced across in-store ($13,942.04), online ($14,258.55), and social media ($14,250.46), totaling $42,551.05, showing multi-channel activity.
      - Representation:
        - Tech-savvy, high-frequency shoppers who engage across channels, ideal for digital marketing campaigns.
      ![image](https://github.com/user-attachments/assets/cd3c1f6e-7291-4f1e-bd58-f2c67e17bacb)
      - *The above chart was used through standardizing the attribute values (excluding the "Cluster" column) by applying min-max scaling to ensure all features are on a comparable scale (0 to 1), then creating a parallel coordinates plot to visualize the standardized profiles of three customer clusters, with each line representing a cluster's characteristics across multiple features, annotated with PCA loadings for interpretability, and includes a descriptive caption explaining the clusters and axes*

    - Cluster 1 (Proximity-Driven Frequent In-Store Bulk Shoppers): High total_items_purchased (0.214929, PC2), low online_purchases (-0.200433, PC2), close stores (distance_to_store: -0.269636, PC2).
    - Cluster 2 (Infrequent Discount-Focused Long-Term Shoppers): High days_since_last_purchase (0.353464, PC1), membership_years (0.225427, PC1), discount_applied (0.203976, PC1), low engagement (product_review_count: -0.387713, PC1).
  - Insights: Cluster 0’s multi-channel engagement and high revenue make it a priority for cross-channel campaigns. Cluster 1 suits localized in-store offers. Cluster 2 requires discount-driven retention strategies.
  - Implications: Cluster 0’s versatility drives RQ2 profitability and RQ3 predictive modeling.
---
## Files:
- SRS_RQ1_Clustering_&_RQ2_Monte_Carlo_Simulation: Google Colab Notebook for SRS K-Means clustering, Monte Carlo simulation, and revenue analysis.
- Systematic_RQ1_Clustering_&_RQ2_Monte_Carlo_Simulation: Google Colab Notebook for Systematic K-Means clustering, Monte Carlo simulation, and revenue analysis.
- Stratified_RQ1_Clustering_&_RQ2_Monte_Carlo_Simulation: Google Colab Notebook for Stratified K-Means clustering, Monte Carlo simulation, and revenue analysis.
- Monte Carlo Simulation - Visual Comparison
- Cluster Differences - Characteristics Differences - Visual
- Project Approach - Steps - Process Map.png (Process Map of Project)






