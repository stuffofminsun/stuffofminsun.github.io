---
layout: post
title: etl
---

Was in the middle of the statistics specialization on Coursera - mostly for some review and ease myself into using scipy so have slowed down a bit on other projects. Finished the first part (the visualization aspect) of a project involving FINRA agency mortgage trading data, since it's something I've wanted to do for a while because the data itself is organized in a format absolutely impossible to readily to use for charting, viewing, or much of anything, really. It was especially important to me to be able to pull together some visualization for this data this month since the transition to reporting the single security happened and I wanted to see if I could pull anything interesting out of it. What I have left to do, visualization wise, is mostly for agency CMOs and specified pool prices. 

The cleanup and extraction was only done for 2019 data. Once I'm generally happy with how the data looks, will test further back on a few more years of data and then plan on building an ETL pipeline to store this data and than building a process to have the pipeline and visualization run and update once a month on its own. Basically using this visualization as a test to try out AWS' DynamoDB, among other things. Had been initially wanting to use Heroku's postgres, but a 10,000 line limit on free accounts is pretty small. May try a smaller project instead with heroku's postgres, if I can think of one.

I'm also in the middle of a fairly large scale visualization using maps, but taking more time to think about how it should look, feel, and perform. May just give up and build a chloropeth map for it.

<iframe src="https://minsun-agencytrading.herokuapp.com/" allowfullscreen="allowfullscreen" width="800" height="800"></iframe>