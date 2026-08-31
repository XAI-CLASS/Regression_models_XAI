# Regression_models_XAI
# Team Name: Regressor

## Contributors : Tim Force, Vinodhini Rajasekhar, Mauzam Shafi Bhat

## Dataset

The Telco Customer Churn dataset contains demographic information, account details (like contract and charges), and subscribed services for telecommunication customers.


## Assumption Checks

| Model | Key Assumptions Checked | Evidence | Concern |
|---|---|---|---|
| Linear regression |  |  |  |
| Logistic regression |Minimal multicollinearity among predictors  | Applied drop='first' in OneHotEncoder to avoid the dummy variable trap  | Low concern for categorical multicollinearity. Moderate concern for the assumption of linearity between continuous variables |
| GAM |  |  |  |

## Model Comparison

| Model | Performance Evidence | Interpretability Strength | Interpretability Weakness |
|---|---|---|---|
| Linear regression |  |  |  |
| Logistic regression | ROC-AUC: 84.22%, Accuracy: 80.70%, F1-Score: 0.607 (at threshold 0.5) | High Feature importance and direction are clearly visible through coefficients  | Assumes a linear relationship between features and log-odds. It cannot naturally capture complex, non-linear feature interactions without manual feature engineering. |
| GAM |  |  |  |

## Recommendation

Recommended model:

Why this model:

What the company can responsibly conclude:

What the company should not conclude yet:

One next analysis we would run:

