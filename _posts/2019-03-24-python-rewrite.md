---
layout: post
title: Rewriting
categories: [python]
---

[Github link](https://github.com/stuffofminsun/CongressMapping)

As alluded to earlier, I recently decided to pick up python, mostly to try it out for data science related items, but also partly as an excuse to consolidate a lot of random code snippets I wrote over the years for this or that minor project at work. I went through Cousera's Python Basics, which covers a lot of the basic syntax, and then rewrote a script I did in Java that, given a set of latitude/longitude points, would look through Census' shapefiles and return either congressional district, state upper legislative district, or state lower legislative district. Special attention would have to be paid to US territories, however, (e.g., Puerto Rico, Virgin Islands, Northern Marinara Islands, Guam, and American Samoa) as I had addresses within those territories and would include them in the US total, but these might not necessarily have a congressional district, state lower district, or state upper district.

It was an extremely fast rewrite, as python has shapely and pyshp, which worked really well, but the downside was that it was insanely slow. The same script in Java that I wrote, which used essentially the same basic algorithm, ran much faster: I could go through 150,000 entries in less than 20 minutes, probably less if I didn't print out the status of the lookup to the console. The same list in python took over a day. While Java mostly runs faster than python, the difference was so large it was probably related to a really expensive operation I thoughtlessly wrote in, so I decided to try to trim runtime. 

Sometime after, I finished most of the rest of the python 3 specialization in Cousera, which gave me a lot more ammo to work with that I didn't have initially, so I set out rewriting. It also helped that it covered the basics to python style classes and methods, so instead of three scripts, I reorganized a bit and consolidated into one main class that 3 others inherit most methods from. I miss Java's multiple constructors, but I guess python overcomes that with some other neat features.

First: congressional districts. There are 435 of them, plus the delegate, non-voting territories, which come out to 444 entries for the 116th Congress in the shapefile. My initial sloppy runthrough had me iterating through the entire shape list to determine if a coordinate was within a shape, which meant a worst case scenario for 100,000 points would mean 44,400,000 lookups. It's even worse for the upper and lower houses of the state: there are 1,961 shapes for state upper houses, and 4,833 shapes for state lower houses. 

So I added another shape load and lookup prior to the congressional district/state upper/state lower house lookup: a state lookup. If I could minimize lookups of the state subdistricts to just a specific state, the upper bounds drop substantially. I rewrote the subdistricts into a dictionary, with the key-value pair as state-list of subdistrict shapes, to reduce the operation of getting a list of subdistrict shapes for a state down to O(1). This also had the added benefit of dealing, very early on, with those states/territories that might not have a district, state lower, or state upper house: if I identified such a state, any further lookup of subdistricts were not needed since I could handle them separately.

<table style="border: 1px solid black;">
	<tr style="border: 1px solid black;"><td style="border: 1px solid black;"></td><td style="border: 1px solid black;">States</td><td style="border: 1px solid black;">Congressional Districts</td><td style="border: 1px solid black;">State Lower</td><td style="border: 1px solid black;">State Upper</td></tr>
	<tr style="border: 1px solid black;"><td style="border: 1px solid black;">States and Territories</td><td style="border: 1px solid black;">56</td><td style="border: 1px solid black;">56</td><td style="border: 1px solid black;">50</td><td style="border: 1px solid black;">52</td></tr>
	<tr style="border: 1px solid black;"><td style="border: 1px solid black;">Number of Subdistricts per State</td><td style="border: 1px solid black;">N/A</td><td style="border: 1px solid black;">1 ("at large") to 53</td><td style="border: 1px solid black;">30 to 203</td><td style="border: 1px solid black;">8 to 67</td></tr>
</table>

So in the example of congressional districts, the worst case lookup would be if the coordinate was in the last state/territory (56 lookups) + last district (53 if California was the last state), or 109 per entry, down from 444.

There are fewer states listed in the state lower house shapefile mostly because state lower houses don't exist for a handful of states and territories (DC and Nebraska being the most notable). This would bring worst case lookup down to 253 lookups per entry (50 + 203) from 4,833. The state upper house has 2 more states in its file (said DC and Nebraska), which bring worst case lookups to 119 (52 + 67) per entry from 1,961.

This also reduces lookups of non-US coordinates to a fixed 56 state & territory lookups instead of maxing out with the entire shapelist (iterating through the entire list of subdistricts). If I worked with a great deal more non-US addresses, I might've added a third shape lookup (the entire US shape) before the state lookup to further reduce foreign lookups. Other ways to further trim lookups would be maybe broadly dividing the states into a latitude or longitude set of buckets, although I'm not sure how I could trim through subdistrict buckets since subdistrict shapes can be quite irregular.

What do I still have left to do? I need to implement a method that pulls all three lookups - congressional district, lower district, and upper district - at once, as well as some more robust documentation, since whatever javadoc's equivalent to python wasn't covered in any the course specialization and I'd like to add that in. 