## Spoken languages

- **Portuguese**: native
- **English**: professional working proficiency

<!-- TODO(Salomao): add Spanish here with your level if you want it listed (the Languages repo has Spanish study notes, but the site does not state a level). -->

## Programming languages

At work I have mostly used **ECL**, **Python** and **SQL**. The rest of this page describes my [Languages repo on GitHub](https://github.com/salomaoalves/Languages), where I keep study notes on the programming languages I have learned or explored.

The repo is a work in progress, and some files go deeper than others, depending on the goal of the study. Languages with their own folder (Julia, Python and R) have the most detailed notes.

In the root there are two `.md` files with the basics of [**GoLang**](https://github.com/salomaoalves/Languages/blob/main/GoLang.md) and [**Octave**](https://github.com/salomaoalves/Languages/blob/main/Octave.md). I find both interesting, but they are not widely used in the data field, so I only covered the first steps. There is also a `test.mojo` file with early notes on **Mojo**, a newer language.

Besides the language folders, `img` holds the images used in some files, and `Human` has notes on spoken languages: grammar and tricky words in [**English**](https://github.com/salomaoalves/Languages/blob/main/Human/english.md) and [**Spanish**](https://github.com/salomaoalves/Languages/blob/main/Human/espanol.md).

## [Julia](https://github.com/salomaoalves/Languages/tree/main/Julia)
 > A high-level, general-purpose dynamic programming language, most commonly used for numerical analysis and computational science

A fast compiled language like C, but with a wide range of features borrowed from languages like Lisp, Python, Ruby, R and Matlab. It uses LLVM (Low Level Virtual Machine) to compile programs down to machine code.

Inside, you can find a `data` folder where the data used by the Jupyter notebooks is stored. The `.ipynb` files contain the language knowledge.

[**AI_ML.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Julia/AI_ML.ipynb)\
Here you can find how to run some Artificial Intelligence and/or Machine Learning algorithms and methods, like Dimensionality Reduction, Label Encoder, AUC and Confusion Matrix, Clustering, Classification and Regression.

[**Base.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Julia/Base.ipynb)\
The language basics: operators, how to install and use packages, data types, data structures, loops, functions, constructors and macros. With this, you can already build some applications, solve computing problems and start learning the language. This is ground zero for beginners.

[**Dataframe.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Julia/Dataframe.ipynb)\
A bunch of functions, methods and tricks to deal with data in a DataFrame format. You can find how to read one *in more than one way*, apply filters, select rows, join, rename columns/rows, get data details, transform and group by, sort, handle missing values and so on.\
Basically, things that are useful when you want to perform operations on the data, e.g., when you are processing or cleaning it.

[**LoadData.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Julia/LoadData.ipynb)\
Data can come in various formats; here you can find how to read and write data in many of them.\
Some of the formats are: Arrow, Txt, Delimited, CSV, XLSX, JLD, NPZ, RDA and MAT.

[**Math.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Julia/Math.ipynb)\
More math functions and methods, like Statistics *distributions* and Linear Algebra.

[**Visualization.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Julia/Visualization.ipynb)\
Plotting data is always important; here you can find more about how to do it.


## [Python](https://github.com/salomaoalves/Languages/tree/main/Python)
 > A high-level, general-purpose programming language. Its design philosophy emphasizes code readability with the use of significant indentation.

Dynamically typed, interpreted and garbage-collected, it supports multiple programming paradigms, like procedural, object-oriented and functional programming.

Inside, you can find a `data` folder where the data used in the files *with code explanations* is stored. The `.ipynb` files contain the language knowledge.

[**Base.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/Base.ipynb)\
The language basics, ground zero for beginners. Here you can find how to create variables, operators, data types, data collections *lists, dicts, sets*, control structures *IFs, loops, error handling*, function definitions, object-oriented programming and how to open and edit files.

[**CustomFunc.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/CustomFunc.ipynb)\
Python functions that I wrote myself and that can be useful in future projects, like sending an email or an SMS.

[**Database.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/Database.ipynb)\
If you want to work with data, you need to deal with databases. Here is some code showing how to use the following database services: SQLite -- MySQL -- PostgreSQL -- AWS RDS -- BigQuery -- MongoDB -- Neo4J.\
In general, you'll find how to connect to the database, run SQL queries and other things.

[**DataScienceCode.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/DataScienceCode.ipynb)\
Pieces of code that can be useful in a data science project, like preprocessing the data (removing outliers/missing values or label encoding), or functions that help explore the data (looking at distributions, pivot tables, summarizing data information).\
Also, in *Free Code*, you'll find pieces of code that are useful when dealing with data, like dates, filters...

[**libsPython.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/libsPython.ipynb)\
One of the good things about Python is the number of libraries available; here you can find more about some of them. At the beginning of the file, there is a list of all the libraries I've gathered some knowledge about.

[**ML&AI.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/ML%26AI.ipynb)\
Methods related to Machine Learning and Artificial Intelligence: how to deal with under- or oversampling of a target feature, how to do feature engineering and selection, some ML algorithms *Association Rules, Classification/Regression, Model Interpretation* and neural network methods.

[**Others.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/Others.ipynb)\
Knowledge about other topics, still in early stages. It may hold many topics, or none; if a topic grows big, it's better to give it its own Jupyter file.

[**Statistics.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/Statistics.ipynb)\
Statistics functions and methods live here: functions to deal with qualitative and quantitative data, correlation/association, sampling functions, statistical tests, and examples of distributions and how to use them.

[**Visualization.ipynb**](https://github.com/salomaoalves/Languages/blob/main/Python/Visualization.ipynb)\
Plotting data is important, and Python is good at it. Here you'll find examples of how to build a bunch of plots using libraries like Matplotlib, Seaborn and Plotly.\
Also, how to build a dashboard using Plotly, and general functions that help set up the whole plotting environment.


## [R](https://github.com/salomaoalves/Languages/tree/main/R)
 > An open-source programming language for statistical computing and graphics, supported by the R Core Team and the R Foundation for Statistical Computing

It is written primarily in C, Fortran and R itself (partially self-hosting) and has a command-line interface.\
Precompiled executables are provided for various operating systems, and multiple third-party graphical user interfaces are also available, such as RStudio and Jupyter.

First, you'll see two `.pdf` files, both *cheat sheets*, very useful when dealing with the [*Dplyr*](https://github.com/salomaoalves/Languages/blob/main/R/R-Dplyr-CheatSheet.pdf) or [*GGPlot2*](https://github.com/salomaoalves/Languages/blob/main/R/R-GGPlot2-CheatSheet.pdf) packages. Then, three `.md` files with the language knowledge.

[**R.md**](https://github.com/salomaoalves/Languages/blob/main/R/R.md)\
The basics, ground zero for beginners in R. Here you can find more about how to use markdown within R, built-in functions, data types, operators, OOP, structures, packages *dplyr, tidyr, ...* and how to plot.

[**RDataScience.md**](https://github.com/salomaoalves/Languages/blob/main/R/RDataScience.md)\
Functions and methods related to some steps of a DS project. You can find ways to clean the data, calculate correlation, select features, split data and run machine learning *with data in a dataframe format*.

[**RStatistics.md**](https://github.com/salomaoalves/Languages/blob/main/R/RStatistics.md)\
Statistics functions and methods live here: functions to deal with qualitative and quantitative data, correlation, combinatorial and sampling functions, examples of distributions and how to use them, statistical tests and multivariate analysis methods.