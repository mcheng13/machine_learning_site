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
  1. 60000, 28, 28
  2. 60000
  3. 10000, 28, 28
  4.   
 ```python
  import tensorflow as tf
  import numpy as np

  class Callback(tf.keras.callbacks.Callback):
    def on_epoch_end(self,epoch,logs={}):
      if(logs.get('accuracy')>0.99):
        print('\nReached 99% accuracy so cancelling training!')
        self.model.stop_training = True

  mnist = tf.keras.datasets.mnist
  (x_train, y_train),(x_test, y_test) = mnist.load_data()
  x_train, x_test = x_train/255.0, x_test/255.0

  callbacks = Callback()

  model = tf.keras.models.Sequential([
  tf.keras.layers.Flatten(input_shape=(28,28)),
  tf.keras.layers.Dense(512,activation=tf.nn.relu),
  tf.keras.layers.Dense(10, activation=tf.nn.softmax)
  ])

  model.compile(optimizer='adam',
                loss='sparse_categorical_crossentropy',
                metrics=['accuracy'])
  model.fit(x_train,y_train,epochs=10,callbacks=[callbacks])

  probability_model = tf.keras.Sequential([model,
                                           tf.keras.layers.Softmax()])
  predictions = probability_model.predict(x_test)

  random_image = np.random.randint(0,len(x_test))
  print('Random Image Number:',random_image)
  print(predictions[random_image])
  ```
  5.   
  ```python
  print(np.argmax(predictions[random_image]))
  ```
  6.   
  ```python
  def plot_value_array(i, predictions_array, true_label):
    predictions_array, true_label = predictions_array, true_label[i]
    plt.grid(False)
    plt.xticks(range(10))
    plt.yticks([])
    thisplot = plt.bar(range(10), predictions_array, color="#777777")
    plt.ylim([0, 1])
    predicted_label = np.argmax(predictions_array)

    thisplot[predicted_label].set_color('red')
    thisplot[true_label].set_color('blue')

  numbers = ['0','1','2','3','4','5','6','7','8','9']

  plot_value_array(1, predictions[random_image], y_test)
  _ = plt.xticks(range(10), numbers, rotation=45)
  plt.show()
  ```
