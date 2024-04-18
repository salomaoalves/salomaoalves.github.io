---
layout:       post
title:        "Google Calender"
author:       "Salomon"
header-style: text
catalog:      true
tags:
    - Python
    - API
    - DataVisualization
    - Plotly
    - Plotly Offline
---

> A Report and Dashboard of your life, at least how much you are willing to track in Google Calender.

Click here to see the [Github Repo](https://github.com/salomaoalves/DataScience_Visualization/tree/main/GCalendar) with more technical information *has readme*.


This project ~~which can me divide in two parts~~ has the goal to show ~~in two differents ways~~ the events from a **Google Calender** account. 

The Google Calender events need to follow a pattern in realted to its colors. Since I was building it to use with my personal account, two patterns was created, or almost two. Look, for date older than 2022 ~~from 2018 to 2021, exactly~~ a random report was made, you can see more about in `Report|2018-21` and `report_specifYear.py` - this was the "first" part. The other part use the others files and folders, and the events are from 2022 onwards.

In short, the code usefull for you to use in your personal Google Calender is every file and folder, except `Report|2018-21` and `report_specifYear.py` *and one more*. IMPORTANT remember to see the colors patterns for the events, they are extremely important.

You can visualize you events in two ways, with a **Report** or a **Dashboard**.

All the code was develop using Python, the plots using Plotly and to get the data the Google Calender API.

## Report
To create a report is called the `get_report()` function from `report.py`, which will take the data *(from `modConstants`)* and start building the report. The function is like a script, where in each **step/code block** a part of the report is done and concatenate with the one before.

During each **code block**, some *statistics* or *metric* - a *aggregation* is extract and put it in the report structure. The structure can be for a txt file or for html file, with the last one, is also possible to use a email function (in the same file) to send the report via email.

## Dashboard
To a dashboard run the `dashboard.py` file, which will take the data *(from `modConstants`)* and start building the dash, by preparing the data, create initial/general graphics and build the web pages (has a main one and subjacents for the events types) - also the folder `Visu` has functions used for this file.

The dashboard is build in html files (so can be send by email or can be upload in a serve) - the graphics are build using Plotly and than transformed into html code with Plotly Offline. This transformation is made during the build of each graphic (bar, table, lines), in `Visu/build.py`; in the end of each function, the plot is export to a given html file.

In `Visu/create_html.py` there are the functions responsible to build the html code - the dashboards webpages with the graphics in right place - and put the graphic html code (will read from the exported file before) in the correct format.  

The others files in `Visu` is used to create the graphics that will be used for each webpage.