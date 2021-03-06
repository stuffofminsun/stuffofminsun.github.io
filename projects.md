---
layout: page
title: Projects
---

My projects page. Mostly for visualizations and the like. In date order, most recent first.

### 2019-06-10
## <a href="https://app.powerbi.com/view?r=eyJrIjoiMTU2ZDg5NTItYTZiOC00YWRmLWIwMzUtZTU4Yjc0YzljMGU4IiwidCI6ImY1ZGY0YzdmLTA1YjMtNDQzYi04MjZkLTk1YzQxYWFkMTQyYiIsImMiOjN9">State Level Statistics for Broker Dealers and RIAs (mapbox, PowerBI)</a>

A choropleth map with some assorted statistics on the broker-dealer and RIA industry, in PowerBI. Fair warning, this WON'T display in your browser if you use the LastPass extention (which I do) - there is a known bug with Mapbox/PowerBI and LastPass, of all things. 

### 2019-05-30
## <a href="https://minsun-13f.herokuapp.com/">13F Securities Holdings, Last 7 Days (dash/plotly, MongoDB, redis/apscheduler)</a>

A visualization on securities holdings filed by institutional investment managers. Provides data filed in SEC EDGAR from the last days. Discussion located here: <a href="https://www.stuffofminsun.com/2019/05/29/13f-fixes/">Part 1</a>, <a href="https://github.com/stuffofminsun/13F">Git Repository</a>

### 2019-05-28
## <a href="https://minsun-bd.herokuapp.com/">Change in Number of Broker-Dealers in the United States, 2007 - 2018 (dash/plot.ly, Heroku, Mapbox)</a>

A visualization on the changes in the number of broker-dealers headquartered in specific counties. Uses the 2018 Census shapes. Discussion located here: <a href="https://www.stuffofminsun.com/2019/05/24/mapbox-stories/">Part 1</a>, <a href="https://github.com/stuffofminsun/Dash-BD">Git Repository</a>

### 2019-05-02
## <a href="https://minsun-agencytrading.herokuapp.com/">U.S. Agency Trading Volumes and TBA Prices (2019) (dash/plot.ly, Heroku, DynamoDB, apscheduler+redis)</a>

A visualization of the US agency trading market. Also automates extracting the data to DynamoDB through a Heroku cron job once a month. Discussion located here: <a href="https://www.stuffofminsun.com/2019/05/02/etl-pipelines/">Part 1</a>, <a href="https://www.stuffofminsun.com/2019/05/06/dynamodb-heroku-config/">Part 2</a>, <a href="https://www.stuffofminsun.com/2019/05/09/heroku-cron/">Part 3</a>, <a href="https://github.com/stuffofminsun/FINRA-ABS">Git Repository</a>

### 2019-04-22
## <a href="https://minsun-muni.herokuapp.com/">U.S. Municipal Loans Held by Commercial Banks (2000-2018) (dash/plot.ly, Heroku)</a>

A visualization of municipal loans held by U.S. commercial banks, ranked by bank holdings. From the period from 2000 to the end of 2018, quarterly. Some brief additional discussion <a href="https://www.stuffofminsun.com/2019/04/22/more-heroku-more-dash/">here</a>.

### 2019-04-18
## <a href="https://minsun-abs.herokuapp.com/">U.S. Asset Backed Securities Outstanding Visualization (dash/plot.ly, heroku)</a>

A continuation of the work from 4/16/2019, but in visualization form and deployed from heroku. Some brief additional discussion <a href="https://www.stuffofminsun.com/2019/04/18/herokus-awesome/">here</a>.

### 2019-04-16
## <a href="../files/matplotlib_example3.html">Auto ABS Ratings from 2000-2018 (matplotlib, seaborn)</a>

Some more work with matplotlib, this time with matplotlib's (small) interactive widgets. HTML won't allow the interaction, but may come back to this dataset in bokeh or dash for interactivity.

### 2019-04-12
## <a href="../files/matplotlib_example1.html">State GDP and Population Growth, 2013-2017 (matplotlib, seaborn)</a>

Some work with matplotlib and trying out seaborn.