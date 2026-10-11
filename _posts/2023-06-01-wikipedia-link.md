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

> I wanted to test the Neo4J database, so I found a graph project. Basically, if you click on the first link of a Wikipedia page (following a few rules) and keep doing that, you will probably end up on the Philosophy page or in a loop.
> So I scraped many links (the blue words) and, with the help of Neo4J, stored and queried them.

Click here to see the [Github Repo](https://github.com/salomaoalves/random/tree/main/Wiki1Link) with more technical information *it has a README*.

The project is an application, started from **main.py**, that runs all of this functionality. It can be divided into 5 parts: Custom Ingestion, Auto Ingestion, View Paths, Summary and Graph Display. From the main script, you can call the web scraping functions to gather data *Custom/Auto Ingestion*, get graph and node information *View Paths and Summary*, and view the graph *Graph Display*.

<figure style="margin: 0;">
  <img src="/img/wiki1link-home.png" alt="Wikipedia first-link graph" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Home page</figcaption>
</figure>


## Tools
### Web Scraping
Used to gather the data from Wikipedia pages. First, **ETL/connection.py** uses the **Selenium** library to connect to a browser (Firefox or Chrome) and get the page source, the HTML of the Wikipedia page; if a connection error happens 3 times, the page is saved to a CSV file.

**ETL/extractWords.py** and **ETL/autoWords.py** are responsible for getting the wiki page source (by calling the *connection.py* functions) and extracting the words from the HTML. For that, I use the **BeautifulSoup** library to extract blocks of words/paragraphs (with functions like *find_all()* and *find()*) and the **re** library *Regular Expressions* to search the paragraphs, apply the rules and extract the correct word. In fact, *autoWords.main()* only collects different starting words, each of which is passed to *extractWords.main()*, which builds the graph starting from that word.

<figure style="margin: 0;">
  <img src="/img/wiki1link-webscraping.png" alt="Wikipedia first-link graph" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">One of the web scraping processes</figcaption>
</figure>

### Neo4J / Cypher
All the related functions are in **ETL/neo4jFunc.py**. They use the Cypher language to get nodes, paths and loops, insert pairs of nodes to build the graph, and delete nodes. There are two functions for each action: the main one, which creates the session, and an auxiliary one, where Cypher is used to work with the data.

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
The project is made up of the following folders and files:
 - **ETL** *folder* contains the Python code responsible for scraping the data from Wikipedia and the Neo4J functions that work with the data
 - **common** *Python file* with common functions used across many files
 - **createFakeData** *Python script* responsible for creating and storing the fake data used for testing
 - **graph_visu** *Python file* with functions that display the graph, using the **NetworkX** library
 - **ingestion** *Python file* responsible for collecting the data and building/ingesting the graph, always starting from a word. It has two main functions: (1) `auto_ingestion()`, which starts with random words, and (2) `costum_ingestion()`, which starts with a word you type in
 - **main** the main *Python script*: it creates a nicer prompt in the terminal with a short description of the project and how it works, and from there you can start and control the project
 - **path** *Python file* with functions related to paths: given two words, show the path between them, the path to the word Philosophy, whether a word belongs to a loop, and more
 - **summary** *Python file* with the functions that generate a summary: graph degrees, loops, predecessor/successor nodes and paths between nodes. With Cypher, I was able to read and manipulate the data (filters, aggregations and so on)

<figure style="margin: 0;">
  <img src="/img/wiki1link-summary.png" alt="Wikipedia first-link graph" style="width: 100%;">
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Summary information</figcaption>
</figure>

All the files have comments, so you can understand how they work, and the repo has a README with more information.

*Images are AI-generated*