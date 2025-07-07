# 🏠 House Sale Price Prediction

## 📌 Project Goal
This project helps a real estate firm accurately predict house sale prices. The goal is to guide optimal pricing decisions for listed properties by leveraging historical data and machine learning models.

---

## 📊 Dataset Details

- **Datasets:**  
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
