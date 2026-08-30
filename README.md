# AI4I 2020 – ML Experiment Workflow




## 1. Problem Understanding ✅

- Problem: Predict whether a machine/process will fail or not.
- ML Type: Binary Classification.
- Target:
  - `0` → No Failure
  - `1` → Machine Failure

---

## 2. Dataset Understanding ✅

- Dataset contains 10,000 rows.
- `UDI` is just a unique identifier → Remove from ML features.
- `Product ID` contains:
  - `L`, `M`, `H` → Product type.
  - Remaining number → Serial number → Remove.
- `TWF`, `HDF`, `PWF`, `OSF`, `RNF` represent failure modes.
  - Do not use them as ML features because they cause data leakage.
- No missing values.
- No duplicate rows.
- Dataset is imbalanced:
  - `0` → 9661
  - `1` → 339

---

## 3. Data Cleaning

- Clean and standardize column names.
- Verify data types.
- Remove `UDI`.
- Extract `L`, `M`, `H` from `Product ID`.
- Remove the serial number.
- Remove/exclude `TWF`, `HDF`, `PWF`, `OSF`, `RNF` from ML features.
- Check invalid values and ranges.
- Recheck missing values and duplicates.

---

## 4. Exploratory Data Analysis (EDA)

### Univariate Analysis

- Analyze one feature at a time.
- Distribution of numerical features.
- Distribution of categorical features.
- Outlier analysis.

### Bivariate Analysis

- Feature vs Machine Failure.
- Relationships between two numerical features.
- Product Type vs Machine Failure.

### Multivariate Analysis

- Correlation analysis.
- Relationships between multiple features.
- Interaction between features and Machine Failure.

### Target Analysis

- Analyze failure vs non-failure.
- Identify patterns associated with failures.

---

## 5. Feature Engineering

- Extract Product Type from Product ID.
- Create meaningful features based on domain knowledge and EDA.

Possible features:

- Temperature Difference.
- Power-related feature.
- Tool Wear × Torque interaction.

Evaluate whether engineered features improve model performance.

---

## 6. Train / Test Split

- Split the dataset into training and test sets.
- Use Stratified Split because the dataset is imbalanced.
- Keep the test set untouched for final evaluation.

---

## 7. Handle Data Imbalance

Dataset:

- No Failure → 9661
- Failure → 339

Try and compare:

- Baseline without balancing.
- Class weights.
- SMOTE.
- Other sampling techniques if required.

Important:

- Apply sampling only to training data.
- Do not apply SMOTE before splitting.

---

## 8. Preprocessing

### Categorical Features

- Encode Product Type.

### Numerical Features

- Apply scaling where required.

Important:

- Fit preprocessing only on training data.
- Test data should only be transformed.

---

## 9. Model Building

Start with:

- Dummy Classifier.

Then experiment with approximately 6–7 models:

- Logistic Regression.
- Decision Tree.
- Random Forest.
- KNN.
- SVM.
- Gradient Boosting.
- XGBoost / LightGBM.

---

## 10. Cross-Validation

- Use Stratified Cross-Validation.
- Compare model performance across folds.

---

## 11. Hyperparameter Tuning

Select the best 2–3 models.

Use:

- GridSearchCV.
- RandomizedSearchCV.
- Other optimization methods if required.

Tune the selected models and compare results.

---

## 12. Model Evaluation

Evaluate using:

- Precision.
- Recall.
- F1 Score.
- ROC-AUC.
- PR-AUC.
- Confusion Matrix.

Do not rely only on Accuracy because the dataset is imbalanced.

---

## 13. MLflow Experiment Tracking

Track for every experiment:

### Parameters

- Model name.
- Hyperparameters.
- Feature set.
- Sampling strategy.

### Metrics

- Precision.
- Recall.
- F1 Score.
- ROC-AUC.
- PR-AUC.

### Artifacts

- Confusion Matrix.
- Classification Report.
- Feature Importance.
- Trained Model.

---

# Complete Workflow

Problem Understanding
↓
Dataset Understanding
↓
Data Cleaning
↓
EDA
↓
Feature Engineering
↓
Train/Test Split
↓
Handle Data Imbalance
↓
Preprocessing
↓
Model Building
↓
Cross-Validation
↓
Hyperparameter Tuning
↓
Model Evaluation
↓
MLflow Experiment Tracking
↓
Final Model Selection