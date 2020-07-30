### Response for Wednesday, July 29
#### Using NLP to build a sarcasm classifier  
1. The three news sources I have selected are Yahoo Finance, ScienceDaily, and Associated Press News. After running the model on five headlines from each source, we can see that it had the best accuracy with AP News and the worse accuracy with Yahoo Finance. I chose the sources that I did, as they would each have different types of news, and therefore, different words in their headlines. As we can see, the model performed well with more generic news. When predicting for science news and finance news, it fell a bit short. Interestingly, one of the AP news headlines was about the same story as one of the Yahoo Finance headlines. This particular headline was the only one that the model was very confident in having no sarcasm for Yahoo Finance. Overall, although ScienceDaily only had one headline misclassified, the model was not as confident in its prediction as it was for AP News  

| News Source      | Correct (no sarcasm) | Incorrect (sarcasm) |
|------------------|----------------------|---------------------|
| Yahoo Finance    | 2                    | 3                   |
| ScienceDaily     | 4                    | 1                   |
| Associated Press | 5                    | 0                   |

#### Text generation with an RNN  
1. What the RNN model does is it uses the original input string to predict the next character based on the categorical distribution. It gets this distribution by learning how characters are used together, as in, which characters get used most before and after each other. By learning the likeliness of these sequences, the model is essentially able to "remember" the writing style that Shakespeare used. Once the model has predicted the next character, it cycles back, adding the character to the input string so that the model has more context for generating the next character.     
2. For my selected text, I used the script to my favorite movie, _Monty Python and the Holy Grail_. I decided to use 30 epochs instead of 10, as there is less content to learn so training would not take as long as the Shakespeare dataset. After training, my model had some interesting predictions. It was obvious that the words were english, but they had no sense to them. It also seemed like an inexperienced typer was typing the script very quickly, causing many misspellings, but retaining the word as a whole. I thought this was surprising considering the previous characters are used to predict the next character. The script also looked like a script should and was formatted well.

#### Neural machine translation with attention  
1. Although I don't know any Spanish, the output seemed to be correct (I do speak French so I could tell more or less what it said). In the instances where a direct translation would seem awkward, like the phrase about being at home, the model did well to actually retain the intended meaning and make it sound natural.
2. Was not able to load in a different language, the website was not being recognized for some reason.  