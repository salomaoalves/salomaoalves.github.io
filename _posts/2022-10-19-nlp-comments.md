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
---

> In short, from a given url - a Insta post or a Youtube video, a Flask App will scrap all comments and will apply some NLP into the data extracted (create n-grams, tf-idf, and so on) - inclusive a Sentiment Analysis is done. Also, instead of read from some url, you can upload a file or use a default text already insert in the project.

Click here to see the [Github Repo](https://github.com/salomaoalves/DataScience_MachineLearning/tree/main/InstaYTComments) with more technical information *has a readme*.

## Structure
The projects is composed with the following folder and files:
  - **media_files** *folder* contain the txt files that can be used as source data
  - **services** *folder* contain the python code responsible to scrap the data, treat it and apply some NLP methods (tokenization, n-gram, TF-IDF, Wordcloud) - also a sentiment analysis is done.
  - **static** *folder* contain static data - like the CSS files, images, JS scripts, the n-gram in csv format
  - **templates** *folder* contain the html file used to show the information - front end part
  - **Dockerfile** *docker file* to deploy the app
  - **NLP** a *docx file* with explanation about some concepts in NLP - text in pt-br
  - **POS_tagger_brill** *pickle files* that load pos_tag in pt-br
  - **main** the main *(python) script* responsible to launch the Flask app and its pages - the one to be runned
  - **requirements** a txt file with the python libs version required