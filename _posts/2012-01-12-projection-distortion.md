---
ID: 23
post_title: Projection Distortion
author: matt
post_date: 2012-01-12T08:03:30.000Z
layout: post
published: true
title: Projection Distortion
---
Each of the red blobs in the map below would,  on a globe or in the real world, occupy the same amount of space (area) and be the same shape (a circle).

_Tissot error elipses on an unprojected lat-long world map_
![tissot-on-latlong.png]({{site.baseurl}}/media/tissot-on-latlong.png) 

https://github.com/maphew/code/tree/master/gis/misc/tissot : contains a tissot shapefile in geographic decimal degrees you can load into your gis to demonstrate distortion in whatever projection you like. A really useful enhancement would be to change **generate_tissot-py** to generate more and smaller tissot circles for smaller localised projections like UTM. _[hint hint]_ The script and graphic is courtesy of Matt Perry in "[Examining the distortion of map projections][1]", which has more examples and explanation.

[1]: http://www.perrygeo.com/tissot-indicatrix-examining-the-distortion-of-map-projections.html
