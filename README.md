# Fluid-mobility-prediction-using-logging-measurments-
In this study, we focused on predicting formation fluid mobility from well logging data, which included neutron porosity, density, resistivity, lithology (geological units), and effective porosity (PHIE). Mobility was initially measured using MDT (Modular Formation Dynamics Tester), but since these measurements are sparse and costly, we aimed to predict them across the wellbore using routinely collected log data.

For modeling, we employed XGBoost, a boosting algorithm capable of capturing complex, nonlinear relationships between input logs and mobility. The model’s hyperparameters were tuned using the TPE (Tree-structured Parzen Estimator) within a repeated cross-validation framework. This ensured the model’s performance was robust and generalizable, avoiding overfitting to specific wells or depth intervals.

Preprocessing included a log transformation of the mobility output. This was necessary because mobility values ranged from 2 to 229, and without log scaling, the model would underfit the small values while being dominated by the largest ones. The resistivity input was right-skewed, so it was also log-transformed to reduce skewness. Notably, extreme resistivity values were retained instead of removed, as they represent the true heterogeneity of the reservoir and are geologically meaningful.

Before using XGBoost, a polynomial regression model was tested, but it performed poorly, which was expected given the complex, nonlinear nature of the relationship between logging measurements and mobility.

Finally, the model’s R² and RMSE were calculated on the log scale, which provides a fair assessment of predictive accuracy across the entire mobility range. Evaluating on the log scale ensures that both small and large mobility values contribute appropriately to the error metrics, giving a more realistic picture of the model’s performance.
