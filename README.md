

# Binary Classification Project

## Overview

The goal is a binary classification task to predict which customers will perform a specific future transaction, using structured financial data that mirrors Santander's real-world records. The dataset includes training and test sets with anonymized features, and model performance is evaluated using the ROC-AUC metric.

The dataset contains around **200,000 observations** and approximately **200 numerical features**.

One of the main challenges of this project is **class imbalance**.

Due to the class imbalance, Accuracy alone is not considered a reliable evaluation metric.

Data Source : https://www.kaggle.com/c/santander-customer-transaction-prediction

---
````
## Project Workflow

Raw Data
   ↓
Exploratory Data Analysis (EDA)
   ↓
Outlier Analysis
   ↓
Class Imbalance Analysis
   ↓
Feature Relationship Analysis
   ↓
Variance Filtering
   ↓
Correlation Filtering
   ↓
Baseline Model
   ↓
Feature Importance
   ↓
Feature Selection
   ↓
Model Comparison
   ↓
Hyperparameter Tuning
   ↓
Final Model
````

---

# 1. Exploratory Data Analysis

Before training the models, the dataset was explored to understand its structure, distributions, class balance, and feature relationships.

### Target Analysis

The target variable is imbalanced:

* Class 0: approximately 89.95%
* Class 1: approximately 10.05%
Therefore, metrics such as **F1 Score, Recall, and PR-AUC** are more informative than Accuracy alone.

### Outlier Analysis

Outliers were investigated using the **IQR method** & **z-score methode**



Since the proportion of outliers was relatively small, they were not automatically removed.

---

# 2. Feature Relationship Analysis

Several methods were used to investigate relationships between features and the target:

* Correlation Analysis
* Mutual Information
* KDE Plots
* Boxplots

### Mutual Information

Mutual Information was used to investigate potential dependencies between features and the target, including possible nonlinear relationships.

In this project, MI was mainly used as an **exploratory analysis tool**, while final feature selection was based on model performance.

---

# 3. Feature Reduction

### Variance Filtering

Variance filtering was used to identify features with very low variance.

Only 10 number of features were removed using this method.

### Correlation Filtering

Correlation analysis was performed to identify highly correlated features.

No significant feature reduction was obtained from this step.

---

# 4. Baseline Model

**Logistic Regression** was selected as the baseline model.

Because of the class imbalance, balanced class weights were used


### Baseline Results
Accuracy : 0.7834
Precision: 0.2865
Recall   : 0.7754
F1 Score : 0.4184
ROC-AUC  : 0.8599
PR-AUC   : 0.5004

The baseline model achieved a relatively strong Recall for the positive class and a ROC-AUC of 0.86.

However, the low Precision indicates a relatively high number of false positive predictions.

---

# 5. Feature Importance

Tree-based models were used to estimate feature importance:

* Random Forest
* XGBoost

Each model ranked the features according to its estimated importance.

Different numbers of top-ranked features were then evaluated:
 150 , 100

For each configuration, the selected features were used to retrain the corresponding model and evaluate its performance on the validation set.

In the feature selection stage, XGBoost with 150 features achieved the best overall performance.
Therefore, XGBoost with 150 features was selected as the best candidate for the Hyperparameter Tuning stage.

---

# 6. Machine Learning Models

### Logistic Regression

Used as the baseline model.

### Random Forest

Used for classification and feature importance analysis.

### XGBoost

Used for classification and feature importance analysis.


---

# 7. Evaluation Metrics

Because the dataset is imbalanced, multiple evaluation metrics are considered.

### Accuracy

Measures the overall percentage of correct predictions.

### Precision

Measures how many predicted positive samples are actually positive.

### Recall

Measures how many actual positive samples are correctly identified.

### F1 Score

Provides a balance between Precision and Recall.

### ROC-AUC

Measures the model's ability to distinguish between the two classes across different decision thresholds.

### PR-AUC

Provides a useful evaluation of positive-class performance, particularly for imbalanced datasets.

The main metrics considered in this project are:

**F1 Score, Recall, and PR-AUC.**

---

# 8. Model Selection

The models are compared using different feature-selection strategies and different numbers of selected features.

The best configuration will be selected based on validation performance.

The selected model will then be used for hyperparameter tuning.

---

# 9. Future Work

The remaining steps of the project are:

1. Select the best model and number of features.
2. Hyperparameter Tuning
3. Retrain the model using the best parameters.
4. Evaluate the final model.
5. Analyze feature importance.
6. Perform error analysis.
7. Compare the final model against the baseline.

---

# Technologies

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* Matplotlib
* Seaborn
* Jupyter Notebook



# Conclusion

This project demonstrates an end-to-end workflow for solving a binary classification problem with an imbalanced target and a relatively high number of numerical features.

The workflow includes:

* Exploratory Data Analysis
* Outlier Analysis
* Class Imbalance Analysis
* Baseline Modeling
* Feature Relationship Analysis
* Feature Reduction
* Feature Importance
* Feature Selection
* Model Comparison
* Hyperparameter Tuning

The final model will be selected based on validation performance, with particular emphasis on metrics suitable for imbalanced classification problems.

