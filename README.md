# Twitter-Sentimantal-Analysis-Webapp

### What is sentiment analysis?
Sentiment Analysis is the process of ‘computationally’ determining whether a piece of writing is positive, negative or neutral. It’s also known as opinion mining, deriving the opinion or attitude of a speaker.

### Why sentiment analysis?

- **Business** : In marketing field companies use it to develop their strategies, to understand customers’ feelings towards products or brand, how people respond to their campaigns or product launches and why consumers don’t buy some
products.
- **Politics** : In political field, it is used to keep track of political view, to detect consistency and inconsistency between statements and actions at the government level. It can be used to predict election results as well!
- **Public Actions** : Sentiment analysis also is used to monitor and analyse social phenomena, for the spotting of potentially dangerous situations and determining the general mood of the blogosphere.
Installation:



**Tweepy**: tweepy is the python client for the official Twitter API.
Install it using following pip command:
```sh
pip install tweepy
```
**TextBlob**: textblob is the python library for processing textual data.
Install it using following pip command:
```sh
pip install textblob
```
Also, we need to install some NLTK corpora using following command:

python -m textblob.download_corpora
(Corpora is nothing but a large and structured set of texts.)

### Authentication:
> In order to fetch tweets through Twitter API, one needs to register an App through their twitter account. Follow these steps for the same:

- Open this link and click the button: ‘Create New App’
- Fill the application details. You can leave the callback url field empty.
- Once the app is created, you will be redirected to the app page.
- Open the ‘Keys and Access Tokens’ tab.
- Copy ‘Consumer Key’, ‘Consumer Secret’, ‘Access token’ and ‘Access Token Secret’.

#### We follow these 3 major steps in our program:

- Authorize twitter API client.
- Make a GET request to Twitter API to fetch tweets for a particular query.
- Parse the tweets. Classify each tweet as positive, negative or neutral.

**TextBlob** is actually a high level library built over top of NLTK library. First we call clean_tweet method to remove links, special characters, etc. from the tweet using some simple regex.
Then, as we pass tweet to create a TextBlob object, following processing is done over text by textblob library:

1. Tokenize the tweet ,i.e split words from body of text.
2. Remove stopwords from the tokens.(stopwords are the commonly used words which are irrelevant in text analysis like I, am, you, are, etc.)
3. Do POS( part of speech) tagging of the tokens and select only significant features/tokens like adjectives, adverbs, etc.
4. Pass the tokens to a sentiment classifier which classifies the tweet sentiment as positive, negative or neutral by assigning it a polarity between -1.0 to 1.0 .

Here is how sentiment classifier is created:

TextBlob uses a Movies Reviews dataset in which reviews have already been labelled as positive or negative.
Positive and negative features are extracted from each positive and negative review respectively.
Training data now consists of labelled positive and negative features. This data is trained on a Naive Bayes Classifier.
Then, we use sentiment.polarity method of TextBlob class to get the polarity of tweet between -1 to 1.
Then, we classify polarity as:
```sh
if analysis.sentiment.polarity > 0:
       return 'positive'
elif analysis.sentiment.polarity == 0:
       return 'neutral'
else:
       return 'negative'
 ```
Finally, parsed tweets are returned. Then, we can do various type of statistical analysis on the tweets. For example, in above program, we tried to find the percentage of positive, negative and neutral tweets about a query.

### Here Are Some ScreenShots of our Locally Hosted webapp in flask
- This is the Home Page.
>> In the bottum right corner there is a search box<br>
>> Let's search Elon Musk there.
![ss1](https://user-images.githubusercontent.com/65397085/122366801-838d4c80-cf79-11eb-8ed4-94e15707939e.jpg)
>> Sentimental Analysis of Tweets related to Elon musk
![ss2](https://user-images.githubusercontent.com/65397085/122366816-85efa680-cf79-11eb-81ff-da2e5fe492cf.jpg)
![ss3](https://user-images.githubusercontent.com/65397085/122366820-86883d00-cf79-11eb-8d5d-79bf96a62bea.jpg)
