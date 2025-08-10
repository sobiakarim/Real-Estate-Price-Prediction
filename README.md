# Real Estate Price Prediction – Portugal Listings

This project aims to predict **real estate prices in Portugal** using various regression models and machine learning techniques.  
The dataset used is `portugal_listinigs2.csv`, which contains details about properties such as location, size, number of rooms, and more.

---

## 📌 Project Workflow

### 1. **Data Cleaning & Preprocessing**
Before modeling, extensive preprocessing was performed to ensure the dataset was clean and ready for training:

- **Removed missing target values** (`Price`).
- **Outlier capping on target**: Clipped the `Price` column to the 1st–99th percentile to reduce the effect of extreme values.
- **Categorical columns type fix**: Ensured categorical columns were stored as strings.
- **Numeric missing value imputation**: Used mean imputation for missing numeric values.
- **Random imputation for year**: For missing `ConstructionYear`, assigned random years between 1960–2020.
- **Outlier capping in numeric features**: Applied IQR-based clipping to numeric columns like `TotalArea`, `LivingArea`, etc.
- **Categorical encoding**: Used a custom `TopCategoriesEncoder` to keep only the top 4 most frequent categories per column, grouping others into `"Other"`.
- **Scaling**: Applied `StandardScaler` to numerical features for uniform scaling.

---

### 2. **Modeling Approaches**
Several regression approaches were tested to compare performance:

#### **Gradient Descent**
- Implemented **Mini-Batch Gradient Descent** from scratch using NumPy.

#### **Linear Models**
- **Linear Regression** (no regularization)
- **Ridge Regression**
- **Lasso Regression**
- **ElasticNet Regression**

> These models, even with regularization, **struggled with low R² scores**, indicating they could not capture the non-linear patterns well.

#### **Tree-Based Models**
- **Random Forest Regressor**
- **Decision Tree Regressor**

> Tree-based methods performed **significantly better**.  
> Random Forest achieved **around R² ≈ 0.6**, which was the highest among all models.  
> This improvement was consistent across both training and test datasets, indicating reduced overfitting.

---

### 3. **Evaluation Metrics**
Each model was evaluated using:
- **MAE** (Mean Absolute Error)
- **MSE** (Mean Squared Error)
- **RMSE** (Root Mean Squared Error)
- **R² Score**
- **Adjusted R² Score**

---

## 📊 Key Observations
- **Linear models underperformed** — likely due to complex, non-linear relationships in real estate data.
- **Random Forest** provided the **best balance** between bias and variance.
- **Decision Tree** also performed well but was slightly worse than Random Forest.
- Checking performance on **test data** confirmed that the Random Forest model was **not overfitting**.

---

## ⚙️ Tech Stack
- **Python**
- **NumPy**, **Pandas**
- **Matplotlib**, **Seaborn**
- **scikit-learn**

---

## 🚀 How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/portugal-price-prediction.git
