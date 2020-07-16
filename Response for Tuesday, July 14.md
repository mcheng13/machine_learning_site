## Response for Tuesday, July 14
A.  
what are you functionally accomplishing as you apply the filter, why is the application of a convolving filter to an image useful for computer vision 

![filter1](https://user-images.githubusercontent.com/67922851/87632634-c4486a00-c707-11ea-9606-0d6379efcd63.png)

This filter seemed to emphasize the edge lines in the image. When you look at the image, although the lines may be faint, they are mostly even and cover the outline of every object in the image.

![filter2](https://user-images.githubusercontent.com/67922851/87632641-c6aac400-c707-11ea-9688-ab0b1ee79945.png)

In this image, all of the vertical lines become emphasized, as seen with the posts and the railing. Some diagonal lines are also emphasized, but horizontal lines are difficult to make out.

![filter3](https://user-images.githubusercontent.com/67922851/87632654-cca0a500-c707-11ea-90f9-deefbd1b3daa.png)

In this image, all of the horizontal lines are emphasized, and similar to the previous filter, the diagonal lines are also emphasized. The vertical lines, even including the large posts, are hard to make out.

What applying filters like these actually does is it processes the images into raw features to make it easier to find sets of filters to later be used for classification. This is very useful for computer vision as it allows for input images to have objects that aren't centered and that can face any direction. For example, before we had an issue where shoes could only face one direction or else they would be misidentified, but this acts as a solution to that problem.

B. 

![pooling](https://user-images.githubusercontent.com/67922851/87633122-ce1e9d00-c708-11ea-81b1-724ce785c5d2.png)

This pooling done on the horizontal filter was able to extract and emphasize the features while removing any unnecessary information. Looking at the code, for every 2x2 set of pixels, the pixels are sorted in descending order, and then are replaced by the pixel with the greatest value. Since four pixels are replaced by one, this makes the image four times smaller and makes each axis half the length it was previously. This is useful as it accelerates the learning process. Images have less information overall, but retain the information that is actually useful for classification.

C. Yes, I was able to improve the model using the Conv2D and MaxPooling layers. Without them, the training ran through all ten epochs without reaching 99.8%, but with them, the training stopped at the ninth epoch.  
*plot convolutions graphically, include them in response and describe them*  
By decreasing the amount of convolutions, accuracy decreases slightly, but it also does not take as long to run. On the contrary, with increasing the amount of convolutions, the accuracy is slightly increased, but is does take slightly longer for each epoch. However, by adding more convolutional layers, there are actually less epochs required before reaching the target accuracy, so an increase in time for reach epoch is offset by having less epochs.