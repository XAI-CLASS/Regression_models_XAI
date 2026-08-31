# Regression_models_XAI
# Team Name: Regressor

## Contributors : Tim Force, Vinodhini Rajasekhar, Mauzam Shafi Bhat

## Dataset

The Telco Customer Churn dataset contains demographic information, account details (like contract and charges), and subscribed services for telecommunication customers.


## Assumption Checks

| Model | Key Assumptions Checked | Evidence | Concern |
|---|---|---|---|
| Linear regression | Linearity, constant variance, normality of residuals, multicollinearity, independence | Scatterplots of tenure and MonthlyCharges vs. Churn, residuals vs. predicted values, Q-Q plot, correlation matrix, and VIF | Several concerns: Churn is binary, residuals are not normally distributed, residual variance is not constant, and tenure/TotalCharges show relatively high VIF |
| Logistic regression |Minimal multicollinearity among predictors  | Applied drop='first' in OneHotEncoder to avoid the dummy variable trap  | Low concern for categorical multicollinearity. Moderate concern for the assumption of linearity between continuous variables |
| GAM |  |  |  |

## Model Comparison

| Model | Performance Evidence | Interpretability Strength | Interpretability Weakness |
|---|---|---|---|
| Linear regression | MSE = 0.1459, R² = 0.2522. The model explains about 25.2% of the variation in Churn. | Easy to understand. Coefficients show the direction and relative strength of each feature's association with predicted Churn. | Churn is binary (0/1), so linear regression is not ideal for probability prediction. Coefficients should not be interpreted as exact changes in true churn probability. |
| Logistic regression | ROC-AUC: 84.22%, Accuracy: 80.70%, F1-Score: 0.607 (at threshold 0.5) | High Feature importance and direction are clearly visible through coefficients  | Assumes a linear relationship between features and log-odds. It cannot naturally capture complex, non-linear feature interactions without manual feature engineering. |
| GAM |  |  |  |

## Recommendation

Recommended model:

Why this model:

What the company can responsibly conclude:

What the company should not conclude yet:

One next analysis we would run:

