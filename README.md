# Twitter_Sentiment_Analysis

It is no longer difficult to understand what people think about a topic by analysing the tweets shared by people. Sentiment analysis is one of the most popular use cases for NLP (Natural Language Processing).

Here,I am going to use “Tweepy,” which is an easy-to-use Python library for accessing the Twitter API. You need to have a Twitter developer account and sample codes to do this analysis. You can find the Colab Notebook code in my Github Repository.

## *Step 1: Install and Import Libraries*
Before analysis, you need to install textblob and tweepy libraries using !pip install command on your Colab Notebook.
```
# Install Libraries
!pip install textblob
!pip install tweepy

```
You need to import libraries that you will use in this sentiment analysis project.
```
import re
import tweepy as tw
from textblob import TextBlob
import pandas as pd
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
import matplotlib.pyplot as plt

```

## *Step 2: Authentication for Twitter API*
Before the authentication, you need to have Twitter Developer Account. If you don’t have, you can apply by using this [https://developer.twitter.com/en](link). Getting Twitter developer account usually takes a day or two, or sometimes more, for your application to be reviewed by Twitter.

Open the above mentoned link and click the button: 'Developer Portal'
1.Fill the application details.
2.Once the app is created, you will be redirected to the app page.
3.Open the ‘Keys and Access Tokens’ tab.
4.Copy ‘Consumer Key’, ‘Consumer Secret’, ‘Access token’ and ‘Access Token Secret’.
```
# Authentication
consumerKey = “Type your consumer key here”
consumerSecret = “Type your consumer secret here”
accessToken = “Type your accedd token here”
accessTokenSecret = “Type your access token secret here”
auth = tweepy.OAuthHandler(consumerKey, consumerSecret)
auth.set_access_token(accessToken, accessTokenSecret)
api = tweepy.API(auth)

```
After your authentication, you need to use tweepy to get text and use Textblob to calculate positive, negative, neutral, polarity and compound parameters from the text.

## *Step 3: Fetching Tweets*
##### tw.cursor 
We use pagination a lot in Twitter API development. Iterating through timelines, user lists, direct messages, etc. In order to perform pagination we must supply a page/cursor parameter with each of our requests. The problem here is this requires a lot of boiler plate code just to manage the pagination loop. To help make pagination easier and require less code Tweepy has the Cursor object.

To know more about *tweepy* visit [https://docs.tweepy.org/en/v3.5.0/api.html]

## *Step 4: Cleaning Tweets to Analyse Sentiment*
Use regualr expression to clean RT,hyperlink, punctuation characters etc.. and finally convert to lowercase and then split the sentence into tokens.
Now using for loop check whether those tokens are present in stopwords are not.If not then add those tokens to empty list.Then join all those tokens to get a sentence.

## *Step 5: Sentiment Analyse*
Now, I can use cleaned text to calculate polarity, subjectivity, sentiment, negative, positive, neutral and compound parameters again. For all calculated parameters, I create new features to my data frame.When you have a look into tweet list you can see some duplicated tweets, so you need to drop duplicate tweets.
