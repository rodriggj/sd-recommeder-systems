# Section 3 - Evaluating Recommender Systems

## Ojectives
- [ ] Test/Train Cross Validation
- [ ] Accuracy Metrics (RMSE, MAE)
- [ ] 

## Steps 

### Test / Train Cross Validation 

The way Recommender Systems get trained is by taking a meaning population set of data and splitting that data into groups. The _training_ data, and the _testing_ data. The training data is what the statistical models get built on by making meaningful correlations using statistical techniques. To validate that the statistical techniques are a meaningful predictor, you expose the statistics to the _testing_ data and see how well the predictions perform. This cycle is used as many times as needed to successfully "train" a predictor model. 

The process looks something like this: 

<p align="center">
<img width="350" src="https://user-images.githubusercontent.com/8760590/206578255-fb9a2a6f-de14-4f8e-b830-b32fe619acfa.png"/>
</p>

This process can get more elabore but has the same "tenants" of constructing a meaningful predictor model. For example a "repeating process" of segmenting the _training_ data and validating against the test data is to use the `k-fold` method. Here instead of segmenting the _training_ data once, you take many "folds" of segmenting the _training_ data to see if the folds are rendering meaningful and consistent predictor patterns. Again you take each fold and validate against the _testing_ data you've set aside, usually 20% of the total sample set. In this instance each fold is evaluated for accuracy and the models are tuned accordingly for prediction accuracy. 

<p align="center">
<img width="350" src="https://user-images.githubusercontent.com/8760590/206580120-a06c3490-e060-4f5c-9472-bbc4b3652e45.png"/>
</p>

This process help ensure that the model generation doesn't "overfit" our data set. 

------

So the approach of taking Testing and Training data to build a model can be prone to error. For one it only uses history to predict the future so any significant change to historical occurances would render the predictive accuracy of the model "risky". So this begs the question, how can you measure the success of the modeling? What tools/metrics would indicate whether the predictive error is within a particular tolerance or not? 

A common error measuring technique is `mean absolute error`. 

### Mean Absolute Error (MAE)

> mean absolute error: The sum of the absolute delta between the predicted rating ("y") vs. the known rating ("x"), divided the by number of observations to get the "mean". So the average of all the "absole error" within the model === mean absolute error. When assessing a "good" or "bad" MAE -- the lowest number is better. 

Example
| predicted rating (y) | actual rating (x) | absolute delta | 
| ---------------------| ------------------| ---------------|
| 5 | 3 | 2 |





## Reference


