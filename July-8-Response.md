## Response to July 8 Questions

A. We need to split the data into training and testing images because it is very helpful
to be able to first train the model on data and then test it on data that we already know
the answer to. If we collected testing data but did not know its classification, we would
have no way of telling how well the model actually works. In this case, since our testing
data has already been classified, we can compare its actual classification with the
output of the model and determine the model's accuracy. If we simply did this with 
training data, the model has already seen this data, so we could run into the issue of 
the model simply memorizing the classification of the training data and not actually being
able to classify.

B. The purpose of the relu function is to avoid skewing made by negative outputs. In 
order to do this, the function takes all negative outputs and sets them to zero. The softmax
function helps us find the most likely category that the input belongs to by setting the
highest chance value to 1 and the rest to 0. This makes it easier, since now we just have
to find the 1 and don't have to look for which value is the highest. There are 10 neurons
in this last layer since there are 10 categories, with each of the neurons corresponding to 
one of the categories (one of the pieces of clothing in this case).

C. Although each optimizer and loss function is different, they all have the same basic
use. Originally, the model does not know anything about the relationship between the features
and targets, so it makes a guess. The loss function evaluates bad the guess is, and using
this value, the optimizer makes the next guess. This repeats with each epoch trying to 
minimize the loss and increase the accuracy of the model. Each optimizer and loss function 
also has scenarios it works best for. In this case, for example, we have a categorical loss
function, since we are separating the data into clothing categories.

D. Using the mnist drawings dataset (the dataset with the hand written numbers with
corresponding labels) answer the following questions.
  1. What is the shape of the images training set (how many and the dimension of each)?
  2. What is the length of the labels training set?
  3. What is the shape of the images test set?
  4. Estimate a probability model and apply it to the test set in order to produce the 
  array of probabilities that a randomly selected image is each of the possible numeric 
  outcomes (look towards the end of the basic image classification exercises for how to 
  do this — you can apply the same method applied to the Fashion MNIST dataset but now 
  apply it to the hand written letters MNIST dataset).
  5. Use np.argmax() with your predictions object to return the numeral with the highest 
  probability from the test labels dataset.
  6. Produce the following plot for your randomly selected image from the test dataset
