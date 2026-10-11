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

> In short, given a URL (an Instagram post or a YouTube video), a Flask app scrapes all the comments and applies some NLP to the extracted data (n-grams, TF-IDF and so on), including a Sentiment Analysis. Instead of reading from a URL, you can also upload a file or use a default text already included in the project.

Click here to see the [Github Repo](https://github.com/salomaoalves/DataScience_MachineLearning/tree/main/InstaYTComments) with more technical information *it has a README*.

## Knowledge
### Flask
Used in the **main.py** script to initialize the Flask application and create the app routes, using the POST and GET methods. The `render_template()` function from **Flask** renders the HTML pages. GET routes are simple: they just render a simpler HTML page. POST routes are more complex: they get the input data from a form, process it and call the functions, and then render an HTML page.

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
**services/scraping.py** has both functions that scrape data (from YouTube and Instagram). With the help of **Selenium**, they open a browser connection, interact with the page to automatically load all the comments, and then extract them.

### Natural Language Processing
Several NLP methods are applied in the application. Tokenization and stop word removal are done in all three files below.

**services/ngram.py** creates unigrams, bigrams, trigrams and a mix of the three. It uses **NLTK** to create the bigrams and trigrams, with filter functions that remove stop words, spaces and tokens of the wrong type from the generated bigrams/trigrams. All 4 n-gram sets are saved in the **../static/dataset** folder.

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

**services/tfidf.py** uses a bag of words to store the comments and calculates the TF-IDF. The calculation is done by hand, using plain Python to replicate the formulas. **services/wordcloud.py** creates a word cloud using the **wordcloud** module, saves the image to a custom path and returns it.

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
First, the **services/set_train.py** script takes training data from different sources, puts it in a specific format and stores it (in **services/data**) to be used later. It must be run before the application.

**services/sent_analysis.py** has the functions used by the application. It loads the training data (generated by *set_train.py*), vectorizes it, trains a *BernoulliNB()* model from **sklearn**, makes predictions on the extracted data and then returns the results in a predefined format.

<figure style="margin: 0;">
  <img src="/img/InstaYTComts-sentAnaly.png" alt="Sentiment analysis" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Sentiment analysis</figcaption>
</figure>

## Structure
The project is made up of the following folders and files:
  - **media_files** *folder* contains the txt files that can be used as source data
  - **services** *folder* contains the Python code responsible for scraping the data, processing it and applying some NLP methods (tokenization, n-grams, TF-IDF, word cloud), as well as the sentiment analysis
  - **static** *folder* contains static data, like the CSS files, images, JS scripts and the generated n-grams in CSV format
  - **templates** *folder* contains the HTML files used to display the information (the front end)
  - **Dockerfile** *docker file* to deploy the app
  - **NLP** a *docx file* explaining some NLP concepts (text in pt-br)
  - **POS_tagger_brill** *pickle files* that load the POS tagger for pt-br
  - **main** the main *(Python) script*, responsible for launching the Flask app and its pages (the one you run)
  - **requirements** a txt file with the required Python library versions

*Images are AI-generated*