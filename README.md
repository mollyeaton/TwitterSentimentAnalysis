# CS254 Final Project - Sentiment Analysis on Tweets
## Ben Caruso
## Molly Eaton

Our goal is to correctly classify the sentiment - positive or negative - of a group of tweets, for the purposes of better understanding natural language processing and eventually using the model to gain a better knowledge of how people are feeling about a certain idea or media news. 

### Obtaining and cleaning the data
For this version of our project, we chose to use a subset of 80,000 tweets from our original dataset. We removed the “Sentiment Source” column, as it does not benefit our model in any way, and renamed the SentimentText column to “Tweet” for simplicity.

### Preprocessing:
### Remove twitter handle 
Use a function to find and remove all instances of @___ in order to remove usernames from the tweet.
Remove special characters: Parse through the entire set of tweets and remove all unnecessary characters such as commas, symbols, and other punctuation/odd keys that won’t help with determining sentiment
### Remove 3-letter words
Remove stop words such as “the” and “as” that simply act as noise and don’t contribute to determining sentiment. All words not greater than 3 letters fall into this category and so are removed.
### Tokenize tweet
Break down each tweet into a vector of individual words, which in our case is delimited by an empty space.
### Stemming
Remove unnecessary suffixes from each word, so that words like “grabbing” or “missed” become “grab” and “miss”. Doing this will reduce the overall variety of words we have and thus decrease computational lookup time when the algorithm must find a certain word.
### Stitch tweet back together 
Put the words back together to form a clean, ready-to-analyze version of the original tweet.

### Feature Extraction
Using the bag-of-words method and CountVectorizer from sci-kit learn, we transform the clean tweets into a sparse matrix representing the usage of each word in our data. Each dataset may only contain a few instances of a certain word, which is why the matrix is so sparse, and why it is so important to clean and pre-process the data so that only the relevant words for determining sentiment are kept. 
### Normalize data
We transform the bag of words matrix into a dataframe, and then used preprocessing from sci-kit learn to normalize our data. Thus, each word becomes associated with a number on a new scale, which allows the algorithm to run much faster.

### Training
We train our data using cross validation with 5 folds. We performed this cross validation on both a Logistic Regression model and a Decision Tree model.

### Graphing
Lastly, we graph the most popular words associated with positive/negative tweets, in order to gain a better understanding of the tweets we are working with.

### Bibliography
Sources we used to complete this version of the project:

Das, Deepak. “Social Media Sentiment Analysis Using Machine Learning : Part - I.” Medium, Towards Data Science, 18 Oct. 2019, towardsdatascience.com/social-media-sentiment-analysis-49b395771197.

Naji. “Twitter Sentiment Analysis Training Corpus (Dataset).” Thinknook, thinknook.com/twitter-sentiment-analysis-training-corpus-dataset-2012-09-22/.

Inzaugarat, Euge. “Learning How to Perform Twitter Sentiment Analysis.” Medium, Towards Data Science, 20 Apr. 2019, towardsdatascience.com/keras-challenges-the-avengers-541346acb804.
