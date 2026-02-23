# What Drives the Price of a Car?

A CRISP-DM-based analysis of used car pricing drivers for a used car dealership client, using a Kaggle dataset of ~426K used cars.

---

## CRISP-DM Framework

This project follows the **CRISP-DM** (Cross-Industry Standard Process for Data Mining) framework:

| Phase | Description |
|-------|-------------|
| **Business Understanding** | Define the business goal and reframe it as a data problem |
| **Data Understanding** | Explore and assess data quality and relevance |
| **Data Preparation** | Clean, transform, and prepare data for modeling |
| **Modeling** | Build and tune regression models to predict price |
| **Evaluation** | Assess model quality and interpret drivers of price |
| **Deployment** | Report findings and recommendations to the client |

---

## 1. Business Requirement (Business Understanding)

**Business goal:** Identify what factors make a used car more or less expensive so the dealership can stock and price inventory effectively.

**Data problem definition:**  
We have a dataset of used cars with attributes (year, odometer, color, manufacturer, condition, transmission, model, cylinders, etc.) and **price**. The task is to build a **supervised regression model** that predicts **price** and to use the CRISP-DM process to:

1. Perform exploratory data analysis (EDA) to understand the data  
2. Apply feature engineering and preprocessing  
3. Fit multiple regression models (e.g., linear regression, Random Forest, regularized models)  
4. Evaluate and compare models to choose the best predictor  
5. Translate model outputs (e.g., coefficients/feature importance) into recommendations for pricing and inventory decisions  

---

## 2. Data Understanding

**Dataset:** ~426K used cars (subset of a larger Kaggle dataset), 18 columns.

**EDA approach:**

- **Structure:** Inspect shape, column names, and data types  
- **Missing values:** Count nulls per column and decide strategy (drop vs impute vs default)  
- **Numerical features (including target “price”):**  
  - Summary stats (mean, median, std, quartiles)  
  - Outlier detection and handling  
  - Correlation with price (e.g., correlation plots)  
- **Categorical features:**  
  - Unique value counts and distributions  
  - Relationship to price (e.g., mean price by category)  

**Notable insights (from the notebook):**

- **Condition:** Most cars “Excellent” or “Good”  
- **Fuel & transmission:** Mostly “Gas” and “Automatic”  
- **Cylinders:** Mostly 4, 6, or 8 (6 most common)  
- **Title status:** Mostly “Clean”  
- **Drive:** Mix of 4WD and FWD  
- **Type, size, color:** Many “Full size” sedans; black and white common  
- **Manufacturer & state:** Ford/Chevy common; California prominent  

---

## 3. Data Preparation

**Objectives:** Fix integrity issues, clean data, engineer features, and prepare a modeling-ready dataset (including scaling/encoding) for `sklearn`.

**Steps in the notebook:**

1. **Handle nulls**  
   - Drop low-value/high-null columns (e.g., `size`, `VIN`, `id`)  
   - High-null categoricals → fill with `"other"` (e.g., condition, cylinders, drive, paint_color, type)  
   - Low-null categoricals → fill with mode (e.g., manufacturer, model, fuel, title_status, transmission)  
   - Numerical (year, odometer) → fill with median  

2. **Handle outliers**  
   - Remove or cap extreme values (e.g., price, odometer) so the training set is representative  

3. **Feature engineering & encoding**  
   - **Categoricals:** One-hot (low cardinality), ordinal, frequency, and target encoding where appropriate  
   - **Numericals:** Scaling (e.g., StandardScaler); optional imputation (e.g., median) in a pipeline  
   - **Pipeline:** `ColumnTransformer` with sub-pipelines for numeric, ordinal, one-hot, target-, and frequency-encoded features  
   - **Split:** Train/test (and/or validation) split; fit transformers on training data only  

---

## 4. Modeling

**Target:** Continuous **price**.

**Models used:**

- Linear Regression  
- Lasso Regression (with cross-validated alpha, e.g., `LassoCV`)  
- Ridge Regression (with cross-validated alpha, e.g., `RidgeCV`)  
- Random Forest Regressor  
- Gradient Boosting Regressor  

**Practices:**

- Preprocessing and model in a `Pipeline` (e.g., `preprocessor` + regressor)  
- Hyperparameter tuning (e.g., alpha for Lasso/Ridge via 5-fold CV)  
- Cross-validation to compare and select models  

---

## 5. Evaluation

**Goals:** Decide which model is best, check alignment with the business objective, and extract interpretable insights on what drives used car prices.

**Findings (from the notebook):**

- **Best model:** Random Forest (e.g., best on chosen metrics).  
- **Feature importance (summary):**  
  - **Strong drivers:** Car age (year), mileage (odometer), then car type (e.g., sedan, SUV), fuel (e.g., diesel), and number of cylinders.  
  - **Weaker than expected:** Manufacturer vs. physical attributes; title status; some fuel types (e.g., EV, hybrid); transmission; geography; paint color.  

Evaluation is used to confirm that the model delivers actionable insights before deployment.

---

## 6. Deployment — Recommendations and Next Steps

**Deliverable:** A concise report for used car dealers on primary findings and how to use them to tune inventory and pricing.

**Recommendations (from the notebook):**

- **Model performance:** The current model predicts car prices within about **±$3,600** (e.g., MAE or similar metric).  
- **Strategy to maximize revenue/profits:**  
  - Prefer **newer** cars and **lower mileage**; they command higher prices.  
  - **Diesel** tends to outperform gas, electric, and hybrid in this dataset.  
  - **Type matters:** Pickups, SUVs, convertibles tend to fetch higher prices.  
  - **Drive:** FWD is a relatively better choice in the data.  
  - **Cylinders:** More cylinders associate with higher prices.  
  - **Lower impact:** Color and title status have relatively small influence; can be deprioritized in procurement.  

**Next steps:**

- **Operational use:** Integrate the chosen model (e.g., Random Forest) into a pricing tool or dashboard for lis
