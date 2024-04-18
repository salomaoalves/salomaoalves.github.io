---
layout:       post
title:        "Explore & Analysis"
author:       "Salomon"
header-style: text
catalog:      true
tags:
    - Python
    - R
    - DataScience
    - DataVisualization
    - DataExplore
    - DataAnalysis
---

> Here has some projects about explore and analyze data; they're more simple, are just analyze some random data. Each project has a short descriptions and a list of tecniques used.

Here is the main repo with all the projects together [Github Repo](https://github.com/salomaoalves/DataScience_Analysis-Explore).

## [Brazil Governament Spend](https://github.com/salomaoalves/DataScience_Analysis-Explore/tree/main/BrasilGovernamentSpend)
In this project, I clean, transform and explore the Brazil governamental spending during 2016. Developing using R - there is also a RMarkdown file to show the result in a report format.

With R, I read the csv data, did some munging (dataframe columns rename, find n drop na values, create and drops columns, data type transformation, values replace), and the analysis/exploration, which is custom, so can be done in a different way depending on the question or the guy coding. So I will not explain line by line or code block by code block (there comments in the code or you can reach me out for question), I will just list the tools used.

In the analysis, I used basically functions like `summary`, also the dplyr operator `%>%` with some aggregration functions *count(), filter(), group_by(), arrange()*. Plot and customize graphics with the help of the package **ggplot2** - bar, histograms, boxplot, line.


## [Company Financial Health](https://github.com/salomaoalves/DataScience_Analysis-Explore/tree/main/CompanyFinancialHealth)
Here, using R, I explore and analysis a company financial data, calculate some metrics and look closer to some columns. *Proposed by Data Science Academy*

With R, I read the csv data, did some cleaning (format datetime field, remove columns and data normalized), and the analysis/exploration, which is custom, so can be done in a different way depending on the question or the guy coding. So I will not explain line by line or code block by code block (there comments in the code or you can reach me out for question), I will just list the tools used.

In the analysis, I used basically functions like `summary`, plot and customize a sequence of graphic using **ggplot2**. Also some hypothesis tests - Mann-Whitney, Test t, ANOVA.


## [Company Sales](https://github.com/salomaoalves/DataScience_Analysis-Explore/tree/main/CompanySales)
Here I answer 10 question about sales data from a company, by using Python and libs like **pandas**, **numpy** and **matplotlib**. Also, a cleaning to set the columns date correct is done in the begining.

To respond: from the pandas tools, I used `.values_count()`, `.groupby()`, `.sort_values()`, aggregations functions and make some filters; to plot I used the `.plot()` function from matplotlib. 


## [Human Resources](https://github.com/salomaoalves/DataScience_Analysis-Explore/tree/main/HumanResources)
Explore data related with HR, using Python and R. *Proposed by Data Science Academy*

In both language, read the csv data, make some data type transformation and label encoder *- last one only in Python*. Than ... *continues below fore each language*

During the exploration, in Python, I used the **seaborn** lib to plot and customize some graphics (bars, lines, boxplots) and dashboards/figures; also extract information by making pandas filtering and math calculation using **numpy**. Than, with **sklearn**, create a program to extract the best features for a given target using the `SelectkBest` method with `Lasso` model and the errors `mean_squared_error`, `mean_absolute_error`, `median_absolute_error`, `mean_squared_log_error`.

In R, more columns are created to better view the data. After this many graphic are plot and customized using **ggplot2** - bar, density, grid of graphics, boxplot. Also some insigths are extract using R filtering and math functions/operators - and more graphics, of course. In the last, some linear models are created to predict better the target feature, using the `glm` function to create the model, `vif` to calculate the Variance Inflation Factor and `predict` to make predictions