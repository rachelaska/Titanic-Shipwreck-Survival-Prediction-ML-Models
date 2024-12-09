# **Model Card: Titanic Shipwreck Survival Prediction ML Models**
## **Basic Information**
- **Person or organization developing model**: Rachel Aska (rachel.aska@gwu.edu) & Himavarsha Yerrapothu (himavarsha.yerrapothu@gwu.edu).
- **Model Date**: December 6, 2024
- **Model Version**: 1.0
- **License**: MIT License
- **Model Implementation Code**: titanic-shipwreck-survival-predicting-models-with-ml.ipynb

---
## **Intended Use**
- **Intended Uses**: 
  - Predict survival probability of Titanic passengers based on demographic and ticketing data.
  - Practice machine learning concepts, such as data preprocessing, feature engineering, model training, evaluation, and optimization.
  - Provide hands-on experience with Python libraries like Pandas, NumPy, and Scikit-learn for building predictive models.
  - Perform statistical analysis of survival trends and correlations between demographic or socio-economic factors and survival rates.
- **Intended Users**:
  - Students, educators, and beginner data scientists.
- **Out-of-Scope Uses**:
  - Applications requiring high-stakes decision-making.
  - Use similar analyses to explore survival trends in other historical contexts and highlight socio-economic disparities.
  - Use the techniques to evaluate fairness in decision-making systems in healthcare, hiring, or education.
---


## **Training Data**
- **Source**: [Kaggle Titanic Dataset](https://www.kaggle.com/c/titanic/data)
- **Data Splits**:
  - **Training Set**: 80% (712 rows)
  - **Validation Set**: 20% (179 rows)
- **Preprocessing**:
  - Missing values in `Age` and `Fare` were imputed using the median.
  - `Embarked` was filled with the most frequent value.
  - `Sex` and `Embarked` were encoded numerically.
- **Data Dictionary**:

| Name            | Modeling Role | Measurement Level | Description                                        |
|-----------------|---------------|-------------------|-----------------------------------------------     |
| **PassengerId** | ID            | int               | Unique row identifier                              |
| **Survived**    | Target        | int (binary)      | Survival status (1 = Survived, 0 = Did not survive)|
| **Pclass**      | Input         | int (ordinal)     | Passenger class (1 = 1st, 2 = 2nd, 3 = 3rd)        |
| **Name**        | Unused        | string            | Passenger name                                     |
| **Sex**         | Input         | int (binary)      | Gender (0 = Male, 1 = Female)                      |
| **Age**         | Input         | float             | Passenger's age (missing values imputed)           |
| **SibSp**       | Input         | int               | Number of siblings/spouses aboard                  |
| **Parch**       | Input         | int               | Number of parents/children aboard                  |
| **Fare**        | Input         | float             | Ticket fare                                        |
| **Embarked**    | Input         | int               | Port of embarkation (0 = C, 1 = Q, 2 = S)          |

---

## **Test Data**
- **Source**: [Kaggle Titanic Test Dataset](https://www.kaggle.com/c/titanic/data)
- **Number of Rows in Test Data**: 418
- **Differences in Columns**: No `Survived` column in the test set.

---

## **Model Details**
- **Input Features**: `Pclass`, `Sex`, `Age`, `SibSp`, `Parch`, `Fare`, `Embarked`
- **Target Variable**: `Survived`
- **Type of Models**: 
  - Logistic Regression
  - Decision Tree Classifier
  - Random Forest Classifier
- **Software**: Python, scikit-learn
- **Version**: Python 3.10, scikit-learn 1.3.0
- **Random Forest Hyperparameters**:
  ```python
  RandomForestClassifier(
      n_estimators=100,
      max_depth=5,
      random_state=1
  )


## **Quantitative Analysis**

### **Performance Metrics**

| Model                  | Dataset       | Accuracy | Precision | Recall | F1-Score |
|------------------------|---------------|----------|-----------|--------|----------|
| **Logistic Regression**| Training      | 80.0%    | 81.2%     | 78.4%  | 79.8%    |
|                        | Validation    | 78.0%    | 79.3%     | 75.9%  | 77.6%    |
| **Decision Tree**      | Training      | 97.9%    | 98.1%     | 97.6%  | 97.8%    |
|                        | Validation    | 79.0%    | 80.3%     | 76.5%  | 78.3%    |
| **Random Forest**      | Training      | 97.9%    | 98.2%     | 97.6%  | 97.9%    |
|                        | Validation    | 81.0%    | 82.4%     | 79.6%  | 81.0%    |

## **Ethical Considerations**

- **Bias**: The model relies heavily on features like **gender (Sex)** and **passenger class (Pclass)**, reflecting historical biases in survival rates.
- **Missing Data**: Imputation of missing values (e.g., **Age**, **Cabin**) may introduce inaccuracies.
- **Data Privacy**: Using Titanic passenger data assumes the data is public or used ethically. Modern datasets must ensure compliance with privacy laws like GDPR.
- **Unbalanced Classes**: Unequal distribution of survivors and non-survivors could affect fairness in predictions.
- **Miuse of Predictions**: Misinterpreting predictions as deterministic rather than probabilistic could lead to harmful decision-making in contexts such as healthcare or disaster management
- **Interpretability**: ML models, especially ensemble methods like Random Forest, can be complex and challenging to interpret for non-technical stakeholders.

--

## **Conclusion**

### **Best Model: Random Forest Classifier**

The **Random Forest Classifier** is the best-performing model for the Titanic Survival Prediction project due to the following reasons:

1. **High Accuracy**: Achieved **97.9% training accuracy** and **81.0% validation accuracy**, demonstrating strong learning capability and good generalization.
2. **Balanced Performance**: Maintained a balance between **Precision** (82.4%) and **Recall** (79.6%), minimizing both false positives and false negatives.
3. **Robustness**: Performs well with both numerical and categorical features, even with missing or noisy data.
4. **Feature Insights**: Identified key features influencing survival predictions, such as:
   - **Pclass**: Passengers in first-class had significantly higher survival rates compared to those in lower classes.
   - **Sex**: Female passengers were more likely to survive than male passengers.
   - **Age**: Younger passengers, especially children, had better survival odds.
   - **SibSp**: Passengers with families onboard showed varying survival probabilities based on family size.
   - **Parch**: Passengers with families onboard showed varying survival probabilities based on family size.
   - **Fare**: Higher ticket fares correlated with increased survival rates, likely linked to class and economic status.
   - **Embarked**: Passengers boarding from certain ports exhibited different survival rates, possibly reflecting socio-economic or class-related differences.
     
---
