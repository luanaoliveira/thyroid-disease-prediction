# Thyroid Disease Prediction

Final Data Science project developed for the EBAC course **Profissão: Cientista de Dados**.
The objective of this project is to build a Machine Learning model capable of supporting the diagnosis of thyroid-related conditions based on clinical, historical, and laboratory data.

## Project Context

This project simulates a real-world Data Science scenario in which a stakeholder from the medical field needs a predictive model to support the diagnosis of thyroid diseases.

The dataset contains patient information such as demographic data, medical history, medication usage, symptoms, and laboratory exam results. The main goal is to identify patterns in the data and build a classification model with strong predictive performance.

## Objective

The objective of this project is to develop a classification model capable of predicting the target variable `binaryClass`, supporting the analysis of thyroid-related diagnoses.

Since this is a healthcare-related problem, the model evaluation considers not only accuracy, but also precision, recall, F1-score and confusion matrix.

## Dataset

The dataset used in this project is:

```text
Base_M43_Pratique_Hypothyroid.csv
```

The dataset contains:

* 3,772 records
* Clinical and demographic variables
* Laboratory exam results
* Categorical and numerical features
* Target variable: `binaryClass`

## Project Steps

The project was developed following the main steps of a Data Science workflow:

1. Problem understanding
2. Data loading
3. Initial data analysis
4. Missing value treatment
5. Data type conversion
6. Exploratory Data Analysis
7. Data preprocessing
8. Train-test split
9. Model training
10. Model evaluation
11. Hyperparameter tuning
12. Final model interpretation
13. Stakeholder recommendations

## Data Preparation

During the data preparation stage, the following treatments were applied:

* Missing values represented by `"?"` were replaced with `NaN`
* The `TBG` column was removed because all its values were missing
* Numerical variables were converted from text to numeric format
* Missing numerical values were filled with the median
* Missing categorical values were filled with the mode
* An inconsistent age value above 120 years was treated as missing and replaced with the median
* Categorical variables were encoded using One-Hot Encoding

## Exploratory Data Analysis

The exploratory analysis showed that the target variable is highly imbalanced:

* Class `P`: approximately 92.28%
* Class `N`: approximately 7.71%

Because of this imbalance, the model evaluation focused on metrics that better represent performance across both classes, especially macro precision, macro recall and macro F1-score.

The analysis also showed that laboratory variables such as `TSH`, `FTI`, `TT4` and `T3` were relevant for the classification task.

## Models Evaluated

The following classification models were tested:

* Logistic Regression
* Decision Tree
* Random Forest
* Support Vector Machine
* Gradient Boosting

Models sensitive to feature scale, such as Logistic Regression and SVM, were trained using standardized data.

## Final Model

The selected final model was **Gradient Boosting**, after hyperparameter tuning with GridSearchCV.

Best hyperparameters:

```text
learning_rate = 0.05
max_depth = 4
n_estimators = 50
```

## Final Results

The final model achieved the following performance on the test set:

| Metric            | Result |
| ----------------- | -----: |
| Accuracy          | 99.60% |
| Macro Precision   | 98.23% |
| Macro Recall      | 98.99% |
| Macro F1-score    | 98.61% |
| Weighted F1-score | 99.60% |

The confusion matrix showed that the final model made only 3 errors on the test set, indicating strong predictive performance even with class imbalance.

## Feature Importance

The most important variable for the final model was `TSH`, followed by variables such as:

* `on thyroxine`
* `FTI`
* `TT4`
* `thyroid surgery`
* `T4U`
* `T3`

These results suggest that laboratory exams and clinical history related to thyroid function played an important role in the model predictions.

## Conclusion

The final model showed strong performance in predicting thyroid-related diagnoses. The Gradient Boosting model achieved high accuracy, recall and F1-score, even in a highly imbalanced dataset.

However, since this project is related to healthcare, the model should be used only as a decision-support tool and not as a substitute for medical evaluation. In a real-world scenario, additional validation with new clinical data would be necessary before practical use.

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

## Repository Structure

```text
thyroid-disease-prediction/
│
├── Base_M43_Pratique_Hypothyroid.csv
├── thyroid_disease_prediction_M43_final_project.ipynb
├── README.md
├── LICENSE
└── .gitignore
```

## Author

Developed by Luana Oliveira as part of the EBAC Data Science final project.
