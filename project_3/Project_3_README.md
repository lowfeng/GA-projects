# Project 3


## Contents  

- [Background](#Background)
- [Problem Statement](#Problem-Statement)
- [Data](#Data)
- [Research](#Research)
- [Data Dictionary](#Data-Dictionary)  
- [Findings](#Findings)
- [Conclusions & Reccomendations](#Conclusions-&-Recommendations)


## Background
Reddit has been a centralized source of gaming news, opinions and debates for consoles and their games.  In particular, the [r/xbox](https://www.reddit.com/r/xbox/) and [r/playstation](https://www.reddit.com/r/playstation/) consoles are the 2 most popular and are always in comparisons with each other. 

As a consumer, buying a console on which one is the most popular, may seem like a poor choice to make.

But, thanks to the psychological concept of informational social influence, it is one many gamers make. What this means is that many consumers will look towards their peers online to choose the ‘right’ console because of a desire to be correct when there is no obvious choice.


## Problem Statement  

The moderators of the xbox and playstation subreddits understand that for the consumer to make a proper informed decision, ideally their subreddits should only contain posts related to their console.

As misclassification of consoles by the individual subreddit authors (intentionally/mistakenly), are confusing the readers on the subject topic.

As such, the moderators would like to identify posts in their subreddit that are about their rival console. Hence we have been tasked to construct and find the best classification model to correctly predict the subreddit a given post belongs to, through identifing the keywords associated with the subreddit.


## Data  


* [api.pushshift.io](https://api.pushshift.io/reddit/submission/search):  We will be using this program to perform webscraping on the 2 subreddit posts
* [`xbox.csv`](./datasets/xbox.csv): This contains the most recent 2200 xbox subreddit posts
* [`playstation.csv`](./datasets/playstation.csv): This contains the most recent 2200 playstation subreddit posts


## Research

* According to a [comment](https://www.reddit.com/r/xboxone/comments/iwour0/unpopular_opinion_we_need_to_unify_all_xbox/) made on the xbox subreddit, there are many subreddits made for each generation of console (r/XboxSeriesX, r/SeriesXbox, r/XboxOne, r/PS4, r/PS5 etc.) instead of one subreddit for each console type where the community can engage in. For the consumer looking to buy a console, they probably will explore beyond r/xbox and r/playstation and go to more specific subreddits on next-gen consoles. Ideally for our model, scraping from these subreddits would improve our model.

* The subreddits contains posts by the Moderator and bots that inform users on the ethics and rules of the subreddit. These are repetitive posts and do not contain any relevant information for building our model.

* If there are NSFW (Not Safe For Work) posts, its text is hidden by fault. This could lead to us scraping an empty post

* Reddit includes an API that allows us to send a request and receive a JSON containing information about a post, but there are issues with this. One being that reddit throttles requests to once every few seconds, which we will deal with by puting a sleep statement in our code
        
        
        
## Data Dictionary

Data contains the most recent 2200 xbox and playstation subreddit posts each, with the below table showing the variables of interest


|Variables|Dataset|Type|Description|  
|:--|:-:|:-:|:--|  
|author|unstructured|object|Subredditor whom posted submission|  
|title|unstructured|object|Title of the post|  
|self_text|unstructured|object|Includes all text inside the post|  
|subreddit|structured|object|which subreddit the post was classified under|


## Findings

### Data Cleaning
* 790 xbox & 816 playstation posts had missing text and were removed. Its possible that some of these posts only had pictures embedded, or the post is empty as the user may have deleted their account. We wouldn't know for sure exactly, but its not important for us
*3 xbox post by the same author were duplicated and removed

### EDA on Text
Although we can perform text preprocessing using tokenizers, there is some freedom to manually cleaning the data first. 
* \n\n denotes a new line. There is not spacing between it and the adjacent words. When removing, will need to put a space between
* &amp;#x200B denotes the character code for a zero-width space, which is usually between two new lines (\n\n), but we won't assume its consistently always between the new lines, hence we will remove them seperately from the new lines
* Asterisks(*) denotes bullet points and bold type face which will be removed
* Hyperlink and links denoted by the text between the []\(\) brackets parentheses. We will remove all links and hyperlinks
* We will remove the subreddit name and ps (xbox, playstation, ps)
* Numbers are denoted by digits from 0-9, we will remove them before removing punctuations
* Punctuations are denoted by symbols. We will use regex to remove all symbols finally.

### EDA on Word Count
Before vectorizing the text, we will look at the length and the word count for each reddit submission
* Some posts have missing text, which can be explained by the manual cleaning done earlier
* Most posts with text_word_counts less than 20 were mostly authors asking for help or displayed error messages 
* An average length is 335 and average word count is 73 (inclusive of both Title & selftext)
* The distributions between length & word count are similar, which is what we want to observe. If there were abnormality, we will want to further inspect indivdual words for links/words without spacings etc.

### EDA on Author
Would like to explore and analyze the Authors and see what the total number of posts per author represents.
* No moderator or bots observed in the dataset
* As we have removed duplicated posts, there doesn't seem to be anything out of the ordindary. Large number of authors have less than 3 unique posts.
* No action required after doing EDA on the author

### EDA on n-grams
To build our representation of our vocabulary we will use countvectorizer to tokenize, vectorize and represent the corpus in an appropriately.

#### Unigram
*For the posts without the stopwords, the top words were mostly prepositions which we will ignore.
*For the posts with stopwords, words like 'game, games, like, know, controller' are observed in both posts. We could remove them by including them into a stopword list, but I've decided to leave them in, to see the effects of how the Tf-idf balances out the term frequency when there are words that highly occur in both subreddits.
*The frequency for the top 15 unigram was approximately 100 - 800 for the 2 subreddits

#### Bigram
*For posts without stopwords, there was a combination of prepositions and adverbs which had a high frequency. 
*Interestingly, the bigram for xbox 'game pass' was identified to have the highest frequency under xbox. The game pass represents the xbox user account, so no surprises. On the other hand, the top bigram for playstation were related to their exclusive game titles (e.g. god of war, ghost tsushima)
*The frequency for the top 15 bigram was bwetween 25 to 200, with only 'gamepass' exceeding 50 frequency of words.
*The bigrams above definite puts a clear distinction between the subreddits, but I'm not sure how useful it will be when we vectorize the data due to the low frequency.

#### Trigram
Interestingly, for both subreddits, their trigrams are very distinct towards the exclusive console games and common help questions. However, their frequency of words are far lesser than the uni and bigrams. Its improbable that the model will consider these features during vectorization, hence we will not include them into our grid search.

### Lemmatization
Part of feature engineering, Lemmatization reduces words showing an inflection in order to return a root word. We will be storing the lemmatized text into the dataframe to compare the results with the original text. 
first we'll tokenize the text, followed by transforming it, and joining the tokens back together to return a string.

### Stemming
Also part of feature engineering, Stemming is a method where the end of words are removed if it shows derivational changes to its root word. This could be helpful as most of the semantic meaning of a word is the root word. 

As such, stemming is strict compared to Lemmatization, but we'll like to compare the results by observing which text helps the model produce a better fit


### Model Selection
I have selected the logistic regresison model using the Tf-idf vectorizer on the text stemming data as it has the highest accuracy score with a reasonable variance and bias, somewhat of a best fit. It also has a high AUC score of 0.84, which denotes good performance. Below, we will explore this model in further detail to see what we can infer from its misclassification rate and feature importance.


## Conclusions & Recommendations

It would appear that there is evidence within the data from subreddit posts, users have discussions off-topic, read off different sources, and sometimes use the reddit to connect personally with the subreddit community. 

Of all the models, the Logistic Regression model performed consistently with the lowest bias and variance, I also found that it performs well with features that are strongly correlated. I conclude that the subreddit posts consist of many correlated text, though we tried to deal with it using feature engineering like ngrams.

Of the 172 posts misclassified, 130 posts was the actual xbox posts were predicted as playstation posts. Looking at the original text, I would iterate back to do some feature engineering, and do further EDA on the missclassified text to identify if the post had tokens that caused the misclassification, or the text was generalized between both subreddits.

Given that the topics discussed and latest trends are constantly changing, the EDA done on our model will be less effective outside the period of time of our webscraped data. We can still retrain the model by feeding it with new data.

As there seems to be a stronger coefficient  We could improve on the model by scraping from the subreddit comments and other relevant subposts (r/ps4, r/ps5, r/xboxseries etc.)