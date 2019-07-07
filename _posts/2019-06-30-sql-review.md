---
layout: post
title: sql review
---

Things got a bit busy at work (it's quarter-end, so a lot of data related stuff has to be done). Have a preliminary database schema set up to migrate an old access database to sql server, but want to review it sometime in July before building it out. 

Last week I was working on something very (very) small in AWS Redshift and learned that it's based on Postgres 8 so... it turns out you can't use things like generate_series. Or, well, you can... sort of... but it can't be joined to tables so... yeah. That experience made me want to do a quick review of SQL so ran through some Vertabelo exercises, specifically the ones specific to sql server and postgres. I use a fair amount of sql at work, but 99% of my everyday stuff is really basic (select * from x inner join y where z) and the few that are complicated I put together ages ago and saved. I guess if I have free time I can practice some more by refactoring them since they were built out hodge podge style and could really use a review. 
