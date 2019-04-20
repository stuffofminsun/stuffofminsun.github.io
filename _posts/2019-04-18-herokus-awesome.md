---
layout: post
title: heroku's awesome
---

It took a few hours, but I managed to launch the <a href="https://minsun-abs.herokuapp.com/">dash visualization</a> up on <a href="https://www.heroku.com">heroku</a> and then spent a few more hours fiddling with very minor look and feel items. Probably took me less than 3 hours total to set up all three graphs, and took the remainder of the time just messing with the axes and legends. Anyway, I'm quite happy with the result - it's something I've always wanted to show but there were no other good ways to produce this visualization in a static format (i.e., a report with a million charts is just a bad idea all around). Pulling it together did confirm what I mostly thought - downgrades/upgrades are concentrated mostly during the great recession time, with the exception of the student loan asset class. But considering how much of the student loan ABS category is actually backed by FFELP loans (and still are despite the program ending in 2010!), the ratings breakdown looks like it was specifically affected by the U.S. sovereign downgrade by Standard and Poor's in 2011. Since the ratings shown are floor ratings, downgrades are far more noticeable in these charts than upgrades, actually.

The data pulled together for this is actually executed from a sql server and spat out into a csv file just so pandas can do its magic, so there's very little munging (really, none) at this point in the process since it's done quite a bit earlier. The ease in which I could execute from data to visualization was so nice I'm inspired. Might start work on a separate but related visualization to this (working on subcategories or LIBOR based items). I learned to use stack/unstack in pandas for this visualization, which is incredibly useful. 

In the meantime I should probably sit down to edit the css file - I'm using the default css that the plotly starts with - so I don't have to be messing so much with css attributes within python script. Reading css or css-ish things embedded in other text always gives me a headache - I ended up breaking the dash debug server over a missing comma 99% of the time.

Now that I'm a lot more comfortable with pandas generally, I very much enjoy working with dataframes now. Combined with the jupyter notebook, it's just incredibly fast to prototype quickly. And it's way more useful in certain things than Excel, although I do like both. The only downside is that I use pycharm as my python editor and pycharm and jupyter don't... really go that well together. I much prefer to launch jupyter off into a browser instead of inside pycharm, and then keep projects in pycharm generally because it plays nicely with Git and everything else about pycharm is really very nice. So nice, in fact, that I'm kind of curious about IntelliJ for Java/Scala (I've previously used Eclipse). But I'm digressing. I guess the only thing I'm still having trouble with with dataframes is when I have to process in chunks or how to deal with python's sort of nonexistent garbage collection, but practice makes perfect...

<iframe src="https://minsun-abs.herokuapp.com/" allowfullscreen="allowfullscreen" width="800" height="800"></iframe>




