# Dataiku Data Science Challenge

### This analysis was done using Python and various libraries. The process and results are outlined below.

## Exploratory Analysis

To understand the data I would be working with, I decided to utilize the pandas-profiling module, which allows the user to simply output many summary statistics on every variable in a dataframe. The .html output is available in this repository in the 'Exploratory Analysis' folder. pandas-profiling provides a visual representation of the distribution of each feature as well as correlations between each feature. 

I noticed multiple variables that had high percentages of null values and skewed data. As I had limited domain knowledge on this survey, I decided to use a robust method for feature selection using machine learning as opposed to deciding to drop variables with no subject matter knowledge.

## Feature Selection

To eliminate features that were not needed, I ran an inital XGBoost model on all features (with one-hot-encoded variables for each nominal variable) and output the variable importance. I then used the top 20 variables from the variable importance and recursively removed features while monitoring the AUC. This showed me that above 9 features or so there were only small improvements in model performance. Once I had selected the top 9 features to train the final model, I then proceeded to train multiple machine learning models to decide on a final model.

## Training the Models

I decided to train two different models to test against the test dataset. The two classification models I chose were XGBoost and Logistic Regression for their performance and relative simplicity. Although both models performed similarly against the test dataset, the XGboost model performed slightly better on the AUC metric. This model was then used to evaluate the impact of the features used.

## Impact of Features and Insights

After visualizing the effect of each variable on the outcome, it's obvious that certain features have more impact than others. For example, age was one of the best predictors and shows a strong positive relationship with the outcome. another feature with a strong positive relationship, not surprisingly, is the number of weeks worked per year. Each of the 9 features are analyzed in the notebook and have an automatically generated color based on the feature's interaction with the most closely related variable.

## Final Thoughts

While I believe this analysis is a good start, I think that with more time a more comprehensive approach can be taken and perhaps increase performance. Let me know if you have any questions!
