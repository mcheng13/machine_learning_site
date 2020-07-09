## Responses to the July 9 Questions
1. What is TF Hub?  How did you use it when creating your script for “text classification
of movie reviews”?
TF Hub is _. When creating the text classification script, I _
2. What are the optimizer and loss functions?  How good was your “text classification of 
movie reviews” model? 
The loss function determines how bad a prediction is, and then outputs a certain loss value.
The optimizer then uses this value to try to make a better guess, which the loss function
then evaluates again. This repeats for every epoch. In this case, the optimizer was _ and
the loss function was _. The model ended up being decent, with an accuracy of _
3. In “text classification with preprocessed text” you produced a graph of training and 
validation loss.  Add the graph to this response and provide a brief explanation.

In this graph, we can see that the original loss is very high and decreases every epoch.
Loss is the 'inaccuracy' of the prediction, so minimizing loss increases the accuracy of 
the model. 
4. Likewise do the same for the training and validation accuracy graph

On the other hand, validation accuracy begins very low, as the initial guess is blind.
As the optimizer makes better and better guesses, the decrease in loss correlates with
an increase in validation accuracy. After a while, the validation accuracy actually starts
to decrease, as the model is getting overfit. This is because the model starts trying to 
find patterns in the training data that do no actually exist, so it will end up performing
better with training data, but worse with the testing data.
