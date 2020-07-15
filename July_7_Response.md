## Response to questions on Tuesday, July 7:

1. According to Maroney, the difference between traditional programming and machine learning is that 
traditional programming involves inputting rules and data for the computer to produce the answers as the 
output, but machine learning takes data and answers as the input and the computer tries to determine the 
rules based on the data and answers. *This is significant, as computers are able to analyze thousands of data points in seconds, something humans can't do. They are then able to accomplish tasks such as image recognition and modeling housing prices. By training correctly, these models are able to produce some amazingly accurate results with some being above 99% accurate.*
2. The two answers are not the same, but they are very close. This is because the model trains on the data by guessing and then using the loss function's output with the optimizer to produce smaller and smaller losses. The prediction converges to the same value (of 22 in this case), so the difference is very minimal, but the output is always slightly different.
3. According to the model, the Hudgins house presents a good deal, whereas the Moon house is the worst deal. This is because the model looks at the price relative to the amount of bedrooms. The Moon house is a two bedroom house that costs about $250K, but according to the model, a two bedroom house should cost around $150K, $100 less than the Moon house price. The Church house, although costing $120K more than its estimated price, is only 1.4x overpriced compared to the Moon house's 1.7x. The Hudgins house is a 3 bedroom house that costs about $100K, but the model predicts that it would cost $215K, more than double the price.  
| Home(# Bedrooms) | Moon(2) | Church(4) | New Pt Comfort(3) | Mobjack(4) | Mathews(5) | Hudgins(3) |
|------------------|---------|-----------|-------------------|------------|------------|------------|
| Estimated Price  | $150K   | $280K     | $215K             | $280K      | $350K      | $215K      |
| Actual Price     | $250K   | $400K     | $230K             | $290K      | $350K      | $100K      |
