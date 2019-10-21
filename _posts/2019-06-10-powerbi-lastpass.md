---
layout: post
title: powerbi/mapbox
---

Built a very quick choropleth in PowerBI; using Mapbox with PowerBI is almost criminally easy. The huge, gigantic downside is that it won't display _at all_ in app/web display if you use the LastPass extension on any of your browsers - and since I _do_, it was literally the first thing I noticed. There is an odd known bug with Mapbox/LastPass/PowerBI, unfortunately, for now. 

Building the visualization cost me about an hour of my life, which made me a little bit sad for my past self - I had built this very same map in Excel (!?) using VBA and a custom SVG shape map (to incorporate the territories) about.... five plus years ago? Cost me almost two days, a lot of it tinkering with color gradients (what kind of bins should I use? What color?) and painstakingly naming every shape in the file. I'm not too big of a fan of using Excel to distribute visualization type data as they almost invariably require macros and most non-Excel-using people never turn them on.

Spent most of the day working out how to implement shapefiles into PowerBI visualizations. It took a while to figure out, but I finally did it. Just need to work on making it pretty. 