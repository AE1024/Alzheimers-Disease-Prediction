## 🧠 Alzheimer's Disease Prediction Project Summary

This project establishes a robust Machine Learning pipeline to predict Alzheimer's Disease (Diagnosis) using a dataset rich with patient clinical, demographic, and lifestyle features. The core objective was to demonstrate the potential of ML in supporting early medical diagnosis by achieving high, reliable classification scores.



## Methodology
* Data Preprocessing & Feature Engineering

* Data Cleaning: We successfully handled the initial data, removing non-predictive or redundant columns like PatientID and DoctorInCharge. No missing or duplicate values were found, ensuring a clean foundation.

* Domain Expertise: We applied medical domain knowledge to create several powerful engineered features. These include:

* PulsePressure: Calculated from systolic and diastolic blood pressure.

* LDL_HDL_Ratio: A critical marker for cardiovascular health.

* ChronicDiseaseCount & SymptomCount: Aggregates of relevant medical history and observed symptoms.

* Data Preparation: The Age column was grouped and encoded. Crucially, data leakage was prevented by fitting the MinMaxScaler only on the training data and then transforming both the training and test sets.


## Feature Selection (RFE)
* Efficiency and Focus: We used the Recursive Feature Elimination (RFE) method, guided by a Random Forest model, to select the top 12 most predictive features out of the original 39. This streamlined the model input, improving efficiency and interpretability.

* Selected Features: The final feature set includes key clinical scores like MMSE, Functional Assessment, and ADL, along with engineered ratios and symptom counts.

## Model Training & Evaluation
* Hyperparameter Tuning: Six different classification algorithms (including Decision Tree, Random Forest, XGBoost, and SVM) were trained using GridSearchCV with 5-fold cross-validation.

* Metric Focus: Given the medical context where avoiding false negatives (missing a true diagnosis) is vital, the F1 Score was prioritized as the primary evaluation metric.

## 📦 Required Packages
Key Libraries:
pandas and numpy (for data manipulation)

matplotlib and seaborn (for visualization)

sklearn (for splitting, scaling, RFE, model building, and metrics)

xgboost (for the high-performing XGBoost Classifier)