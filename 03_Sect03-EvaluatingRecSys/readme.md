# Section 3 - Evaluating Recommender Systems

## Ojectives
- [ ] Test/Train Cross Validation
- [ ] Accuracy Metrics (RMSE, MAE)
- [ ] RMSE doesn't help Recommender Systems

## Steps 

### Test / Train Cross Validation (`accuracy measures`)

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

#### Mean Absolute Error (MAE)

> mean absolute error: The sum of the absolute delta between the predicted rating ("y") vs. the known rating ("x"), divided the by number of observations to get the "mean". So the average of all the "absole error" within the model === mean absolute error. When assessing a "good" or "bad" MAE -- the lowest number is better. 

Example
| predicted rating (y) | actual rating (x) | absolute delta | 
| ---------------------| ------------------| ---------------|
| 5 | 3 | 2 |
| 4 | 1 | 3 | 
| 5 | 4 | 1 | 
| 1 | 1 | 0 |

MAE = (2 + 3 + 1 + 0) / 4 = 1.5

#### Root Mean Square Error (RMSE)

> root mean square error (rmse): the benefit of this accuracy predictor is that it penalizes you more when you are way off and way less when you are reasonably close. The construct is similar, it is the sum of the differences between the predicted rating and the actual rating. It nets out to be a positive number b/c the results are squared, but it penalizes you less the more accurate you are. 

| predicted rating (y) | actual rating (x) | error^2 | 
| ---------------------| ------------------| ---------------|
| 5 | 3 | 4 |
| 4 | 1 | 9 | 
| 5 | 4 | 1 | 
| 1 | 1 | 0 |

RMSE = sqrt(4 + 9 + 1 + 0)/4 = 1.87

Realize that Accuracy Predidictions in the case of Recommendation Systems have limited value. No one cares the prediction accuracy of a recommendation ... they care that the prediction (aka recommendation) is something that may be correlated to thier previous purchasing / browsing / interests are. So it is important to understand accuracy metrics but more important to evalute success of the models based on "recommends" vs. "fitting" of a predictive curve. 

### Top-N (`Hit Rate` not accuracy)

When evaluation Top-N type metrics that may be more applicable for a recommender system vs. RMSE scores, you will priortize other metrics. For example, `Hit rate ` is a ration between number of "hits" or visits to a particular recommendation as compared to number of users: (e.g. "hits" / "users" = "hit rate"). 

Measuring Hit Rate is a little tricky. You can't really use the metrics used for measuring `accuracy` -- in fact it wouldn't make any sense to do so. Measuring the 'accuracy' of the top 10 recommends that the model produced would simply be measuring the relevance of the top 10 list it produced ... you would have to score 100%. So you need to use other methods...

#### `leave-one-out cross validation` 

In this technique, we leave out one of the recommends that the Training data produces as a recommendation. We then run the model against the test data and validate whether / or how many times this ommitted recommend is "re-recommended". 

The downside of this approach is you need a relatively large data set to test against or you may get skewed results and false positives on your validation efforts. 

#### `average reciprocal hit rate` 

Another variation of the `leave-one-out x-validation` is called the `average reciprocal hit rate (arhr)`. This is taking the position of the recommendation and scoring higher for instances where the highest rated recommends are predicted correctly. An example would look like this: 

| predicted rank | repricol rank | 
| ---------------| --------------| 
| 1 | 1 | 
| 2 | 1/2 | 
| 3 | 1/3 | 

arhr = (1 + 1/2 + 1/3) / 3 = 2.16 / 3 = 0.72

#### Cumulative Hit Rate (cHR)

| hit rank | predicted (or actual) rating | 
| ---------------| --------------| 
| 4 | 5.0 | 
| 2 | 3.0 | 
| 1 | 5.0 | 
| 10 | 2.0 | 

So here we can see that the number one hit rank is getting 5.0 stars, but the second is getting 3, while the 4th is getting 5, and the 10th hit rank is 2 stars. So the cumulative hit rank may or may not being properly modeled.

#### rating Hit Rate (rHR)

### Coverage, Diversity, & Novelty

> Coverage: % of <user, item> pairs that can be predicted.

## Reference
- [ ] Netflix RMSE Prize - Bellkor [here](https://www.scinapse.io/papers/54392637)