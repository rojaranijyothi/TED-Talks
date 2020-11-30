# TED-Talks Recommendation system and Summarization

### 1. Background,Problem and context:

TED, which operates under the slogan 'Ideas worth spreading'  is a nonprofit devoted to spreading ideas, usually in the form of short, powerful talks (18 minutes or less). TED began in 1984 as a conference where Technology, Entertainment and Design converged, and today covers almost all topics  from science to business to global issues  in more than 100 languages. The first TED, concieved by Richard Saul Wurman,who co-founded with Harry Marks, included a demo of the compact disc, the e-book and cutting-edge 3D graphics from Lucasfilm, while mathematician Benoit Mandelbrot demonstrated how to map coastlines using his developing theory of fractal geometry.But despite a stellar lineup, the event lost money, and it was six years before Wurman and Marks tried again. 

The TED Conference became an annual event in Monterey, California, attracting a growing and influential audience from many different disciplines united by their curiosity and open-mindedness and also by their shared discovery of an exciting secret. It has been held since 1990.Back then, TED was an invitation only event. It is now you are welcome and encouraged to apply to attend.TED Talks are giving so much information and knowledge about fields that are alien to the audience and amaze them in the form of outstanding short stories,breathtaking visuals  and subtle humor. We will explore datasets containing transcripts available in www.kaggle.com of all audio-video recordings of TED Talks uploaded to the official TED.com website until September 21st, 2017. Our main goal here in this project is 
to find out the similarity between TED Talks and based on those similarities to build a recommendation system.And second one is TED Talk summarization. At the same time, our focus would be to answer the below questions from the dataset available to get meaningful derivations and inferences.


### 2. Target Clients:

These meaningful derivation, inference and results can be used by several kinds of people with different aims in mind. 

- Audience who wants to know the summary of the talk from a specific area without further going through the whole talk.
- Audience who are looking for the content relevant contextual recommendations.
- Another audience of our result can be a person looking to gain information from any TED talks from a specific area. Our result would help such people to know which talk and speaker has the most popularity in that area as a suggestive guide. It is highly likely that a popular talk will have some informative message and learnings thus the listener can be benefited most. 
- A TED talk presenter can use it to know the common topic in which people are more interested to listen and thus he can plan the topic of his talk accordingly. 
- Also, the patterns from rating data for a TED talk can help speakers to know whether their talk has been informative or confusing or ok and improve accordingly.


### 3. Data Wrangling:

#### 3.1 Data Collection

The source of the data set is:

https://www.kaggle.com/rounakbanik/ted-talks

TThis dataset contains two csv files:

ted_main.csv - Contains data on actual TED Talk metadata and TED Talk speakers.
transcripts.csv - Contains transcript and URL information for TED Talks.

#### 3.2 Data Definition

Columns description for the ted_main.csv file  

Column Name |	Description	
----------- | -----------

name | The official name of the TED Talk. Includes the title and the speaker
title | The title of the talk
description | A blurb of what the talk is about
Main_speaker | The first named speaker of the talk
Speaker_occupation | The occupation of the main speaker
num_speaker | The number of speakers in the talk
Duration | The duration of the talk in seconds
Event | The TED/TEDx event where the talk took place
Film_date | The Unix timestamp of the filming
Published_date | The Unix timestamp for the publication of the talk on TED.
Comcomments | The number of first level comments made on the talk
Tags | The themes associated with the talk
Languages | The number of languages in which the talk is available
Ratings | A stringified dictionary of the various ratings given to the talk (inspiring, fascinating, jaw dropping, etc.)
Related_talks | A list of dictionaries of recommended talks to watch next
Url | The URL of the talk
views | The number of views on the talk

Columns description for the transcript.csv file  

Column Name |	Description	
----------- | -----------

transcript | Transcript of the talk  
url | The URL of the talk


#### 3.3 Data Cleaning

- Checking the NaN values.
- Typecasting the columns: Date present in the dataset is in Unix format so we processed Unix Date and changed it to YYYY-MM-DD format and created day,month and year columns for further analysis.
- Checking the outliers.
- Checking the duplicate values and removes them.

### 4. Exploratory Data Analysis

[DataWrangling & EDA Notebook](https://github.com/rojaranijyothi/TED-Talks/blob/main/Notebooks/DataWrangling%20%26%20EDA.ipynb)

We visualized the TED Talks based on various parameters. We visualized the most viewed talks of all time, top 10 speakers, themes and occupations. And made hypothesis about views and comments. Visualized the TED Talks by yearly, monthly, and weekdays.

![most_viewed talks](https://github.com/rojaranijyothi/TED-Talks/blob/main/Figures/Most_viewd_talks.png)
![occupation-views](https://github.com/rojaranijyothi/TED-Talks/blob/main/Figures/occupation_w.r.t_views.png)
![yearly_talks](https://github.com/rojaranijyothi/TED-Talks/blob/main/Figures/yearly_talk.png)
![occupatio_wordcloud](http://localhost:8889/view/Desktop/Springboard/TED-Talks/Figures/occupation-wordcloud.png)


### 5. Data Preprocessing

[Preprocessing Notebook](https://github.com/rojaranijyothi/TED-Talks/blob/main/Notebooks/preprocessing.ipynb)

 - Language Detection
 - Text preprocessing
 - Feature extraction
 - Feature Engineering
 - Handling Rare Categories
 - Create dummy features for categorical variables - MultiLabelBinarizer encoding

### 6. TED Talk Summarization

[TED Talk Summarization Notebook](https://github.com/rojaranijyothi/TED-Talks/blob/main/Notebooks/TED%20Talk%20Summarization.ipynb)

Text summarization can broadly be divided into two categories

**Extractive Summarization**:

These methods rely on extracting several parts, such as phrases and sentences, from a piece of text and stack them together to create a summary. Therefore, identifying the right sentences for summarization is of utmost importance in an extractive method.

**Abstractive Summarization**:

These methods use advanced NLP techniques to generate an entirely new summary. Some parts of this summary may not even appear in the original text.

Here I focused on the extractive summarization technique. And the algorithms we tried are

- Text summarization using spaCy
- Text Summarization using Gensim with TextRank
- Text Summarization with Sumy

From all the above algorithms, we found that summarization with spaCy makes sense to me. So I used spaCy to summarize all the TED Talks.

### 7. TED Talk Recommendation System

[Recommendation system Notebook](https://github.com/rojaranijyothi/TED-Talks/blob/main/Notebooks/TED%20Talk%20Recommendation.ipynb)

The idea is to demonstrate how one can generate recommendations just using content. This becomes essentially important when you don’t have any user-item interaction data, essentially when you are starting out new and still want to provide the consumers of your content relevant contextual recommendations.

We did recommendation system to get the top 10 most similar talks by following these steps:

- Text Preprocessing
- Tfidf Vectorizer
- Generate Cosine similarity matrix
- Built a recommendation function based on similarities


### 8. TED Talk Topic Modeling

[Topic Modeling Notebook](https://github.com/rojaranijyothi/TED-Talks/blob/main/Notebooks/Topic%20Modeling.ipynb)

In this step we tried two algorithms LDA(Latent Dirichlet Allocation) and NMF(Non-negative Matrix Factorization) for topic modeling

- Latent Dirichlet Allocation (LDA)
- Non-Negative Matrix Factorization(NMF)

The derived topics from LDA for this TED Talks dataset produces some of the topics with noisy data and are hard to interpret. I’d say the NMF was able to find more meaningful topics in this dataset. So used the NMF model for final topic modeling and got the top 20 topics along with tags.


### 9. Prediction Modeling

[Prediction Model](https://github.com/rojaranijyothi/TED-Talks/blob/main/Notebooks/Prediction%20Modeling.ipynb)

In addition to the Recommendation system, Summarization and Topic modeling, I tried prediction of TED Talk ratings using different machine learning algorithms.

Since target is a categorical variable with many classes and data is labelled data, it is a Supervised multiclass classification problem. The dataset is imbalanced because the classes in target have an unequal distribution. For modeling I choose to work with a machine learning library - scikit.learn. 

Metrics: Choosing the right metrics is the key to assess the performance of a model. I choose to take a “weighted” F1 score. For multi-class problems with imbalance data, we have to average the F1 scores for each class. The weighted F1 score averages the F1 score for each class by taking the class imbalances into account. In other words, the number of occurrences of each class does figure into calculation when using “weighted” score.

I evaluated the following machine learning models: 

  - Support Vector Machine (SVM)
  - k-Nearest Neighbors (KNN) 
  - LogisticRegression (LogReg) 
  - Random Forest (RF) 
  - SGDClassifier(SGD)
  
The output results are:

![output_result](https://github.com/rojaranijyothi/TED-Talks/blob/main/Figures/evaluation_models.png)

I choose the Cost sensitivity with random forest algorithm as the final model. After that I did hyperparameter tuning to increase the performance of the model and the model performance was increased by 1% and gave the final f1_score(weighted) as 50%.

We can we visualize the results through confusion matrix as well as with AUC-ROC and Precision-Recall curves.

![AUC-ROC and Precision-Recall](https://github.com/rojaranijyothi/TED-Talks/blob/main/Figures/auc-roc.png)

![Confusion matrix](https://github.com/rojaranijyothi/TED-Talks/blob/main/Figures/confusionmatrix.png)

In conclusion, our work led to interesting results, analysis and statistics, but also provided useful tools both for audience and speakers, which allows a better understanding of TED Talks dataset. 

This project gave me an opportunity to explore this freely available dataset using NLP and a proper data science pipeline of data wrangling, data analysis, data visualization, prediction, and data storytelling.


### 10. Future Improvements

- The recommendation engines used by the official ted page, will be a degree of magnitude more sophisticated than what we demonstrated here and would also involve use of some sort of historical user-item interaction data. Would love to try the TED Talk recommendation system using historical user-item interaction data if available.
- Further analysis can be done over the rating column in the dataset to relate the negative comments with topics of TED talk, and find the area of talk which has received more negative feedback. 
- We can also make some more analysis over topic and area of TED Talk, by combining some other datasets like news article, social media post etc to find for any pattern between how the hot discussed topics over world found from news article and social media post are included in TED talk topics, around the same time frame as of the hot discussion over the world. 
- Further we can use the most advanced technologies like deep learning and Neural Networks  to boost the accuracy of our prediction model.














