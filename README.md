# NLP-Sentiment-Analysis

## Creating a multi-categorical Classification Model to predict sentiment of tweets

Apple and Google have tasked me as a 3rd party investigator to research user sentiment on twitter. My process for this will be broken down into 4 major sections.

1. Preprocessing
2. Data Exploration
3. Modeling
4. Recommendations

There are 3 models used in the notebook. The first is a Multinomial Naive Bayes Classifier, the second is a Support-Vector-Machine, and the third is a Perceptron neural net using Keras. The MultinomialNB and SVM both performed similarly, however the Neural Net acheived better training accuracy and test accuracy. I will seperate each of the previously mentioned steps for the different models.

## Preprocessing

The MultinomialNB and SVM were preprocessed in the same way and used the same training and test sets. I tokenized the tweets and removed stopwords, including twitter specific words that don't add value to the tweet. I also added features for number of sentances and emoji usage. I tried stemming the words but did not acheive better results. 

The Neural Net was tokenized using Keras.text and the 20000 most important words. The sequences were also padded to ensure the same legnth for entry into the neural net.

## Data Exploration

Insert dist frequency graphs and the like here

## Modeling

Insert results here

## Recommendations

Insert cool findings and recs here



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
