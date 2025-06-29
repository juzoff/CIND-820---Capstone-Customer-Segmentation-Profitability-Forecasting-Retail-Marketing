# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Branch Description:
This branch implements machine learning models for RQ3 (predictive modeling of customer clusters) in the CIND-820 Capstone project, aiming to classify customers into clusters (0, 1, 2) for targeted marketing, with a focus on Cluster 0, identified as the high-value segment in RQ2 Monte Carlo simulations. Decision Tree, Random Forest, and K-Nearest Neighbors (KNN) models are evaluated with and without SMOTE/RandomUnderSampler balancing, using all features (p-value ≤ 0.10 from RQ2) and model-specific selected features via Recursive Feature Elimination with Cross-Validation (RFECV) or feature importance ranking. The model variation with the highest Cluster 0 recall is further tuned using an expanded hyperparameter grid and class weights to optimize performance. Evaluations include recall, accuracy, precision, specificity, and 5-fold cross-validation, executed in Google Colab Notebooks to inform retail marketing strategies.

---
## Branch Components
Data Loading:
- Loaded stratified sampled training (srsstat_train_data.csv, 21,000 entries) and testing (srsstat_test_data.csv, 9,000 entries) datasets using pandas.read_csv with encoding='ascii' (Wickham, 2016).
- Target Variable: cluster (0, 1, 2), with Cluster 0 (6,913 train samples) as the high-value segment.
- Usage: Provides input for model training and evaluation (RQ3).

Data Balancing:
- Applied SMOTE to oversample Clusters 0 and 2 to 10,000 samples each and RandomUnderSampler to reduce Cluster 1 to 10,000 (total: 30,000 samples) for balanced variations (Chawla et al., 2002).
- Usage: Ensures balanced class distribution to improve model performance for Cluster 0.

Feature Preprocessing:
- Filtered features with p-value ≤ 0.10 from RQ2 (e.g., last_purchase_month, product_review_count, total_transactions).
- Used ColumnTransformer with SimpleImputer (mean for numeric, most_frequent for categorical), StandardScaler for numeric features, and OneHotEncoder (drop='first', handle_unknown='ignore') for categorical features (Hastie et al., 2009).
- Usage: Prepares features for model training and ensures consistency across datasets.

Feature Selection:
- Decision Tree: Applied RFECV with DecisionTreeClassifier (3-fold CV, accuracy scoring, step=1) to select optimal features (Pedregosa et al., 2011).
- Random Forest: Used RFECV with RandomForestClassifier (n_estimators=50, random_state=42, 3-fold CV, accuracy scoring, step=1) to select optimal features.
- KNN: Selected top 10 features based on feature importance from RandomForestClassifier (n_estimators=50, random_state=42) to reduce dimensionality.
- Usage: Reduces feature set to improve model performance and interpretability for RQ3.

Model Training and Variations:
- Decision Tree:
  - Algorithm: DecisionTreeClassifier with GridSearchCV (parameters: max_depth=[None, 10, 15, 20], min_samples_split=[2, 5, 10], min_samples_leaf=[1, 2, 4], criterion='gini') (Breiman et al., 1984).
  - Variations: (1) Without Balancing – All Features, (2) Without Balancing – Selected Features, (3) With Balancing – All Features, (4) With Balancing – Selected Features.
- Random Forest:
  - Algorithm: RandomForestClassifier with GridSearchCV (parameters: n_estimators=[50, 100, 150], max_depth=[None, 10, 15, 20], min_samples_split=[2, 5, 10], min_samples_leaf=[1, 2, 4], criterion='gini') (Breiman, 2001).
  - Variations: Same as Decision Tree.
- KNN:
  - Algorithm: KNeighborsClassifier with RandomizedSearchCV (parameters: n_neighbors=3–20, weights=['uniform', 'distance'], metric=['euclidean', 'manhattan', 'minkowski']) (Cover & Hart, 1967).
  - Variations: Same as Decision Tree.
- Usage: Evaluates multiple models to identify the best for Cluster 0 prediction.

Further Hyperparameter Tuning:
- Selected the model variation with the highest Cluster 0 recall (Random Forest, assumed based on robustness).
- Data: Combined dataset (30,000 entries) with 50 significant features, SMOTE oversampled Cluster 0 to 12,000, Cluster 2 to 10,000, and RandomUnderSampler reduced Cluster 1 to 10,000 (total: 32,000).
- Model: RandomForestClassifier with class weights (Cluster 0: 1.5, Cluster 1: 1.0, Cluster 2: 1.0) and GridSearchCV (expanded grid: n_estimators=[50, 100, 150, 200, 250], max_depth=[None, 10, 15, 20, 25, 30], min_samples_split=[2, 5, 10], min_samples_leaf=[1, 2, 4, 6, 8], criterion='gini') using weighted F1-score (Breiman, 2001).
- Usage: Optimizes Cluster 0 recall for targeted marketing.

Model Evaluation:
- Metrics: Recall for Cluster 0 (primary), accuracy, precision, specificity per cluster, and 5-fold cross-validation mean accuracy (weighted F1-score for tuned model) (Kohavi, 1995).
- Outputs: Classification reports, confusion matrices, and feature importances saved to CSV files.
- Usage: Quantifies model performance and stability for RQ3 deployment.

---
## Data Preprocessing Present:
- Filtered features with p-value ≤ 0.10 from RQ2 statistical analyses.
- Imputed missing values (mean for numeric, most_frequent for categorical), scaled numeric features, and one-hot encoded categorical features.
- Applied SMOTE and RandomUnderSampler for balanced variations (30,000 samples, 10,000 per cluster; tuned model: 32,000 samples with Cluster 0 at 12,000).
---
## Files:
- 




