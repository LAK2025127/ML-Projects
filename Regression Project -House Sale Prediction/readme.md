# 🏠 House Sale Price Prediction

## 📌 Project Goal
This project helps a real estate firm accurately predict house sale prices. The goal is to guide optimal pricing decisions for listed properties by leveraging historical data and machine learning models.

---

## 📊 Dataset Details

- **Datasets:**
  - 1 explordatory data analysis dataset
  - 1 training dataset  
  - 1 validation dataset
- **Key cleaning steps:**  
  - Replaced `'Unknown'` in the `city` column with `'--'`
  - Filled missing values in `months_listed` with the mean (normal distribution)
  - Standardized spelling in `house_type`
  - Removed `'sq.m'` from `area` and converted to numeric (2 decimal places)
  - Converted `sale_date` to datetime format

---

## ⚙️ Methods & Tools Used

**Tools:**  
Python, NumPy, pandas, scikit-learn, matplotlib, seaborn

**Key Methods:**  
- Exploratory Data Analysis (EDA)
- Preprocessing pipeline (scaling, encoding)
- Linear Regression
- Decision Tree Regressor
- Hyperparameter Tuning (GridSearchCV)
- Feature Importance Analysis

---

## 📈 Performance Metrics

- **R-squared (R²):** Measures how well the model explains price variance
- **RMSE:** Shows the average difference between actual vs predicted sale prices
- **Average Cross-Validation Score:** Tests model performance on unseen data

## 💡 Key Insight

- **Most impactful features:** `area`
- Feature 'area' has **linear relation with target variable 'sale_price'** and stated by both Linear Regression and Decision Tree       Regressor as the most important features.
- Decision Tree Regressor was chosen as per the model comaprsion where on the RMSE it performed better than Linear Regression.


## Relation between feature 'area' and target variable 'sale_price'
![Correlation between area and sale_price](https://github.com/user-attachments/assets/bdf4e898-a68f-4323-879d-1446a2ca33e3)


## Model Comparison
![regression_model_comparisom](https://github.com/user-attachments/assets/97dce9bd-f479-4d38-81f7-7ada2f6dabec)

