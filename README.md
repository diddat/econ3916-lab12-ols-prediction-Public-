# OLS as a Line of Best Fit: Estimation versus Prediction

## Objective
The objective of this lab was to understand how Ordinary Least Squares (OLS) regression can be used for both estimating relationships between variables and predicting outcomes, while learning how to evaluate model performance.

## Methodology
- I used the California Housing dataset, containing 20,640 districts, to examine the relationship between median household income and median house value.
- I fitted the same OLS regression three ways: using the closed-form equation, statsmodels, and scikit-learn. I compared their intercepts and slopes to confirm they matched.
- I added up to 100 columns of random noise to the regression to observe how R-squared and adjusted R-squared changed.
- I split the dataset into training and testing sets before fitting an eight-feature regression model and compared its performance on both sets using RMSE.
- I used a regression with median income and average rooms to estimate a coefficient and its 95% confidence interval, then evaluated the model's prediction accuracy using test RMSE.
- I wrote a function called `holdout_rmse()` to calculate test RMSE for different predictors and used it to evaluate median income alone.

## Key Findings

**1. OLS Regression Results**

All three methods produced the same results:
- Intercept: 0.450856
- Slope: 0.417938

This showed me that the three methods produce the same line of best fit.

**2. R-Squared and Random Noise**

- R-squared with no noise: 0.4734
- R-squared with 100 noise columns: 0.4758
- Adjusted R-squared with no noise: 0.4734
- Adjusted R-squared with 100 noise columns: 0.4732

I found that adding random predictors increased R-squared even though those predictors contained no useful information. Adjusted R-squared eventually decreased because it accounts for the number of predictors.

**3. Training vs. Testing Performance**

For the eight-feature regression model:
- Training RMSE: 0.7197
- Test RMSE: 0.7456

The test RMSE was slightly higher than the training RMSE, showing that the model performed somewhat better on the data it was trained on than on unseen data.

**4. Estimation vs. Prediction**

Using median income and average rooms:
- AveRooms coefficient: -0.0381
- 95% confidence interval: [-0.0430, -0.0333]
- Test RMSE: 0.8379

This helped me understand that regression can be used for two different purposes: estimating the relationship between variables and predicting outcomes on new data.

**5. Median Income as a Single Predictor**

- Test RMSE using median income alone: 0.8421
- Test RMSE using all eight features: 0.7456

The model using all eight features had a lower test RMSE than the model using only median income. This showed me that including additional relevant predictors can improve prediction accuracy.

## Conclusion

This lab helped me understand the difference between using regression for estimation and prediction. I learned that a higher R-squared does not always mean a better model, especially when unnecessary predictors are added. I also learned why testing a model on unseen data is important for evaluating its predictive performance. Overall, the lab showed me how the same regression methods can answer different questions depending on what I am trying to measure.
