# Stock-Data-Analysis
Analyzed and predicted stock prices from two datasets using both supervised and unsupervised Machine Learning techniques using PySpark

## Table of Contents  
- [XGBoost](#xgboost)      
<a name="xgboost"/>


- [Clustering Models](#clustering-models)      
<a name="clustering-models"/>

- [Summary](#summary)      
<a name="summary"/>

- [Possible techniques that can improve the accuracy](#possible-techniques-that-can-improve-the-accuracy)      
<a name="possible-techniques-that-can-improve-the-accuracy"/>


---------------------------------------------------------------------------------------------------------------



## XGBOOST

### SCOPE

- XGBoost was used as a classification model
- Avoids **overfitting** by its regularization parameters
- Can deal with missing values and NaN values

### Methodology

- Predicted the closing price for the next 14 days on the validation data during training.
- Made predictions on holdout testing data.

### Observations

- We used **Root Mean Squared Error (RMSE)** function to check for prediction errors. Our calculations showed an average RMSE of 30 for all the stocks with the maximum reaching 77 for an individual stock.
- Validation prediction results sometimes varied by a big margin as it produced a RMSE very different from what we got in the testing data. For instance, TITAN, a stock in the dataset, had a difference of **47** in RMSE.






### Interpretation 

- For good predictions, RMSE is usually in the range 0.2-0.5.
- RMSE was very high on training compared to testing which indicates that the model did not learn the training distribution well.
- A more complex model could reduce underfitting

## CLUSTERING MODELS

- Time series k-means with Dynamic Time Warping
- Why use DTW instead of Euclidean?
  - Euclidean doesn’t work well if the time series lengths are mismatched
DTW is uses the nearest neighbour in the comparison sequence at each inde


### Dataset Overview
<img width="443" alt="Screen Shot 2021-05-02 at 10 34 08 PM" src="https://user-images.githubusercontent.com/43936803/116825199-dca24c00-ab96-11eb-9554-4ad874f00417.png">

- Most stocks increase, some are stagnant, very few decrease = 3 clusters

### Number of Models 
- Two models: one with normalized data, one with standardized data

<img width="783" alt="Screen Shot 2021-05-02 at 10 33 38 PM" src="https://user-images.githubusercontent.com/43936803/116825135-977e1a00-ab96-11eb-8d9b-2e0a72879e80.png">

### Standardized Data and Normalized Data

<img width="855" alt="Screen Shot 2021-05-02 at 10 34 02 PM" src="https://user-images.githubusercontent.com/43936803/116825155-a49b0900-ab96-11eb-8d45-f670435e2414.png">

- *_Standardized model_*
  - **Cluster 0**: stocks are rising 
  - **Cluster 1**: stocks are stagnant
  - **Cluster 2**: stagnant at first, but late 2019 there is a spike(which is interesting since the pandemic starts somewhere around then).

This appears to be the more reliable model.

- *_Normalized model_*
**Cluster 0**: messy - may not have trained well. Can see some rising stocks, but also some that don’t, and some that are volatile
**Cluster 1**: rising stocks
**Cluster 2**: 1 decreasing stock

- The standardized model appears to be the more reliable model 



## SUMMARY
Lastly, we share the insights into our results to summarize. For the XGBoost model, predicting stock market data did not produce the best results. This Implies that the stock market data is difficult to predict.

- **XGBoost**
  - The model was definitely not the best for predicting stock market data. 
  Stock market data is difficult to predict.
- **K-Means Clustering**
  - Picking stocks for a portfolio that generally increases based on clusters may be more reliable than training a model that predicts the stock price.





## POSSIBLE TECHNIQUES THAT CAN IMPROVE THE ACCURACY
- Updating the classification model with PySpark would give a better overview of the performance of the model 
- **Hyperparameter Tuning** can improve the accuracy for the classification model 
- **Stacking models** with different models can be used to produce better and more accurate predictions
