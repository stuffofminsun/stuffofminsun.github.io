---
layout: post
title: mapbox
---

Went back to the data viz using mapbox and Dash. For quite a while, I could get the Mapbox map to load in a jupyter notebook just fine, but pop it into the dash framework and it'd break. I got so frustrated that I copy pasted plotly's Dash mapbox example (which also didn't work out of the box, as it turns out) and then replaced it piece by piece with my data until I got it to run to work out where the break was. Turns out it's was a combo of what data and layout used. Also, it seems to be legends don't quite seem to work with mapbox, but at least annotations do. 

The end result is a map that isn't too interesting by itself as it doesn't really tell much of a story once I mapped out the changes by color and actually saw the result. <a href="https://minsun-bd.herokuapp.com/">You can see it here</a>.  But I learned how to work with mapbox, and I can apply it (hopefully) to something else that might show a more interesting result.