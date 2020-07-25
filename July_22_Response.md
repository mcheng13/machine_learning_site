## Response for Wednesday, July 22
A. Boosted Trees  
1. A one-hot encoded column is a collection of binary vectors of all zeros except for a 1 that represents the class. This is needed to use categorical data that otherwise would not be able to be fed into the model directly. Each index in the vector represents a different classification. The source values in this case would be discrete data.  
2. A dense feature allows us to view all of the feature data for a particular data point. Instead of being multiple vectors, it is transformed into an array. In the example, we can see several informational points by looking at the array, such as age being 22, fare being 7.25, and sex being male. This is useful as it allows us to consolidate all of the information pertaining to a data point into one array, making it easier to work with as there are less items involved in the process.  
3.
### Predicted Probability Histograms
#### Logistic Regression
![88126237-1e7d7b00-cb9f-11ea-9c52-f72edd8d8b16](https://user-images.githubusercontent.com/67922851/88352973-cf178600-cd29-11ea-9341-a45cf7a261b2.png)
#### Boosted Tree Model
![Unknown-17](https://user-images.githubusercontent.com/67922851/88279973-f2ebb500-ccb2-11ea-9b4a-3def48b8432a.png)  
In these two histograms, we can see the frequencies of the probabilities the model gives passengers to live. In the first histogram, the frequencies are slightly more spread out, but we can see two prominent clusters and two smaller clusters in the second histogram. This could be because these clusters actually correpond to groups of passengers, such as children, first class men, first class women, second class men, and second class women. I say this because there are certain probabilities with higher frequencies, and because I know the different groups listed have different chances of living. Overall, however, the predictions are almost the same, with many instances of low chances of living mixed with a group of higher chances (0.5-1.0).
### Probability Density Functions
#### Logistic Regression
![Unknown-26](https://user-images.githubusercontent.com/67922851/88446272-998c9e80-cdf6-11ea-9178-f4d816ec7bdd.png)
#### Boosted Tree Model
![Unknown-25](https://user-images.githubusercontent.com/67922851/88446274-9b566200-cdf6-11ea-9852-e5ca4d1377e8.png)  
In the two probability density plots, we can see very similar results to the predicted probability histograms. Once again, both have quite high numbers for lower probabilities and the logistic regression is more uniform between 0.5 and 1.0 while the boosted tree model shows more definite clusters. There are four groups again here, just like with the first histogram.
### ROC Curves
#### Logistic Regression
![88126245-23422f00-cb9f-11ea-81c4-52fd7b7da4ea](https://user-images.githubusercontent.com/67922851/88352976-d179e000-cd29-11ea-9ea0-b229bb7c7c36.png)
#### Boosted Tree Model
![Unknown-18](https://user-images.githubusercontent.com/67922851/88279975-f4b57880-ccb2-11ea-9a74-6ab538dfe669.png)  
In these ROC curves, we can see that the boosted tree model has a better ratio of true positives to false positives. This can be seen around the 0.0 false positive rate where the first curve has a rate of 0.4 and the second curve has a rate of 0.6. The second curve also has a sharper curve than the first and is closer to reaching the top left corner. This means that the area under the second curve is greater, making boosted trees the better model in this case. This agrees with the predictive power of the models, as boosted trees has a higher accuracy of around 0.82 versus 0.75. 

B. Boosted Trees model understanding  
1. Interpret and discuss the two plots.  Which features appear to contribute the most to the predicted probability?
#### Predicted Probability Horizontal Bar Plot
![Unknown-19](https://user-images.githubusercontent.com/67922851/88280389-bbc9d380-ccb3-11ea-95a8-5ff2002e636e.png)  
Here we can see just how each feature contributes to the survival of this particular passenger. Using this information, we can also assume what other plots would be like for passengers with different information. We can see that sex, age, class, and deck are the most important, with embark town and fare also having some significance. It is evident that being male is detrimental to the survival of the passenger, and that being middle-aged, second class, and belonging to an unknown deck is not helping. Although having a higher fare seems to help some with the survival, this is not nearly enough to offset some of these other features. Embark town may not seem like it would contribute to the survival, but this could be somewhat significant as different locations may have different demographics, which could then contribute to other features such as class, fare, and even age. When looking at being alone or having spouses and siblings, it seems that they are not very important when determining the survival, but having others with you does appear to help slightly.
#### Violin Plot
![Unknown-20](https://user-images.githubusercontent.com/67922851/88280393-bcfb0080-ccb3-11ea-9798-21956c1763f2.png)  
In this plot, we can see the feature contributions for the particular individual being compared to the feature contributions of all the passengers. As stated before, sex is the most important for determining a passenger's survival, and that is evident in the two hotspots in the plot. One spot is located on the negative side (male) and the other is on the positive side (female). Moving on to age, although there isn't as huge of a distinction between two groups, we can see that there are many on the negative side representing the adults as well as a much smaller amount on the positive side representing children. It also seems like this is the case for having a known (positive) versus unknown (negative) deck. Moving on to class and fare, the majority of individuals had negative contributions for those features, likely being those who have low fares and are second class. There are small clusters with very positive contributions likely representing those with high fares and who are first class. In terms of embark town, being alone, and having spouses and/or siblings, there is very little contribution or variation in contribution.     
2. Here we can see the feature importance plots for fare and age. These are arguably the more importance features behind the sex of the passenger in terms of predicting passenger survival.  
#### Fare Feature Importance Plot
![Unknown-21](https://user-images.githubusercontent.com/67922851/88280883-aa34fb80-ccb4-11ea-8f77-4841011ffecb.png)  
As seen in this first plot, as the price of the fare goes up, so does its contribution to the outcome. This could be because those with especially high fares were given special treatment and had a higher chance of living. Those with more standard fares did not have this luxury.
#### Age Feature Importance Plot
![Unknown-22](https://user-images.githubusercontent.com/67922851/88280886-ab662880-ccb4-11ea-858d-6c53808acc4c.png)  
In this second plot, it seems like those with lower ages, especially babies and young children, had a higher chance of surviving. It is also interesting looking at the age range between 20 and 60, as there seem to be two groups forming, likely due to the sex of the passenger being so significant. There are also several outliers near the end where elderly passengers can have a very high chance of living, comparable to that of babies.  