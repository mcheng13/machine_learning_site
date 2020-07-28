## Image Prediction
### Image 1: 
![Figure_1](https://user-images.githubusercontent.com/67922851/88574638-9ff66280-d010-11ea-95b2-8687b4295329.png)  
Predicted: 14  
Actual: 0  

###Image 2: 
![Figure_2](https://user-images.githubusercontent.com/67922851/88574646-a1c02600-d010-11ea-9fe5-c320f9d41930.png)  
Predicted: 18  
Actual: 36  

###Image 3:
![Figure_3](https://user-images.githubusercontent.com/67922851/88574653-a4bb1680-d010-11ea-8273-880662cfdb4f.png)  
Predicted: 19  
Actual: 38  

Overall, the predicted population counts were not too accurate, but there may be some reasoning behind this. First, in image 1, there is actually a house centered in the image, so it would make sense for the model to predict a population. Maybe this amount is high for one house, but the actual amount ended up being 0, which does not seem correct. Second, some of the images that the model was trained on were actuall blank, but still had population data. This error may have skewed results, as the model associated blank space with a population count. This could mean that it adds noise to every image, since there is always a blank border at the top and the bottom. It was also interesting seeing that for image 2 and 3, the predicted amount was half of the actual amount. Although the model was not the best at predicting the actual values, it was able to determine which image had the highest population and which had the lowest. To improve on this, maybe the 0 population images as well as the blank images could be removed. This could cause better accuracy and lower error for the remaining images.