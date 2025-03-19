# Student Performance Prediction Model Documentation
Generated on: 2025-03-19 16:51:27

## Overview
This document provides a detailed overview of the machine learning models developed to predict student final grades. 
Three different regression approaches were evaluated to determine the most effective prediction strategy.

## Data Preparation
The original dataset was processed and transformed before model training. The transformed data is stored at `data/transformed_data.csv`.

### Data Preprocessing Steps:
- Categorical features were encoded
- Boolean features were converted to numeric (0/1)
- Missing values were handled
- Feature scaling was applied where appropriate

### Feature Set:
Total features used: 50

## Modeling Approaches

### Model 1: Basic Linear Regression
* **Description**: Standard linear regression using all available features
* **Implementation**: `sklearn.linear_model.LinearRegression`
* **Training Set Size**: 400 samples
* **Feature Count**: 50 features

### Model 2: Linear Regression with Feature Selection
* **Description**: Linear regression using only the 20 most predictive features
* **Implementation**: `sklearn.feature_selection.SelectKBest` with `f_regression` for feature selection
* **Feature Selection Method**: F-test (ANOVA)
* **Selected Features**:
  1. previous_gpa
  2. attendance_rate
  3. participation_score
  4. assignment_completion
  5. study_hours_per_week
  6. previous_course_failures
  7. work_hours_per_week
  8. family_support_High
  9. family_support_Low
  10. program_of_study_Biology
  11. program_of_study_Chemistry
  12. program_of_study_Liberal Arts
  13. program_of_study_Mathematics
  14. study_participation_interaction
  15. gpa_attendance_interaction
  16. extracurricular_work_interaction
  17. engagement_score
  18. academic_risk
  19. is_high_gpa
  20. is_low_attendance

### Model 3: Ridge Regression
* **Description**: Linear regression with L2 regularization to prevent overfitting
* **Implementation**: `sklearn.linear_model.Ridge`
* **Regularization Strength (alpha)**: 1.0
* **Training Set Size**: 400 samples
* **Feature Count**: 50 features

## Model Evaluation

### Performance Metrics:

```
                              Model      MSE     RMSE       R2      MAE
            Basic Linear Regression 0.524769 0.724409 0.517161 0.537218
Feature Selection Linear Regression 0.517756 0.719553 0.523613 0.535156
                   Ridge Regression 0.525566 0.724959 0.516427 0.539079
```

### Best Performing Model: Feature Selection Linear Regression

### Performance Analysis:
* **Mean Squared Error (MSE)**: Measures the average squared difference between predicted and actual values. Lower values indicate better performance.
* **Root Mean Squared Error (RMSE)**: The square root of MSE, providing a metric in the same units as the target variable.
* **R-squared (R²)**: Indicates how well the model explains the variance in the target variable (0-1). Higher values indicate better performance.
* **Mean Absolute Error (MAE)**: Measures the average absolute difference between predicted and actual values. Lower values indicate better performance.

## Coefficient Analysis

### Top 10 Most Positive Influential Features:
```
                      Feature  Coefficient
                 previous_gpa     0.853528
              attendance_rate     0.372790
program_of_study_Liberal Arts     0.224992
 program_of_study_Engineering     0.215320
          family_support_High     0.215054
          participation_score     0.189965
         study_hours_per_week     0.177875
        family_support_Medium     0.084116
             completed_course     0.072718
     previous_course_failures     0.070388
```

### Top 10 Most Negative Influential Features:
```
                      Feature  Coefficient
first_generation_student_True    -0.068106
          work_hours_per_week    -0.132183
   program_of_study_Chemistry    -0.162835
 program_of_study_Mathematics    -0.197535
            is_low_attendance    -0.280894
           family_support_Low    -0.299170
                  is_high_gpa    -0.354468
        assignment_completion    -0.380108
                academic_risk    -0.532957
   gpa_attendance_interaction    -1.686268
```

## Conclusion
The models were evaluated based on their performance metrics, with R² being the primary criterion for model selection.
The model with the highest R² score demonstrates the best fit for predicting student final grades.

## Recommendations
1. Use the best performing model for final grade predictions
2. Consider feature engineering to further improve model performance
3. Evaluate model performance periodically with new data
4. Explore non-linear models if prediction accuracy needs further improvement

## Model Storage
All models and their evaluation results are stored in the 'models' directory for future reference and deployment.
