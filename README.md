# Healthcare Dataset Data Mining Project

## Dataset Summary

This project uses a healthcare dataset with 55,500 records and 15 attributes, including patient demographics, admission details, billing amount, medical condition, medication, and test results. The dataset is suitable for data mining because it contains both numeric and categorical variables, enough records for reliable analysis, and several features that can support future regression, classification, clustering, and association rule mining tasks.

## Key Insights

- The dataset is large enough to support meaningful modeling and exploratory analysis.
- Medical conditions are fairly evenly distributed across the major categories.
- Gender is nearly balanced, which reduces the risk of class imbalance in simple demographic comparisons.
- Billing amount varies widely, making it a useful candidate target variable for later regression work.
- Length of stay, created from admission and discharge dates, is an informative engineered feature for future analysis.
- After cleaning, the dataset is more consistent and better suited for downstream modeling.

## Data Cleaning and Exploration Steps

1. Loaded the CSV file into Pandas and inspected the dataset structure.
2. Standardized column names to make the dataset easier to work with.
3. Checked for missing values and verified that the dataset had no null entries.
4. Removed duplicate records to improve data quality.
5. Cleaned text fields by trimming whitespace and normalizing capitalization.
6. Converted admission and discharge dates to datetime format.
7. Engineered a new feature, `length_of_stay`, from the date columns.
8. Checked billing values for noise and treated negative amounts as anomalies.
9. Performed EDA using histograms, count plots, box plots, and a correlation heatmap.

## Challenges and How They Were Addressed

- **Duplicate rows:** The dataset contained duplicate records, so they were removed before analysis.
- **Inconsistent text formatting:** Some names and provider fields had mixed capitalization, so text normalization was applied.
- **Date handling:** Admission and discharge dates needed conversion to datetime values before feature engineering.
- **Noisy billing values:** Negative billing amounts were flagged as anomalies and replaced using the median of valid billing values.

## Files

- [Deliverable1_Healthcare_EDA.ipynb](Deliverable1_Healthcare_EDA.ipynb) - Main notebook for Deliverable 1.
- [healthcare_dataset.csv](healthcare_dataset.csv) - Raw dataset.
- [healthcare_dataset_cleaned.csv](healthcare_dataset_cleaned.csv) - Cleaned dataset exported from the notebook.

## Notes

The notebook includes detailed comments and visualizations that document the cleaning process and the exploratory findings. These results provide the foundation for later deliverables in the project.
