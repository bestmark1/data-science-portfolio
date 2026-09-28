# Bank Customer Classification Project

This project is part of the Skill Factory Data Science course. The goal is to analyze bank marketing campaign data and build a classification model to predict whether a client will open a deposit.

## 📊 Project Overview
The data belongs to a real bank. The objective is to identify patterns and decisive factors that influence a client's decision to invest money. Successful prediction helps the bank increase revenue by targeting the right audience.

## 🛠️ Tech Stack
- **Python** (Pandas, NumPy)
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn
- **Hyperparameter Tuning:** GridSearchCV, Optuna

## 📉 Key Steps
1. **Data Preprocessing**:
   - Cleaned the `balance` feature (removed currency symbols and spaces).
   - Handled missing values in `job`, `education`, and `balance`.
   - Removed outliers using the **Tukey method** (IQR).
2. **Exploratory Data Analysis (EDA)**:
   - Analyzed target variable balance.
   - Identified correlations between social factors (age, job, education) and deposit opening.
   - Discovered that **call duration** and **previous success** are the strongest predictors.
3. **Feature Engineering**:
   - Encoded categorical variables using `LabelEncoder` and `One-Hot Encoding`.
   - Selected the top 15 features using `SelectKBest` (ANOVA F-value).
4. **Modeling & Evaluation**:
   - Trained Logistic Regression, Decision Trees, Random Forest, and Gradient Boosting.
   - Implemented a **Stacking Classifier** for better precision.
   - Optimized hyperparameters using **Optuna**.

## 🏆 Results
The best performance was achieved by the **Gradient Boosting** model:
- **Accuracy:** ~82-84%
- **F1-score:** ~0.82

## 📂 Project Structure
- `Project_4_ML.ipynb`: The main Jupyter Notebook with all calculations and visualizations.
- `bank_fin.csv`: The dataset used for the project.
- `README.md`: Project documentation.

## 📝 Conclusion
The analysis revealed that the bank should prioritize clients who have previously opened deposits and focus on call quality, as duration is a critical factor for conversion.
