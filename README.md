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
- Standardized numerical features (e.g., total_transactions, avg_purchase_value) to mean = 0, standard deviation = 1 using StandardScaler, fitted on training data to prevent leakage (Hastie et al., 2009).
- Usage: Supports distance-based K-Means clustering (RQ1).

Dimensionality Reduction:
- Applied Principal Component Analysis (PCA) to reduce preprocessed features to 2 components (PC1, PC2) capturing key variance, with loadings analyzed to identify top contributors (e.g., product_review_count, days_since_last_purchase) (Jolliffe & Cadima, 2016).
- Usage: Reduces dimensionality for efficient K-Means clustering (RQ1).

K-Means Clustering:
- Performed K-Means clustering on training data, determining optimal clusters (k=3) using Elbow method and silhouette scores. Clusters were assigned to training and testing sets, with characteristics visualized via PCA scatter plots and heatmaps (Jolliffe & Cadima, 2016).
- Usage: Segments customers for RQ1, providing clusters for RQ2 analysis.

Normality Check for Monte Carlo Simulation:
- Conducted Anderson-Darling tests on variables (total_transactions, avg_transaction_value, total_returned_value, total_discounts_received) per cluster, confirming non-normal distributions (log-normal or gamma suggested) (Field, 2018).
- Usage: Informs distribution assumptions for Monte Carlo simulation (RQ2).

Monte Carlo Simulation:
- Simulated total sales revenue per cluster using the formula: total_sales_revenue = (avg_transaction_value * total_transactions - total_returned_value - total_discounts_received) * (1 - churned). Used log-normal distributions for continuous variables, Poisson for total_transactions, and binomial for churn, with 100,000 simulations (Fader & Hardie, 2009; Toptal, 2018).
- Usage: Estimates probabilistic revenue ranges for RQ2, supporting profitability forecasting.

---
## Data Preprocessing Present:
- Imputed missing values with mean (numerical) and mode (categorical).
- One-hot encoded categorical variables and standardized numerical features.
- Reduced dimensionality to 2 PCA components for clustering.
- Checked normality of Monte Carlo input variables, confirming log-normal distributions.

---
## Files:
- D



