## Project 3 Writeup
### Setup
For this project, I started out with a sample size of 20 images to make sure everything went smoothly. I was able to upsize to a set of 2000 images and after that also went well, I decided to try the full 10000 images overnight. The model was saved and when I came back in the morning it seemed like the training was a success.  

In terms of training and testing, I split the 10000 images into 9000 training and 1000 testing images. To prepare for actually performing the training, I set the train labels and test labels equal to the first 9000 and last 1000 labels, respectively, then defined the model. Through my testing, I found that I got the best accuracy from using three Conv2D and three MaxPooling2D layers as well as two Dense layers. The last dense layer had only one neuron and had a linear activation, as I felt this would be best for determining the population. I used the RMSprop optimizer function with a learning rate of 0.001 as well as the mse loss function. For the metrics, I used mse and mae, although that caused loss and mse to have the same value, meaning I had duplicate numbers in some of my analysis. Although there was some variation in the mse and mae for each epoch, I decided that using 10 epochs would be optimal in terms of accuracy and time.
### Results
Although definitely not the best, my model performed decently overall. In the first graph below are all of the 1000 actual vs predicted points for population. The line of best fit is positive, which is a good result, but its slope is not one, which would be an indication of a good model. Instead it is about .52. It seems like the images where the population was zero as well as the pictures with very high populations made it difficult for the model to handle the data, causing the slope of the line of best fit to be so low.  
![figure5](https://user-images.githubusercontent.com/67922851/88491233-a08aec80-cf6f-11ea-89aa-56062d22eaf7.png)  
Here is a plot of only the 20 sample images to make viewing slightly easier. This way we can see that the majority of the points are actually labelled decently well with only a few outliers towards the low and high ends. In the previous plot, having so many data points made this harder to visualize.  
![figure2](https://user-images.githubusercontent.com/67922851/88491228-98cb4800-cf6f-11ea-9bae-3616d532d5c8.png)  
### Further Analysis
Below is a table of the results of training the data. We can see that the loss and mse are equivalent, as I had mse be the loss function. In future testing, I would alter this so that mae is the only metric or so that the loss function is different. Besides that, we can see that for the most part, both training and validation mse and mae decrease with each epoch, but with several exceptions. Originally, I had only three epochs, as the validation mse and mae appeared to go stagnant afterwards. With further testing, however, I found that increasing the epochs past about seven lead to more improved results. Although the validation mse is still very high at above 1000, I could not find a way to improve the results in a short amount of time.
  
|Metric|loss              |mse               |mae               |val_loss          |val_mse           |val_mae           |epoch|
|------|------------------|------------------|------------------|------------------|------------------|------------------|-----|
|0     |523.9864501953125 |523.9864501953125 |17.336877822875977|3533.88671875     |3533.88671875     |45.3958740234375  |1    |
|1     |498.2512512207031 |498.2512512207031 |16.847721099853516|2530.9287109375   |2530.9287109375   |38.457763671875   |2    |
|2     |482.28619384765625|482.28619384765625|16.42477035522461 |1541.272216796875 |1541.272216796875 |31.401973724365234|3    |
|3     |425.48736572265625|425.48736572265625|15.42639446258545 |1992.7490234375   |1992.7490234375   |36.24886703491211 |4    |
|4     |388.6453857421875 |388.6453857421875 |14.706588745117188|1996.5902099609375|1996.5902099609375|34.83063507080078 |5    |
|5     |373.5116271972656 |373.5116271972656 |14.228646278381348|1932.45654296875  |1932.45654296875  |35.72097396850586 |6    |
|6     |392.7917175292969 |392.7917175292969 |13.689448356628418|2016.4285888671875|2016.4285888671875|33.22691345214844 |7    |
|7     |296.2869567871094 |296.2869567871094 |12.641560554504395|1674.0047607421875|1674.0047607421875|30.684524536132812|8    |
|8     |268.0354309082031 |268.0354309082031 |11.95444393157959 |1616.0892333984375|1616.0892333984375|29.922853469848633|9    |
|9     |243.9693603515625 |243.9693603515625 |11.280399322509766|1236.1129150390625|1236.1129150390625|26.667203903198242|10   |  

Below is a histogram of the error for each data point. We can see that it looks somewhat like a bell curve centered near zero, a good sign, but it is skewed to the left. There also seems to be a slight dip in error close to zero as well as a large increase in errors between 10 and 15. Despite most of the errors being above -50 and below 25, some were off by more than (-)100.  
![error histogram](https://user-images.githubusercontent.com/67922851/88491239-af719f00-cf6f-11ea-99c9-28ce17a2b5a5.png)  
Here are graphs of training and validation loss and mae for each epoch. We can see why at first I thought 3 epochs would be sufficient, as there is a huge decrease in mae as well as loss from epoch 1 to 3. Afterwards, it seemed to be stagnant, but then decreased further until 10. Due to training taking about seven hours, I decided not to test anything higher than 10 epochs, as it would take too long. We can also see that, although validation loss and mae are decreasing, the model is very overfit.  
![loss](https://user-images.githubusercontent.com/67922851/88491251-bac4ca80-cf6f-11ea-9ebf-661bbecdd1bb.png)  
![mae](https://user-images.githubusercontent.com/67922851/88491253-bd272480-cf6f-11ea-849f-80155e12977f.png)  
### How could this be improved?
If I were to do this project again, or if this course were longer than five weeks so that we could have more time for this project, the first thing I would add would be using augmentation on the images to try to help with this major overfitting problem I have. This could make the training loss and mae worse, but the testing loss and mae should be improved. This would not be the solution to everything, however, as the values for the training data are still very high, so maybe I could try out different loss or optimizer functions, although the ones that I did try already were not as good as mse and RMSprop. Potentially something else I could do to try and solve the accuracy issue would be to drop some values that appear to be hurting accuracy, such as the images with no population. This seems to be throwing off the model, as it expects there to be a population in every image due to random noise. Doing this would prevent the model from underestimating other values and hopefully help with the accuracy. Lastly, although it might take much longer, I could try to increase the amount of epochs, as testing loss and mae appeared to be on a downtrend when I cut off the epochs at 10.