<img src="http://imgur.com/1ZcRyrc.png" style="float: centre; margin: 20px; height: 55px">

# Capstone Project: Multi-Label Text classification for Trust and Safety (Content moderation)

### Lo Kok Fu DSIF 2


### Problem Statement

- On the online space, there are multiple platforms where users are able to generate and post text contents as they deem fit. With these ease of access, content violations like violence, explicit, cyber bullying or racial hate contents are constantly on the rise. 
- Toxic contents may be also communicated to vulnerable groups such as the minors or racially sensitive groups. In which, would incite violent , hate behaviours or suicide tendencies.
- Therefore there is a need to protect vulnerable groups from such toxic comments through filtering or surfacing at large scale for safe content viewership.

*Solution*

- Develop an online content NLP Machine Learning Algorithm to detect user generated toxic words and classify them for surfacing to platform censorship processes with accordance to community guidelines violations policies for online user text content enabled generation platforms.

### Executive Summary
This project is a multi-label classification problem which aims to utilize NLP to train a multi-label classifier of the type of toxic words they are and whether they are safe content.

Data was obtained and can be downloaded from Kaggle: ref link: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge/data . Text were labelled with accordance to their type of toxic category. There were 159571 rows of comments and 6 types of toxic catogories and we inserted an additional column of stating whether the comments category was safe or not safe.

For our feature extraction, we tokenised, lemmatized utilised TF-IDF to extract out 8000 features for our train - test - split.

We then performed baseline modelling with 3 models,

1) Logistic Regression with OneVsRest

2) Random Forrest Classifier

3) Decision Tree Classifier

We evaluate the model results by their F1 score. Amongst the 3, Decision Tree Classifier perform the poorest and we proceeded to drop it and performed a Logistic Regression and Random Forrest Classifier GridsearchCV to select the best hypertuning parameters for optimization. The results returned Logistic Regression with the best scoring model.


### Data
- Data set were extracted from kaggle. ref link: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge/data
- Columns in the Data set were broken down to id, comment_text, toxic, sever_toxic, obscene, threat, insult, identity_hate
- Id refers to the unique user id who posted comment
- comment_tax refers to the comment that the user posted
- toxic, severe_toxic, obscene, threat, insult and identity_hate columns refers to the labelled category which the comment_text relates to. the values are binary where 0 = no, 1 = yes. this is a multi-label classification therefore we can expect for some of the comment_text to be assigned with multi binary value in the different categories relating to the type of comments they are.
- dataset under CC0, with the underlying comment text being governed by Wikipedia's CC-SA-3.0


### Modelling Scores after Tuning

| Model | Test Accuracy | Precision | Recall | F1 Score | Train Score | Test Score |
|---|---|---|---|---|---|---|
| Logistic Regression | 0.854310 | 0.819183 | 0.907188 | 0.860943 | 0.856314 | 0.854310 |
| Random Forrest Classifier | 0.898253 | 0.898253 | 0.802176 | 0.847500 | 0.8988344 | 0.898253 |

### Conclusion 

From the modelling process,it is evident that Logistic Regression is the choice model to predict multi-label classification of the Toxic Words. 

It is also observed that top frequent words are co-related in Toxic, Severe_toxic, Insult and Obscene classifications. This relates that there is a co-relations in these classifications.

### Recommendations
Recently, NLP Deep Learning models on text classification has been achieving state of the art results. It has shown that deep learning methods are able to provide for a suite of standard academic benchmark problems. Though we had achieve a considerably good modelling result here, we can explore utilising Deep learning models such as LSTM to predict the results. since we have already provided a benchmark result here.