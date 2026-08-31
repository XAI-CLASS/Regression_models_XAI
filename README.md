# Regression_models_XAI
# Team Name: Regressor

## Contributors : Tim Force(tmf48), Vinodhini Rajasekhar(vr156), Mauzam Shafi Bhat (mb948)

## Dataset

The Telco Customer Churn dataset contains information about 7,043 telecommunications customers and whether they left the company. The goal is to understand which customer characteristics are associated with churn, where Churn = 1 means the customer left and Churn = 0 means the customer stayed. The dataset includes demographic information such as gender, senior-citizen status, partner, and dependents, as well as service information such as internet service, phone service, technical support, and streaming services. It also contains account information such as tenure, contract type, payment method, monthly charges, and total charges. For this analysis, the data was cleaned by removing 11 records with missing TotalCharges, leaving 7,032 customers. The dataset is used to build and compare interpretable models that can help a telecom company understand and predict customer churn.


## Assumption Checks

| Model | Key Assumptions Checked | Evidence | Concern |
|---|---|---|---|
| Linear regression | Linearity, constant variance, normality of residuals, multicollinearity, independence | Scatterplots of tenure and MonthlyCharges vs. Churn, residuals vs. predicted values, Q-Q plot, correlation matrix, and VIF | Several concerns: Churn is binary, residuals are not normally distributed, residual variance is not constant, and tenure/TotalCharges show relatively high VIF |
| Logistic regression |Minimal multicollinearity among predictors  | Applied drop='first' in OneHotEncoder to avoid the dummy variable trap  | Low concern for categorical multicollinearity. Moderate concern for the assumption of linearity between continuous variables |
| GAM | Additivity (features act independently without unmodeled interactions), continuity/smoothness of numerical features, absence of severe multicollinearity among splines | KDE distribution plots by Churn for continuous features (`tenure`, `MonthlyCharges`, `TotalCharges`), and continuous feature correlation matrix | Strong evidence of non-linear relationships in `tenure` and `MonthlyCharges` supporting spline use. Moderate collinearity between `tenure` and `TotalCharges` ($r\approx 0.83$) tests the additivity assumption.|
 



## Model Comparison

| Model | Performance Evidence | Interpretability Strength | Interpretability Weakness |
|---|---|---|---|
| Linear regression | MSE = 0.1459, R² = 0.2522. The model explains about 25.2% of the variation in Churn. | Easy to understand. Coefficients show the direction and relative strength of each feature's association with predicted Churn. | Churn is binary (0/1), so linear regression is not ideal for probability prediction. Coefficients should not be interpreted as exact changes in true churn probability. |
| Logistic regression | ROC-AUC: 84.22%, Accuracy: 80.70%, F1-Score: 0.607 (at threshold 0.5) | High Feature importance and direction are clearly visible through coefficients  | Assumes a linear relationship between features and log-odds. It cannot naturally capture complex, non-linear feature interactions without manual feature engineering. |
| GAM | Accuracy: 80.98% (threshold 0.5), ROC-AUC: 86.16%, MSE = 0.1300, R² = 0.3320. The model explains about 33.2% of the variation in Churn. | High visual interpretability through Partial Dependence Plots (PDPs). Captures non-linear curves for continuous features (early tenure drop-off, price escalation) without losing individual feature transparency. | Standard GAMs assume strict additivity and miss multi-way categorical interactions (e.g., Month-to-Month $\times$ Fiber Optic)unless manually specified. Continuous LinearGAM outputs are not naturally bounded in [0, 1].|



## Recommendation

Recommended model: Generalized Additive Model (GAM)

Why this model:

It offers the best balance of performance and interpretability for this specific dataset. It outperformed Logistic Regression in distinguishing churners (ROC-AUC of 86.16% vs. 84.22%). More importantly, it successfully captures the real-world, non-linear relationships in the data (like the sharp drop-off in churn risk after the first few months of tenure) without forcing a strict straight line

What the company can responsibly conclude: 

We can confidently conclude that churn is heavily concentrated among new customers (low tenure). Customers with high monthly charges are also at a significantly elevated risk.  

What the company should not conclude yet: 

company should not conclude that reduced monthly charges would neccesarily reduce churn.

One next analysis we would run: 

Try and figure out how to include more inputs and may also use diffrent relevant models or trees.

