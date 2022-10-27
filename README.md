# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

### Overview

Reddit is a social news, content, and discussions website. Posts are organised according to subject into user-created 'subreddits'. Members submit content (such as images, texts, and links) to subreddits, which can then be voted up ('upvote') or down ('downvote') by other members.

### Problem Statement

Using Pushshift's API, posts from two subreddits, namely r/depression and r/BipolarReddit, will be collected. Natural Language Processing (NLP) will then be used to train a classifier to determine which subreddit a given post came from.

### Datasets

This project analysis is based on the following two data sets from Reddit: 

r/depression - With 890k members, this subreddit is about peer support for anyone struggling with a depressive disorder.

r/BipolarReddit - With 72.3k members, this subreddit is for people with bipolar disorder to discuss who they are, how they think and what helps them cope in life. 

### Data Dictionary

The data comes from two subreddits: Depression and BipolarReddit. 1000 submissions were pulled from each subreddit and later merged for analysis in the project.

|Feature|Type|Description|
|---|---|---|
|selftext|object|The body of the post|
|title|object|Title of the post|
|subreddit|int64|The subreddit where the post was taken from. '0' for depression and '1' for bipolar|

### Executive Summary

This project seeks to create a text classification model to seperate posts drawn from two fairly similar subreddits.

The work was done in two separate jupyter notebooks. The first one focused on webscraping using Pushshift's API and getting the relevant data from Reddit. The second notebook focused on initial cleaning, preprocessing, EDA, building and evaluating of models for the classification problem.

Below are steps for data collection and initial cleaning.

- Webscraping
- Reading and displaying datasets
- Combining necessary text data together
- Remove duplicates
- Handle missing values
- Handle unwanted tags

Further preprocessing and EDA was then done after the initial cleaning to get a final dataset.

- Create stop word list
- Tokenize words
- POS (Part of speech) tagging on tokenized words
- Create lemmatized words from POS tagged words
- Draw WordCloud to visualise
- Explore word and character length of posts
- Finding most common words in the original text

Lastly, the lemmatized text of the final dataset is used for building and evaluating of models. Four models are built, namely  Multinomial Naive Bayes with CountVectorizer, Multinomial Naive Bayes with TfidfVectorizer, Random Forest Classifier with CountVectorizer and Random Forest Classifier with TfidfVectorizer. The performance of the models were then compared using various metrics.

The Multinomial Naive Bayes with CountVectorizer was chosen as the best perfoming model, as it has good generalisation, accuracy and ROC-AUC scores.

### Conclusions and Recommendations

Using a Multinomial Naive Bayes classifier trained on title and selftext combined, we are able to predict post into r/depression or r/Bipolarreddit with a reasonable accuracy of ~85% - showing that although depression and bipolar have many similarities, they still have some key differences. The differences may mainly be due to differences in the behavior of depression and bipolar person. The similarities behind the model misclassifications may be due to more generic, day-to-day topics such as people asking for help or life advice, which are likely to be similar between the two subreddits.

To further improve model accuracy, a bigger corpus that incorporates a bigger vocabulary on the topic on depression and bipolar is needed. As society is constantly changing, new words are also constantly emerging in these subreddits. Therefore, it would not be enough to train the model on/obtain the training corpus from past subreddit posts. A more useful corpus for model training would be sites that report on both depression and bipolar conditions.

Areas for expansion and future exploration:

- use word similarities (e.g. word2vec) to classify posts instead of frequency
- use latent dirichlet allocation (LDA) to first extract topics from words before classifying (as a dimension reduction technique)
- explore other classification models e.g. SVM
- explore relationship between post content, number of comments, and upvote ratio
