# Predicting-Prices-Dont-Be-Fooled

I've been reading a lot online about people's projects with stock/cryptocurrency data in which they use machine learning algorithms and neural networks to "predict" future prices. Here, I've demonstrated a similar project in which I use some metrics like Tweet Volume, Google Trends Volume, Market Cap, and Trading Volume to 'predict' tomorrow's opening price. The trick here is that yesterday's price, is being fed into the model (or something similar like avg last 5 days). The model quickly learns that pinning the prediction at yesterdays price and then slightly nudging it up or down based on the other features to try to predict in the right direction. This is a fine strategy, for example, if these other features were perfectly indicative of price movements, this would work great. Essentially your model would know whether or not the price will rise or fall, allowing you to get rich quick! The problem here, is using metrics like R^2 or RMSE to show people "look how well my model predicts!". I've also seen the instance where the header photo of the article/blog post is a plot similar to the plotly output(attached seperately as Capture.png since GitHub and Plotly aren't compatible); further, there is no code included to show the reader that the previous prices were actually included in the regression algorithm. Had I run this same exact algorithm, but filled the volume features with randomly generated values, the output would still look the same from a distance, and the R^2 would also be extremely high. An even sneakier way to pull off a trick like this is to build a recurrent neural network with x amount of previous prices sequenced for each instance of the network, but failing to shuffle the training data. You tell the network to minimize loss, and the network quickly learns: "Hey look, if I use yesterday's price for every prediction, the loss function minimizes!". 

As you can see (to my disapointment), using Tweet Volume, Google Trends, Market Cap, and Trading Volume to predict this nudge actually performed worse than simply buying at the beginning and selling at the end of the backtesting interval, even though the model evaluation metrics are outstanding. With that being said, I just read a scholarly PhD-authored article published at a well-known University with no reference to this problem I'm outlining, that ultimately reached the conclusion: "By utilizing a linear model that takes as
input tweets and Google Trends data, we were able to accurately predict the direction of price changes." Later in the paper, they mention: "The study found that logistic regression performed best to classify these tweets and that they were able to correctly predict 43.9% of price increases". From the perspective of a trader that wants to make money, correct predicition of 43.9% is less than par (it is worse than random guessing, no?). But, I will say, that plot of the prediction line dancing so precisely with the actual price line is very appealing; maybe too much so to the naive reader.

I would like to make clear that pinning the prediction to a previous price, and then using other features to send the prediction up or down is likely very useful. But, I think many people are being decieved when they read these types of articles that do not outline what exactly makes up their training data.

My ideas regarding this topic are that even though these online articles seem catchy, machine learning/neural nets are not the best approach to algorithmic trading. Or, at least, these algorithms are not able to detect complex trends in stock/crypto prices without additional aid. I think including standard chart metrics and complex trading theories (ex. MA, RSI, Regression to mean) are necessary.
