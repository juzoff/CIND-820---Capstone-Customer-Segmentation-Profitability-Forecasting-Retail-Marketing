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

---
## Files:
- D



