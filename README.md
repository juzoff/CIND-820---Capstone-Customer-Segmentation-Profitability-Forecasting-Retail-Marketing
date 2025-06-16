# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branches 
* **main** : _Project Overview_
* #1 **Beginning Steps, Sampling, Statistical Verification, EDA**
* #2 **Data Preprocessing**
* #3 **RQ1 - Clustering & RQ2- Monte Carlo Simulation**

---

## Project Description:
This project employs a comprehensive, data-driven methodology to address customer segmentation, profitability forecasting, and marketing optimization using a large-scale retail sales dataset with over one million records and 100+ features. The approach integrates advanced statistical and machine learning techniques to deliver actionable insights for retail decision-making in a competitive landscape. 
- Data Sampling and Validation: To ensure computational efficiency while maintaining representativeness, a sample of 30,000 records is drawn using simple random, systematic, and stratified sampling techniques. The sample’s representativeness is validated using Kolmogorov-Smirnov (K-S) tests for numeric attributes and Chi-square tests for categorical attributes, testing the null hypothesis (H₀) that the sample’s distribution matches the full dataset’s distribution against the alternative hypothesis (H₁) that they differ. P-values will assess statistical significance, ensuring the sample reflects real-world retail patterns (e.g., average transaction values and purchase frequency aligned with industry benchmarks from McKinsey or Forrester).
- Data Preprocessing: Post-sampling, the dataset is split into training and test sets (70/30 split) to prevent data leakage and support robust model development and evaluation. Feature engineering includes date binning and feature extraction from datetime data (e.g., extracting day, month, or purchase recency). Missing values, if present, are handled via imputation (e.g., mean/median for numeric, mode for categorical) or removal, based on data characteristics. Outliers, if detected, are addressed using robust methods like IQR-based filtering or capping to ensure model stability.
- Customer Segmentation (RQ1): K-Means clustering, combined with Principal Component Analysis (PCA), is used to segment customers based on transactional and demographic attributes. The optimal clustering configuration is selected based on the highest silhouette score, ensuring distinct and meaningful customer groups. PCA loadings and means for the top two principal components (PCA 1 & 2) are analyzed to identify key attributes driving segment differences, enabling interpretable insights into customer behaviors for stakeholders.
- Profitability Forecasting (RQ2): Monte Carlo simulation estimates probabilistic revenue ranges per segment, prioritizing segments with the highest sales revenue per customer (e.g., > $10,000). Statistical tests (ANOVA, Kruskal-Wallis, Chi-square) identify significant attributes (p < 0.10) influencing profitability, such as purchase frequency and churn risk. The Friedman test (or Block Design Two-Way ANOVA) evaluates differences in key metrics—total_transactions, avg_transaction_value, and avg_discount_per_transaction—across customer clusters within promotion channel blocks (Online, In-Store, Social Media). The segment-level revenue formula, total_sales_revenue = (total_transactions × avg_transaction_value – total_transactions × avg_discount_per_transaction) × (1 − churned), guides channel-specific revenue estimates, informing resource allocation for marketing and inventory planning.
- Predictive Modeling (RQ3): Machine learning models—Decision Trees, Random Forests, K-Nearest Neighbors, and Multinomial Logistic Regression—are applied to predict the top-performing sales revenue cluster. Recursive Feature Elimination (RFE) and SMOTE address feature selection and class imbalance, respectively. Models are evaluated based on recall (target ≥ 0.90) for the high-value cluster, with feature importance rankings and confusion matrices ensuring interpretability for non-technical stakeholders. Key predictors, such as loyalty program participation, are explained in simple terms to support real-time decision-making.
- Interpretability and Actionability: Analytical outputs are designed for transparency and practical application. Clustering results highlight influential attributes driving segment differences, Monte Carlo outputs provide probabilistic revenue estimates for prioritizing high-value segments, and machine learning models offer clear feature importance rankings. These insights enable retailers to design personalized promotions, optimize marketing spend, align inventory with high-value segments, and enhance customer retention, fostering data-driven decisions to maximize profitability in a competitive retail environment.


---

## Research Questions:
1. Can customers be grouped into distinct clusters based on behavior and demographics to uncover underlying customer segments?
2. Which attributes are statistically significant in differentiating customer clusters, and how can Monte Carlo simulation, combined with the Friedman test, estimate customer segment value, including channel-specific revenue estimates across Online, In-Store, and Social Media promotion channels?
3. Which machine learning algorithm performs best in identifying the most valuable customer cluster based on significant attributes?

---

## Dataset Chosen:
https://www.kaggle.com/datasets/utkalk/large-retail-data-set-for-eda/data

---


