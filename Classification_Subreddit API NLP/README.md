<img src="http://imgur.com/1ZcRyrc.png" style="float: centre; margin: 20px; height: 55px">

# Project 3: Web APIs & NLP

### Lo Kok Fu DSIF 2


### Problem Statement

We are tasked to utilize and train a classifier on a binary classification problem to predict which subreddit a given post comes from either Phuket or Bali island (our selected choice). Gathering of our data will be through web scrapping data from reddit using API.

Our solution is 2 fold:
- Using Pushshift's API to scrap for bali and phuket posts.
- Use NLP to train a classifier, 1)RandomforrestClassifier and 2)logistic regression model on which subreddit a given post came from. 

### Executive Summary
This project is a binary classification problem which aims to utilize NLP to train a classifier of scrapped data from subreddit using API to classify which reddit post it came from.

We have selected the topics which will be places of tourist beach interests. They are Bali and Phuket. These 2 places are familier to holiday beach-goers from the south east asian region and are similar in type of tourist activites in nature. Given the current pandemic situation, both islands faced limited visitors from foreign countries. It will be interesting to see what are the results we yield from the analysis of this project.

For the modelling, we choose the Logistic Regression and RandomForestClassifier for our modelling. utilizing pipelines to conduct feature engineering and using gridsearchcv to get the best parameters for our models.

Resulting with Logistic Regression model with the better consistent scoring model.Therefore we reccomend the LogisticRegression model for our binary classifier

*The following are a brief description of the islands for our commonn understanding of the individual island description. These information will come in handy during our analysis.

Bali: an Indonesian island known for its forested volcanic mountains, iconic rice paddies, beaches and coral reefs. The island is home to religious sites such as cliffside Uluwatu Temple. To the south, the beachside city of Kuta has lively bars, while Seminyak, Sanur and Nusa Dua are popular resort towns. The island is also known for its yoga and meditation retreats. ref: https://en.wikipedia.org/wiki/Bali

Phuket: A Thai province located in south of Thailand. It is the biggest Island of Thailand and sits on the Andaman sea. The nearest province to the north is Phang-nga and the nearest provinces to the east are Phang-nga and Krabi. Phuket has a large Chinese influence, therefore you will find many Chinese shrines and Chinese Restaurants around the city.Being a big island, Phuket is surrounded by many magnificent Beaches such as Rawai, Patong, Karon, Kamala, Kata Yai, Kata Noi, and Mai Khao. Laem Phromthep viewpoint is said to feature the most beautiful sunsets in Thailand. It isn’t all just beaches though, there is also the famous Phuket NIGHTLIFE,and is a hotspot for tourists in Thailand. ref: https://www.tourismthailand.org/Destinations/Provinces/Phuket/350

### Data Set Dictionary

| S/N | Data | Description | File |
|:---:|:---:|:---:|:---:|
| 1 | phuket_df | scrapped submission posts of phuket from reddit | phuket_submission.csv |
| 2 | phuket_comments | scrapped comments posts of phuket from reddit | phuket_comments.csv |
| 3 | bali_df | scrapped submission posts of bali from reddit | bali_submission.csv |
| 4 | bali_comments | scrapped submission posts of bali from reddit | phuket_comments.csv |
| 5 | df | combined cleaned dataset | df_clean.csv |


### Data
Utilizing the API, we scarpped 8 loops of 100 posts and 4 types of datasets. each set contains 800 rows, namely the submission and comments posts from each classification. Text data is set to the ‘all’ column which is a cleaned and combined version of self-text and title. we then cleaned and merged the data together as a single set. we've concat the comment post to the submission posts as we will like to know what are the words that are used in the different classification topic.


### Modelling

Features such as word count and a sentiment intensity analyzer added to the dataset to include in the modelling. A function transformer is created to create the columns relevant for our model. . Our numerical data is our recently calculated word count and sentiment.we've utilised Logistic Regression and RandomForesetClassifier for our modeling.The Logistic Regression was the better scoring model and it's AUC scores are only slighty different. 

### Conclusion 

From our modelling, we can deduce that logistic regression is the better model to predict the classification of the posts it is from. Either the island, Bali or Phuket.

it is also observed that words such as names of places of the island or related locations provides a strong classifier between the 2 different places. however there are some words that are a point of interest such as 'business' in the bali features. this may imply business affected by covid or maybe people are heading to bali for business. for phuket would be 'sandbox' a termed coined by the thai govt to 'sandbox' vaccinated visitors to thailand in phuket before they are able to travel around the country. Sentiments are on the positive side for both islands. we hope this stays this way and await for travel to reopen fully.

### Recommendations
It is evident from the scoring of the accuracy and F1 scores that the logistic regression is the better consistent model classifier with slight differences from the Random Forrest Classifier model for this project. it's scoring is slightly lower than the Logistic Regression model but it is also the least overfitted / underfitted.
Thus, we will reccomend logistic regression model for the classification of posts from bali or phuket.

Noteably, from the train, test score it is observed that both models indicated a overfitness. If we are given more time, in the follow up to this project. we will would do more detailed hyper tuning of the model's parameters, reduced feature enginnering to curb overfitting and trying other models to achieve a better result with a better fit model.