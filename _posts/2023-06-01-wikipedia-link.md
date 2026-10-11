---
layout:       post
title:        "Wikipedia Link"
author:       "Salomon"
header-style: text
catalog:      true
tags:
    - Python
    - Neo4J
    - Cypher
    - WebScraping
---

> I want to test Neo4J database, so I find a graph project; basically, if you click in the first hyperlink (has some rules that should be followed) of a Wikipedia page, and continue doing that, you will, probably, end up in the Philosophy page or in a loop. 
> So, I scrape many hyperlink/blue word and, with the help of Neo4J, store and query them.

Click here to see the [Github Repo](https://github.com/salomaoalves/random/tree/main/Wiki1Link) with more technical information *has readme*.

The project is a application, that can be started in **main.py**, to execute all this functionality; you can divide it in 5 parts: Custom Ingestion, Auto Ingestion, View Paths, Summary and Graph Display. So, from the main script, you are able to call the web scraping functions to gather data *Custom/Auto Ingestion*, get graph and nodes information *View Path and Summary* and also has a visualization about the graph *Graph Display*.

<figure style="margin: 0;">
  <img src="/img/wiki1link-home.png" alt="Wikipedia first-link graph" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Home page</figcaption>
</figure>


## Tools
### Web Scraping
Help to gather the data from Wikipedia pages. First, in **ETL/connection.py**, use **Selenium** lib to help connect with a browser (can choose between Firefox and Chrome) and get the page source - the html of the wikipedia page; if an error connection happens 3 times, save it into a csv file.

**ETL/extractWords.py** and **ETL/autoWords.py** are responsible to get the wiki source page (call *connection.py funcs*) and extract the words from the html. To do the last one, I use **BeautifulSoup** lib to extract blocks of words / paragraphs (use funcs like *find_all()* and *find()*) and **re** libs *Regular Expression* to query into the paragraphs, to apply the rules and extract the correct word. Actually, *autoWords.main()* will only collect different words, where each one of them will be passed to *extractWords.main()*, where the graph starting from this words is build.

<figure style="margin: 0;">
  <img src="/img/wiki1link-webscraping.png" alt="Wikipedia first-link graph" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">One of the web scraping process</figcaption>
</figure>

### Neo4J / Cypher
You can find all functions related to it in **ETL/neo4jFunc.py**. There, has functions that will, using Cypher language, get nodes, paths and loops, insert pair of nodes to build the graph, and delete nodes. To work, you gonna have two functions for each action, the main one, which will create the session, and an auxiliary one, where the cypher language is used to work with the data.

<figure style="margin: 0;">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 12px;">
    <!-- Coluna 1 -->
    <figure style="margin: 0;">
      <img src="/img/wiki1link-path.png" alt="Path to Philosophy graph" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Path to Philosophy</figcaption>
    </figure>
    <!-- Coluna 2 -->
    <figure style="margin: 0;">
      <img src="/img/wiki1link-pathterminal.png" alt="Path query in terminal" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Path query (terminal)</figcaption>
    </figure>
    <!-- Coluna 3 -->
    <figure style="margin: 0;">
      <img src="/img/wiki1link-loop.png" alt="Loop detection" style="width: 100%;">
      <figcaption style="text-align: center; font-size: 0.8em;">Loop detection</figcaption>
    </figure>
  </div>
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 10px;">Paths and loops in the first-link graph</figcaption>
</figure>


## Structure
The project is composed with the following folder and files:
 - **ETL** *folder* contain the python code responsible to scrape the data from wikipedia and the Neo4J functions to work with the data
 - **common** *python file* with common and different functions used during many files 
 - **createFakeData** *python script* responsible to create and store the fake data used to test
 - **graph_visu** *python file* with functions that will display the graph - use lib **NetworkX** to help 
 - **ingestion** *python file* responsible to collect the data and build/ingest the graph, always starting with a word. Has two main functions; (1) `auto_ingestion()`, start with random words, and (2) `costum_ingestion()`, start with an input word
 - **main** main *python script*, will create a prompt in terminal with better layout, in there you will have a short description and explanation about the project and how it works and then you can start it - control the project
 - **path** *python file* with functions related to path info, that is, given two words, show the path between them, to the word Philosophy, if the word belong to a loop and others
 - **summary** *python file* has the functions responsible to generate a summary - graph degrees, loops, predecessor/successor nodes, path between nodes. With the help of Cypher, I was able to read the data and manipulate it - make filters, aggregations and so on

<figure style="margin: 0;">
  <img src="/img/wiki1link-summary.png" alt="Wikipedia first-link graph" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Summary information</figcaption>
</figure>

All the files has comments, so you are able to understand how they works - but in the repo there is a readme with more information.

*Images are AI made*