---
layout:       post
title:        "Google Calendar"
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

> A Report and Web Dashboard of your life, or at least of as much of it as you are willing to track in Google Calendar.

Click here to see the [Github Repo](https://github.com/salomaoalves/DataScience_Visualization/tree/main/GCalendar) with more technical information *it has a README*.


This project ~~which can be divided into two parts~~ aims to show ~~in two different ways~~ the events from a **Google Calendar** account.

The Google Calendar events need to follow a color pattern. Since I built it for my personal account, two patterns were created, or almost two. For dates before 2022 ~~from 2018 to 2021, to be exact~~ a one-off report was made; you can see more about it in `Report|2018-21` and `report_specifYear.py`. That was the "first" part. The other part uses the other files and folders, and covers events from 2022 onwards.

In short, the code you can use with your own Google Calendar is every file and folder except `Report|2018-21` and `report_specifYear.py` *and one more*. IMPORTANT: remember to check the color patterns for the events; they are extremely important.

You can visualize your events in two ways, with a **Report** or a **Dashboard**.

All the code was developed in Python, the plots with Plotly, and the data comes from the Google Calendar API.

## Report
To create a report, call the `get_report()` function from `report.py`, which takes the data *(from `modConstants`)* and starts building the report. The function works like a script: each **step/code block** builds a part of the report and appends it to the previous ones.

In each **code block**, some *statistic* or *metric* (an *aggregation*) is extracted and added to the report structure. The report can be a txt or an HTML file; with HTML, you can also use an email function (in the same file) to send the report by email.

<figure style="margin: 0;">
  <div style="display: flex; gap: 12px; flex-wrap: wrap;">
    <img src="/img/GCalender-report01.png" alt="GCalendar report – part 1" style="flex: 1; min-width: 280px; max-width: 100%;">
    <img src="/img/GCalender-report02.png" alt="GCalendar report – part 2" style="flex: 1; min-width: 280px; max-width: 100%;">
  </div>
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Google Calendar Report - fake data</figcaption>
</figure>

## Web Dashboard
To create a dashboard, run the `dashboard.py` file, which takes the data *(from `modConstants`)* and builds the dashboard: it prepares the data, creates the initial/general charts and builds the web pages (a main one plus one for each event type). The `Visu` folder has the functions used by this file.

The dashboard is built as HTML files (so it can be sent by email or uploaded to a server). The charts are built with Plotly and then converted into HTML code with Plotly Offline. This conversion happens as each chart (bar, table, line) is built, in `Visu/build.py`; at the end of each function, the plot is exported to a given HTML file.

`Visu/create_html.py` has the functions that build the HTML code of the dashboard web pages, placing each chart's HTML code (read from the previously exported file) in the right place and format.

The other files in `Visu` create the charts used on each web page.

<figure style="margin: 0;">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 12px;">
    <img src="/img/GCalender-dash01.png" alt="Google Calendar web dashboard – view 1" style="width: 100%;">
    <img src="/img/GCalender-dash02.png" alt="Google Calendar web dashboard – view 2" style="width: 100%;">
    <img src="/img/GCalender-dash03.png" alt="Google Calendar web dashboard – view 3" style="width: 100%;">
    <img src="/img/GCalender-dash04.png" alt="Google Calendar web dashboard – view 4" style="width: 100%;">
  </div>
  <figcaption style="text-align: center; font-size: 0.9em; margin-top: 6px;">Google Calendar Web Dashboard - fake data</figcaption>
</figure>

*Images are AI-generated*