# 📌 Recipe Popularity Prediction

## 🎯 Project Goal

The product team wants to accurately identify and display recipes on the website’s homepage that are most likely to attract high traffic — targeting **80% accuracy** while minimizing the display of unpopular recipes.

---

## 📂 Dataset

- **Rows:** 947  
- **Columns:** 8  
  - **Numeric:** `recipe`, `calories`, `carbohydrate`, `sugar`, `protein`
  - **Categorical:** `category`, `servings`, `high_traffic`

The dataset provides recipe-level nutritional and category information along with a label indicating whether the recipe historically attracted high traffic.

---

## 🛠️ Methods & Tools

**Tools:**  
- Python, NumPy, pandas, scikit-learn, matplotlib, seaborn

**Methods:**  
- Exploratory Data Analysis (EDA)
- K-Nearest Neighbors
- Logistic Regression
- Decision Tree Classifier
- Voting Classifier
- Hyperparameter tuning with GridSearchCV
- Learning curve analysis
- Generalization error estimation

---

## 📈 Key Results & Insights

- **EDA Findings:**  
  - Ingredients like **potatoes**, **vegetables**, and **pork** are strong traffic drivers.  
  - Recipes serving **4** people indicate popularity among **family-oriented users**.
  - From Decision Tree Classifier, nutrition facts hold significant importance.
 
- ** Actionable Recommendation on Findngs:**
  - Craft recipes with ingredients **strong traffic drivers** ingredients
  - To target the **family-oriented users demographic**
  - ** To further dive down into how nutrition facts related and act with target variable***
  
- **Model Performance:**  
  | Model                  | Accuracy | Recall |
  |------------------------|----------|--------|
  | K-Nearest Neighbors    | 72.10%   | 0.88   |
  | Logistic Regression    | 75.26%   | 0.81   |
  | Decision Tree Classifier | 75.78% | 0.81   |
  | Voting Classifier      | 75.26%   | 0.81   |

- The **Decision Tree Classifier** showed that **nutrition information** (e.g., calories, protein) holds significant predictive power for recipe popularity.

---

## 📊 Visualizations

- EDA visuals on ingredient trends and servings distribution.
- Model comparison bar plots (accuracy & recall).
- Learning curves to check model stability and generalization.

---

## Model Comparison
![model_performance](https://github.com/user-attachments/assets/e11ee1ed-fc76-4b36-91cb-5862dd250eb4)


## 🗂️ Project Files
📁 notebook_LAK_ML_classification_popular_recipe.ipynb
📁 recipe_site_traffic_2212.csv
📄 README.md

