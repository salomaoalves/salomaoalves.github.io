---
layout:       post
title:        "NLP Social Media Comments"
author:       "Salomon"
header-style: text
catalog:      true
tags:
    - Python
    - WebScraping
    - Flask
    - NaturalLanguageProcessing
    - SentimentAnalysis
---

> In short, from a given url - a Insta post or a Youtube video, a Flask App will scrape all comments and will apply some NLP into the data extracted (create n-grams, tf-idf, and so on) - inclusive a Sentiment Analysis is done. Also, instead of read from some url, you can upload a file or use a default text already insert in the project.

Click here to see the [Github Repo](https://github.com/salomaoalves/DataScience_MachineLearning/tree/main/InstaYTComments) with more technical information *has a readme*.

## Knowledge
### Flask
Used in the **main.py** script - initiate the Flask Application, create the routes app - using POST and GET method. Use `render_template()` function from **Flask** to render a html page. GET routes are simple, it'll just render a more simple html page, the POST routes are more complex, it'll get input data from a form, treat it and call the functions, to then render a html page.

<figure style="margin: 0;">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 12px;">
    <!-- Coluna 1 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-home.png" alt="App home page" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Home page</figcaption>
    </figure>
    <!-- Coluna 2 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-ytinsta.png" alt="YouTube / Instagram URL input" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">YouTube / Instagram input</figcaption>
    </figure>
    <!-- Coluna 3 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-upload.png" alt="File upload" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">File upload</figcaption>
    </figure>
  </div>
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 10px;">Web UI Preview</figcaption>
</figure>

### Web Scraping
**services/scraping.py** has both function to scrape data (from YouTube and Instagram). With the help of **Selenium**, start a browser connection, making it interactive - automatically load all the comments, and then, extract the data/comments.

### Natural Language Processing
During the application, some NLP methods was applied. Tokenization and stop word deletion was made in all three files below.

**services/ngram.py** here, a unigram, a bigram, a trigram and a mix of the three is made. Use **NLTK** to create the bi and trigram, also, make filter functions to remove stopwords, spaces and tokens from the wrong type of the bi/trigrams generated. Save all 4 grams in **../static/dataset** folder.

<figure style="margin: 0;">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 12px;">
    <!-- Coluna 1 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-unigram.png" alt="Unigrams" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Unigrams</figcaption>
    </figure>
    <!-- Coluna 2 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-bigram.png" alt="Bigrams" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Bigrams</figcaption>
    </figure>
    <!-- Coluna 3 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-trigram.png" alt="Trigrams" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Trigrams</figcaption>
    </figure>
  </div>
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 10px;">N-gram analysis</figcaption>
</figure>

**services/tfidf.py** use bag of words to store the comments and calculate the tf-idf. This calculation is made by hand, using the python functionality to replicate the formulas. **services/wordcloud.py** it'll create a wordcloud, by using the module **wordcloud**. Save the image into a customized path and return it.

<figure style="margin: 0;">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 12px;">
    <!-- Coluna 1 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-token.png" alt="Tokenization" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Tokenization</figcaption>
    </figure>
    <!-- Coluna 2 -->
    <figure style="margin: 0;">
      <img src="/img/InstaYTComts-wordcloud.png" alt="Word cloud" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Word cloud</figcaption>
    </figure>
  </div>
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 10px;">Tokenization & word cloud</figcaption>
</figure>

### Sentiment Analysis
First, **services/set_train.py** script 'll take train data from different sources, put in a specific format and then, stored it (in **services/data**) to be used later. Run before the application.

**services/sent_analysis.py** is the file with the functions used for the application. It'll get the data to train the model (generated in *set_train.py*), put in a Vectorize format, train a *BernoulliNB()* algorithm from **sklearn**, make predictions with the extract data and then, put the result in a pre-defined format to be returned.

<figure style="margin: 0;">
  <img src="/img/InstaYTComts-sentAnaly.png" alt="Sentiment analysis" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Sentiment analysis</figcaption>
</figure>

## Structure
The projects is composed with the following folder and files:
  - **media_files** *folder* contain the txt files that can be used as source data
  - **services** *folder* contain the python code responsible to scrape the data, treat it and apply some NLP methods (tokenization, n-gram, TF-IDF, Wordcloud) - also a sentiment analysis is done
  - **static** *folder* contain static data - like the CSS files, images, JS scripts, the created  n-gram in csv format
  - **templates** *folder* contain the html file used to show the information - front end part
  - **Dockerfile** *docker file* to deploy the app
  - **NLP** a *docx file* with explanation about some concepts in NLP - text in pt-br
  - **POS_tagger_brill** *pickle files* that load pos_tag in pt-br
  - **main** the main *(python) script* responsible to launch the Flask app and its pages - the one to be run
  - **requirements** a txt file with the python libs version required

*Images are AI made*