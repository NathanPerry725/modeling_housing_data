# Problem Statement
My goal is to make reccomendations to clients about the factors that effect the sale price of homes. Knowing the effect of features can help clients make decisions to increase the value of thier home, and allow them to consider if they value certain features more or less than the market. I also have an optimistic goal of creating a model that will be able to predict future home prices.

# Data Dictionary

|Feature|Type|Description|
|---|---|---|
|saleprice|float|The price that each home was sold at. This was the variable I was trying to predict|
|tot_bath|float|The total number of baths in the home (full baths = 1, half-baths = .5)|
|overall_qual|int|A ranking from 1-10 of the overall quality of the house|
|kitchen_qual|int|A ranking from 0-4 of the quality of the kitchen|
|garage_area|float|The area of the garage in square feet|
|lot_area|float|The area of the lot in square feet|
|year_built|int|The year that the home was built|
|gr_liv_area|float|The above ground area of the home in square feet|
|total_bsmt_sf|float|The area of the basement in square feet|
|year_remod/add|int|The year that the home was most recently worked on. If no work was done then the year it was built|
|fireplaces|int|The number of fireplaces in the home|
|heating_qc|int|A ranking from 0-4 of the heating system in the home|
|yr_mnth_sold|float|The year the home was sold plus the month the house was sold divided by 12|

# Summary

The first thing I did was clean the data. This included removing outliers from the saleprice column. I also fillied nulls by using the provided data dictionary. If the data dictionary did not have information on the nulls, I imputed the mean. I also converted many of the features that were rankings into integers so that they could be used as numeric variables in the model. I then made columns for total basement square footage, the year and month of the sale, and total bathrooms. I used a polynomial transformation for the data to look for interaction factors and then standardized the data. I first did a normal regression of this data and found that the model was overfit. After this I used a ridge regression and Lasso regression on the data which created less overfit models. Finally I used Lasso regression to determine what columns from my poly transform should stay. After getting these columns, I performed a linear regression on them. This gave me my final model. Because of the poly transform, it was difficult to grasp the effect of changes in individual features. I averaged the change in predicted value across 4 standard deviations to better interpret the effect of individual features. After noticing time of sale had a negative effect, I plotted its effect on the predicted value and saw that the plot was an upside down parabola with a peak in 2008. I attribute this to the 2008 housing crash

# Conclusions

Because the model was so influenced by the 2008 housing crash, this model will not be effective in predicting future values. The model does do an effective job at predicting values in the time frame it was fit on. The features that had the strongest effect on the price were overall quality, lot area, above ground square footage and basement square footage.