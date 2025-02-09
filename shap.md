# Interpretability / Shap

# Introduction

Shap values are here to explain individuals models predictions. How each feature has contributed to the predictions and if features tend to increase or decrease the prediction made.

Feature importance does not do all this for a specific prediction.
Image1

We can also combine shape values from different predictions.
Image2.

Key benefits of Shap.
- Debugging and find which features causes the bug or anomalies.
- Human friendly explanations and increase trust in predictions.
- Data Exploration, and build better models with more appropriate features.



# Shap with Python

## Importing packages and prework

```python
import xgboost as xgb
import shap
shap.initjs(()

```


The example here is to predict the number of rings in avalons based on several features.
- Correlation matrix: We see that diameter and whole weight are highly correlated to a lot of the other variables so we drop those 2 variables.
- Sex is a categorical variable so we need to dummy it before using any ML model.

## Modeling

```python
# train
model = xgb.XGBRegressor(objective= 'reg:squarederror')
model.fit(X,y)


#Get predictions
y_pred = model.predict(X)

# Model Evaluation
plt.figure(figsize=())
plt.scatter(y,y_pred)
plt.plot([0,30],
  [0,30],
  color ='r'
  linestyle='-',
  linewidth =2)
plt.ylabel('Predicted')
plt.xlabel('Actual')
```

## Standard SHAP values

```python

# Get Shap values
explainer = shap.Explainer(model)
shap_values = explainer(X) # calculate the shap values for each observation values in the matrix X


np.shape(shap_values.values)
>>>(4100,8) # we have 8 features in the model so we have 8 shap values

```

Note: explainer(X) can be very time consumming. So instead of applying it to the whole X, we can apply it to a subset -> explainer(X[0:100])


## Waterfall plot

```python
# Waterfall plot for first observation
shap.plots.waterfall(shap_values[0])

shap.plots.waterfall(shap_values[0],max_display=4)
```
Image3


## Force Plot
You can see it as a condensed Waterfall plot.
Image4.

```python
shap.plots.force(shap_values[0])
```



**Waterfall and Force plots are useful to understand how the model has made individual predictions.**

## Stacked force plot
Combine multiple plots of multiple predictions.

```python
shap.plots.force(shap_values[0:100])
image5
```
Quickly explore some of the relationships capted by the model.

This is an **Interactive graph**

## Absolute Mean SHAP
To understand which features are important.
It is calculating the **absolute mean of all shap values for all observations**. So we can see which features has huge/significant contributions to the model prediction.
Image6

```python
shap.plots.bar(shap_values)
```

## Beeswarm plot

**THIS IS THE MOST USEFUL PLOT IN SHAP!!!**

```python
shap.plots.beeswars(shap_values)
```
image7


## Dependance Plots

```python
shap.plots.scatter(shap_values[:,"shell_weight"])

shap.plots.scatter(shap_values[:,"shell_weight"],
  color = shap_values[:, "shucked weight"])

shap.plots.scatter(shap_values(:,'shucked weight'])

```
Image 8-9





# Shapley Values for machine learning

TreeSHAP for decision trees or Random forest.

# Limitations of SHAP

SHAP is influenced by features correlations.
KERNSHAP assumed that features are independant. 

CANNOT be used for causal analysis.
**SHAP  is not a measure of how important a given feature is in the real world. it is simply how important a feature is to the model.**


# SHAP violin and heatmap


