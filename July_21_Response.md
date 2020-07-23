## Response for Tuesday, July 21
A. Premade estimators  
1. The labels from the Iris training set included Setosa, Versicolor, and Virginica. Once the data was imported, the labels or species names were removed from the data using .pop and assigned to train_y so that train included features and train_y contained targets. The same is true for the testing set.  
```python  
train_y = train.pop('Species')  
test_y = test.pop('Species')
```
2. Five estimators from tf.estimator (other than those used in this file) include Boosted Trees Classifier, Logging Tensor Hook, Multi Label Head, Profiler Hook, and Step Counter Hook. The base commands for these could look like:  
```python
classifier = tf.estimator.BoostedTreesClassifier()
classifier = tf.estimator.LoggingTensorHook()
classifier = tf.estimator.MultiLabelHead()
classifier = tf.estimator.ProfilerHook()
classifier = tf.estimator.StepCounterHook()
```
3. The input functions are useful as they can supply data to be used for training, evaluating, and predicting. They return features, which is a dictionary in which the keys are the names of the features and the values are the arrays containing the features' values. They also return label, which is the array containing the values of the label (class) for each example. Defining feature columns is important as they tell the model how to use the raw input data. The feature columns specified are how the model knows to sort the data.  
4. What classifier.train() does is it does the actual training for the model to prepare it for evaluation and prediction. It takes a specified input function, in this case lambda, as well as a set of training and validation data. Lastly, the amount of steps specified is how many steps the model will take during training. Here the classifier is DNN Classifier, and it was defined when we created an instance of the DNN Classifier called classifier. The nested function input_fn is what is being applied to the training and testing sets and it was defined higher up in the code (specifically def input_fn()).   
5. Here we can see that the DNN Classifier and DNN Linear Combined Classifier have comparable results, with the latter outperforming the former by a small margin. The Linear Classifier, however, is greatly outperforming the other two with an accuracy of 0.97 versus 0.70 and 0.73. It also has a much lower loss of about one eighth of the other two. In terms of performance, Linear Classifer did the best, then DNN Linear Combined Classifier, then DNN Classifier.

|Estimator|Test Accuracy|Test Loss|
|---------|:-------------:|:---------:|
|DNN Classifier|0.70|0.56|
|DNN Linear Combined Classifier|0.73|0.56|
|Linear Classifier|0.97|0.07|

B. Build a Linear Model   

1. Here we can see that the univariate age plot and the age histogram are very similar looking. This is because the univariate age plot in the pairplot displays the probability distribution of age, while the histogram displays the actual amount of passengers in each age group. By looking at these plots, we can determine that the most common age group on the Titanic was late twenties to early thirties, and that the majority of the passengers fell between the late teens and about forty.  
	
#### Pairplot
![Unknown-11](https://user-images.githubusercontent.com/67922851/88121541-06ecc500-cb94-11ea-8437-7af7bd666204.png)
#### Histogram
![Unknown-12](https://user-images.githubusercontent.com/67922851/88121594-3c91ae00-cb94-11ea-9039-82933d2c60d9.png)  

2. A categorical column allows us to represent strings in a dataset, such as categorizing as dog or cat. The way it does this is the data is represented as a one-hot vector, where dog could be 1 and cat could be 0. A dense feature can include any number, not just 0 or 1 and can work for both numerical columns and categorical columns.  

3. The feature columns input into the LinearClassifier() include sex, number of siblings and spouses, parch, class, deck, embark town, alone, age, and fare. Age and fare are numeric columns and the rest are categorical. The initial output had okay results with stats like an accuracy of 0.754, loss of 0.467, and average loss of 0.474. It appears that using the base feature columns was not good enough to produce the best results, so a cross featured column was added. This is important, as there could be a different correlation for different feature combinations that was not previously accounted for. In this model, the cross featured column was made for age and gender to attempt to find a relationship between age and gender and their effect on the label. The resulting output included an accuracy of 0.761, loss of 0.457, and average loss of 0.466. Although not by very much, these results are already better than the previous results by only including one cross featured column. Analyzing the predicted probabilities and ROC curves, we can see this visually.  

#### Predicted Probabilities
##### Without Cross Featured Column
![Unknown-13](https://user-images.githubusercontent.com/67922851/88126237-1e7d7b00-cb9f-11ea-9c52-f72edd8d8b16.png)
##### With Cross Featured Column
![Unknown-14](https://user-images.githubusercontent.com/67922851/88126241-20dfd500-cb9f-11ea-9f38-3a076835c49c.png)  

Here we can see that there is a higher frequency of probabilities near zero for both plots with the plots being skewed to the right. However, the frequencies of the probabilities around 0.5 are lower than those closer to one. This shows that there are almost two groups of passengers, those who are very likely to die, and those who have a decent chance of living. With the sex of the passenger being the most important feature in this dataset, it appears that the plots have displayed this fact, with the low living chance group being the males and the higher chance group being the females.  
#### ROC Curves
##### Without Cross Featured Column
![Unknown-15](https://user-images.githubusercontent.com/67922851/88126245-23422f00-cb9f-11ea-81c4-52fd7b7da4ea.png)
##### With Cross Featured Column
![Unknown-16](https://user-images.githubusercontent.com/67922851/88126246-24735c00-cb9f-11ea-9491-af4a5a20c9ee.png)  

In these graphs, although subtle, we can see higher true positive rates in the second graph, as seen in locations like the spike up to 0.6 for the true rate at around 0.1 for the false rate. For the first graph, this spike is slightly less being around 0.55 instead, further illustrating the effect of cross featured columns.
