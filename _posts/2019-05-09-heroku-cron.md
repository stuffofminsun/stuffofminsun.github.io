---
layout: post
title: heroku-cron
---

Finally finished everything related to the <a href="https://minsun-agencytrading.herokuapp.com/">dash visualization for agency mortgage-backed securities trading</a>. Wrote a fairly quick scraper that would grab the most recent 2 months of data, extract them, and then upload them to the DynamoDB database, and then set up Heroku to execute the cron job with apscheduler/redis to perform on the fifth of every month. I initially wanted to use Heroku's scheduler add on, but reaalized I needed something slightly more complex to run (fifth of every month). Heroku's <a href="https://devcenter.heroku.com/articles/clock-processes-python">guide</a> is pretty straightforward, and you can pretty much use it right out of the box; just fill as necessary.

I made the entire <a href="https://github.com/stuffofminsun/FINRA-ABS">git</a> public. This was a proof of concept that I had in mind and I was happy to be able to execute and learn so many new things out of it. 