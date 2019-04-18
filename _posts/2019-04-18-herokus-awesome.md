---
layout: post
title: heroku's awesome
---

It took a few hours, but I managed to launch the <a href="https://minsun-abs.herokuapp.com/">dash visualization</a> up on <a href="https://www.heroku.com">heroku</a> and then spent a few more hours fiddling with very minor look and feel items. Probably took me less than 3 hours total to set up all three graphs, and took the remainder of the time just messing with the axes and legends. Anyway, I'm quite happy with the result - it's something I've always wanted to show but there were no other good ways to produce this visualization in a static format (i.e., a report with a million charts is just a bad idea all around). The data pulled together for this is actually executed from a sql server and spat out into a csv file just so pandas can do its magic, so there's very little munging (really, none) at this point in the process since it's done quite a bit earlier. The ease in which I could execute from data to visualization was so nice I'm inspired. Might start work on a separate but related visualization to this (working on subcategories or LIBOR based items).

I guess I should sit down to edit the css file - I'm using the default css that the plotly starts with - so I don't have to be messing so much with css attributes within python script. Reading css embedded in other things always gives me a headache - I ended up breaking the dash debug server over a missing comma 99% of the time.

<div style="padding-top: 56.25%;background-color: white;"><iframe src="https://minsun-abs.herokuapp.com/" frameborder=0 allowfullscreen style="width:100%;height:100%;"></iframe></div>




