# Deliverable 2 README: Regression Modeling and Performance Evaluation

## 1. Dataset Summary

This deliverable uses the cleaned healthcare dataset from Deliverable 1.

- Records: 55,500
- Core attributes: 15 original fields, plus engineered features
- Data types: numeric, categorical, and date-derived fields
- Prediction target: `billing_amount`

The dataset is appropriate for regression because it contains both patient-level and admission-level predictors at a realistic scale for model training and validation.

## 2. Modeling Process

The modeling workflow in Deliverable 2 includes:

1. Loaded `healthcare_dataset_cleaned.csv`.
2. Applied feature engineering:

- `admission_year`, `admission_month`, `admission_dayofweek`
- `is_weekend_admission`
- `age_squared`

3. Prepared data with a preprocessing pipeline:

- Numeric features: median imputation + standard scaling
- Categorical features: most-frequent imputation + one-hot encoding

4. Split data into train and test sets.
5. Trained and compared three regression models:

- Linear Regression
- Ridge Regression
- Random Forest Regressor

6. Evaluated models using:

- R-squared (`R2`)
- Mean Squared Error (`MSE`)
- Root Mean Squared Error (`RMSE`)
- 5-fold cross-validation

## 3. Evaluation Results

Observed model comparison from the notebook workflow:

- Random Forest performed best overall.
- Linear Regression and Ridge Regression performed similarly and much weaker.

Representative metrics (from the current run):

- Random Forest: `Test R2 = 0.0827`, `Test RMSE = 13628.42`, `CV R2 Mean = 0.0921`
- Ridge Regression: `Test R2 = -0.0004`, `Test RMSE = 14232.92`, `CV R2 Mean = -0.0006`
- Linear Regression: `Test R2 = -0.0004`, `Test RMSE = 14232.92`, `CV R2 Mean = -0.0006`

## 4. Insights and Key Observations

- Nonlinear modeling helped: Random Forest captured patterns missed by linear models.
- Linear and Ridge results near zero `R2` indicate limited linear relationship between available predictors and billing amount.
- The strongest predictive signal is still modest, which suggests important cost drivers are missing from the available columns.
- Feature-importance analysis indicates variables such as `room_number`, `length_of_stay`, and admission-time calendar features contribute more than most categorical indicators.

## 5. Challenges and How They Were Addressed

- Environment compatibility issue (NumPy/PyArrow mismatch) initially interrupted runs.
  Resolution: reinstalled compatible package versions and reran the modeling steps.

- Seaborn FutureWarning for bar plots (`palette` without `hue`).
  Resolution: updated plotting code to use `hue` with `legend=False`.

- Low predictive performance in linear baselines.
  Resolution: added feature engineering and included a nonlinear model (Random Forest), which improved both holdout and cross-validated performance.

## 6. Deliverable 2 Files

- `Deliverable2_Regression_Modeling.ipynb` - regression modeling notebook
- `healthcare_dataset_cleaned.csv` - cleaned input data
- `README_Deliverable2.md` - this deliverable-specific summary
