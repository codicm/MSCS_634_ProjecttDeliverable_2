# Deliverable 3 README: Classification, Clustering, and Pattern Mining

## 1) Deliverable 3 Overview

This deliverable extends the healthcare data mining project with three complementary approaches:

- Classification to predict abnormal test outcomes.
- Clustering to segment patients into data-driven groups.
- Association rule mining to uncover recurring clinical and operational patterns.

The analysis was performed using the cleaned dataset from prior deliverables and implemented in the notebook `Deliverable3_Classification_Clustering_PatternMining.ipynb`.

## 2) Key Insights

### Classification Insights

- Two baseline classification models were developed:
  - Decision Tree
  - k-Nearest Neighbors (k-NN)
- Hyperparameter tuning was applied to Decision Tree using GridSearchCV with F1 score as the optimization metric.
- Model evaluation (confusion matrix, ROC curve, Accuracy, F1, ROC-AUC) showed that:
  - Model behavior differs significantly between overall accuracy and minority-class sensitivity.
  - Tuning improved parameter selection transparency and provided a more principled model choice.

### Clustering Insights

- K-Means clustering was applied to standardized numeric features (`age`, `billing_amount`, `room_number`, `length_of_stay`).
- Silhouette analysis was used to select a data-supported cluster count.
- Cluster profiling identified distinct patient segments with different average utilization and cost characteristics.
- PCA visualization made cluster separation easier to interpret and communicate.

### Pattern Mining Insights

- Apriori-based association rule mining discovered meaningful co-occurrences across:
  - medical condition
  - medication
  - admission type
  - insurance provider
  - test results
  - gender and blood type
- Rule metrics (support, confidence, lift) helped filter for practically relevant and non-random relationships.
- Top rules provide interpretable relationship patterns that can support operational planning.

## 3) Practical Relevance and Real-World Applications

The findings from this deliverable have direct practical value:

- **Clinical risk monitoring:** Classification outputs can flag records likely to have abnormal results for earlier review.
- **Resource planning:** Cluster segments can guide staffing, bed allocation, and service-level planning based on expected stay/cost profiles.
- **Care pathway design:** Association rules reveal recurring treatment-admission-outcome combinations that can inform protocol updates.
- **Inventory and pharmacy support:** Medication-related patterns can improve forecasting for high-frequency treatment combinations.
- **Decision support:** Combining supervised predictions, patient segmentation, and rule-based patterns provides a richer foundation for hospital analytics dashboards.

## 4) Challenges and How They Were Addressed

- **Mixed data types and preprocessing complexity:**
  - Challenge: Numeric and categorical variables required different handling across tasks.
  - Resolution: Used robust preprocessing pipelines (imputation, scaling, one-hot encoding) for reproducible model training.

- **Model performance trade-offs:**
  - Challenge: A single metric did not capture model quality adequately.
  - Resolution: Evaluated models with multiple metrics (Accuracy, F1, ROC-AUC) plus confusion matrices and ROC curves.

- **Hyperparameter sensitivity:**
  - Challenge: Default parameters did not guarantee strong minority-class behavior.
  - Resolution: Applied GridSearchCV to tune Decision Tree parameters with F1-oriented selection.

- **Choosing cluster count objectively:**
  - Challenge: Cluster count can be arbitrary without a quantitative criterion.
  - Resolution: Used silhouette scores across candidate values of `k` and selected the best-supported value.

- **Large volume of association rules:**
  - Challenge: Raw rule output can be noisy and hard to interpret.
  - Resolution: Filtered rules by support/confidence/lift thresholds and focused analysis on top-ranked rules.

## 5) Files for Deliverable 3

- `Deliverable3_Classification_Clustering_PatternMining.ipynb` - Complete Deliverable 3 implementation and visualizations.
- `healthcare_dataset_cleaned.csv` - Input data used for modeling and pattern mining.
- `README_Deliverable3.md` - This deliverable-specific summary.

## 6) Final Note

Deliverable 3 demonstrates a full multi-method analytics workflow: classification for prediction, clustering for segmentation, and association rules for interpretable pattern discovery. Together, these methods produce actionable insights that are more useful than any single technique in isolation.
