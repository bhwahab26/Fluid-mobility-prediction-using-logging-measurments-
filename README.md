# Fluid-mobility-prediction-using-logging-measurments-
# 1. Data Description

The study focuses on predicting formation fluid mobility obtained from MDT measurements using routine well logging data. The dataset includes:

Neutron porosity – measures hydrogen content in rock, related to porosity.

Bulk density – gives information on rock matrix density.

Resistivity – indicates fluid saturation and pore connectivity.

Lithology / Geological Units – categorical information about the rock type or layer.

Effective porosity (PHIE) – fraction of interconnected pore space contributing to fluid flow.

Mobility measurements span a wide range (2 to 229), highlighting strong heterogeneity within the reservoir.

# 2. Preprocessing

Preprocessing was designed to improve model performance and account for data distribution:

Log transformation of output (mobility) – Mobility values were log-transformed to prevent underfitting small values and avoid dominance of high values in model training.

Input skewness adjustment – Resistivity values were right-skewed and log-transformed to normalize the distribution.

Outliers – Extreme resistivity values were retained instead of removed, as they represent actual geological heterogeneity.

Feature selection – Only relevant logging measurements (neutron, density, resistivity, PHIE, and lithology) were used as predictors.

# 3. Modeling Approach

Model selection – XGBoost, a gradient boosting algorithm, was chosen for its ability to model nonlinear and complex relationships between logs and mobility.
Initial testing – Polynomial regression was tested first but performed poorly due to the nonlinear relationships in the data.

Hyperparameter tuning – Tuning was performed using Tree-structured Parzen Estimator (TPE) within a repeated cross-validation framework to ensure generalizability across wells and depth intervals.

# 4. Model Performance Evaluation

Metrics – R² and RMSE were calculated on the log-transformed scale, which provides a more realistic measure of prediction accuracy across both small and large mobility values.

Results – The model effectively captures mobility variations across different lithologies and porosities, reproducing MDT measurements with high fidelity.
Insights – The predicted mobility profiles highlight reservoir heterogeneity, offering a spatially continuous view of flow properties along the wellbore.

# 5. Key Takeaways

Boosting algorithms can reliably predict MDT-derived mobility using routine logging measurements.
Preprocessing steps like log-transformations and skewness correction are crucial for wide-ranging mobility data.
