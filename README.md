# NLP-Sentiment-Analysis

## Creating a multi-categorical Classification Model to predict the sentiment of tweets

Apple has tasked me as a 3rd party researcher to assist their marketing team with obtaining information from Twitter and sentiment analysis. They gave me a dataset containing about 9000 tweets from around 2011 - 2013. The tweets content is about Apple, its products, and a few competitors like Google or Andriod. Apple has asked me to create a sentiment analysis model that can be used to determine if future tweets are positive, neutral, or negative to a brand, and offer them some recommendations based on this batch of tweets on how they might improve their products or brand. 

1. Preprocessing
2. Data Exploration
3. Modeling
4. Recommendations

There are several models used in the notebook. I began with MultinomailNB and an SVM, before moving on to Random Forest, Logistic Regression, and XGBoost. The MultinomialNB and SVM both performed similarly with poor accuracy and F1 scores. The Random Forest and XGBoost had clear advantages in both metrics mentioned, and the Neural Net achieved better training accuracy, test accuracy, and a decent F1 score. It's worth noting that the Random Forest using Word2Vec had the best F1 score of 95%, however, the number seems too good to be true, and considering the Neural Net's accuracy and F1 score, I'm inclined to use that as the best model going forward, but the Random Forest would probably be ok as well.

For evaluation, I created a validation set of 1800 tweets (20% of the training set) and used this validation set for the F1 score and evaluation.

## Preprocessing

The MultinomialNB and SVM were preprocessed in the same way and used the same training and test sets. I tokenized the tweets and removed stopwords, including Twitter-specific words that don't add value to the tweet. I also added features for the number of sentences and emoji usage. I tried stemming the words but did not achieve better results.

The Neural Net was tokenized using Keras.text and the 20000 most important words. The sequences were also padded to ensure the same length for entry into the neural net.

The Random Forest and XGBoost models used a Word2Vec preprocessing method with a pre-trained Glove vectorizer.

## Data Exploration

As part of my EDA and feature engineering, I checked different attributes of the tweets like if they contain emoticons, or how many sentences the tweets contain.

There was a massive class imbalance where about 60% of the tweets were classified as "No emotion." I suspect that a larger dataset with more tweets classified as either 'Positive' or 'Negative' would tremendously help the models perform better.

Image 1 is the count of the tweets with x number of sentences in Positive, Neutral, and Negative tweets

![image](https://user-images.githubusercontent.com/104473048/224124854-12af0e98-4133-49d2-a11e-5853bf23a345.png)

Image 2 is the count of tweets that contain emoticons in Positive, Neutral, and Negative tweets

![image](https://user-images.githubusercontent.com/104473048/224124973-c1800bd2-626d-4774-931f-267daa689547.png)

I also plotted a 'Word Cloud' to show the frequency of words in all tweets in a more visual format than just a graph

![image](https://user-images.githubusercontent.com/104473048/224125494-d3e95971-f04a-4be7-bc60-67624a7bbb84.png)

There are 3 other word clouds in the notebook for showing Positive only, Neutral only, and Negative only.

Lastly, I found similar words in the Word2Vec model for the stakeholder to use in marketing and advertising. A sample of those is shown below.

![image](https://user-images.githubusercontent.com/104473048/224126174-63eb547f-90df-43ea-bcd0-ee4fdadaedaa.png)

## Modeling

As the Neural Net, Random Forest, and XGBoost models performed the best, I will only be discussing them. The previous model's accuracy and F1 scores sat near the class imbalance of 60%

For the Neural Net, I found that using 3 training epochs achieved the best return. Any further training would likely be overfitting the model on the training set for lower returns on loss and validation accuracy. The Neural Net model achieved a training accuracy of 75%, a validation accuracy of 67%, and an F1 score of 80%.

The Random Forest model achieved a training accuracy of 68%, and an F1 score of 95%

The XGBoost model achieved a training accuracy of 68%, and an F1 score of 94%

## Recommendations

Using Gensim Word2Vec I was able to find the top 10 most similar words used in both positive and negative settings for various words associated with Apple. Below are my recommendations to apple based on my research, modeling, and findings.

1. One of the most positive words associated with Apple is 'Store' / 'applestore.' People love the Apple Store, it was revolutionary when first introduced. How can you market the store and highlight how great it is, and get people to come in?
2. Some common Positive iPhone words are 'handy' and 'schedules.' People love how great the iPhone is as a personal device for day-to-day tasks. Create marketing to highlight businessmen using the iPhone for scheduling meetings, calendar appointments, etc. Or families scheduling playdates for children and soccer games etc.
3. A recurring negative word is sales. Prices are high and there aren't enough discounts and sales for iPhones, iPads, etc.

## Repository Structure

```
.
└── NLP-Sentiment-Analysis
    ├── Data
    │   └── Data.csv
    ├── .gitignore
    ├── NLP and Sentiment Analysis.ipynb
    ├── Notebook.pdf
    └── README.md
