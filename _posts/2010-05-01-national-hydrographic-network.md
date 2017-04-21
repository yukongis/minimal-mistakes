---
ID: 41
post_title: National Hydrographic Network
author: matt
post_date: 2010-05-01 23:00:51
layout: post
published: true
---
[caption id="attachment_42" align="alignright" width="300"][<img class="size-medium wp-image-42" alt="NHN with waterbodies and stream network directions showing" src="http://reboot.yukongis.ca/wp-content/uploads/2013/12/nhn-300x231.jpg" width="300" height="231" />][1] NHN with waterbodies and stream network directions showing[/caption] The authoritative NHN homepage is on <a title="http://geobase.ca/geobase/en/data/nhn/index.html" href="http://geobase.ca/geobase/en/data/nhn/index.html" target="_blank" rel="external nofollow">geobase.ca</a> As of spring 2010 it is distributed in shape, kml, gml, and file geodatabase formats. Direct download address is <a title="ftp://ftp2.cits.rncan.gc.ca/pub/geobase/official/nhn_rhn/" href="ftp://ftp2.cits.rncan.gc.ca/pub/geobase/official/nhn_rhn/" target="_blank" rel="external nofollow">ftp://ftp2.cits.rncan.gc.ca/pub/geob...icial/nhn_rhn/</a>, which is throttled to a maximum of 2 connections per ip address. Http to same is not throttled, however date stamps are not retained then (and it's a little harder to bulk download). Attached is a <a title="http://www.filezilla.org/" href="http://www.filezilla.org/" target="_blank" rel="external nofollow">Filezilla </a>download queue for zones 08,09&10 (BC, Yukon, western NWT) in file geodatabase which adds up to about 12gb or so. <p style="padding-left: 30px;">
  <a href="http://reboot.yukongis.ca/2010/05/national-hydrographic-network/nhn_file-gdb_download_queue-xml/" rel="attachment wp-att-44">NHN_file-gdb_download_queue.xml</a>
</p>

<div id="section_1">
  <h3>
    NHN mxd
  </h3>
  
  <a title="http://www.geobase.ca/geobase/en/data/nhn/utilisation.html" href="http://www.geobase.ca/geobase/en/data/nhn/utilisation.html" target="_blank" rel="external nofollow">They supply an Arcmap .mxd</a> to use with the GDBs, though the links are broken. It is faster to use ArcCatalog <em>"select > r-click > set data sources"</em> instead of opening the .mxd and repairing from there as the docs suggest. Unfortunately this doesn't fix the Event layers which must be repaired one by one. Also unfortunate is that the networks in the gdb's prevent merging the geodatabases together. It looks like I might be better off sticking to downloading and <a title="http://code.google.com/p/maphew/source/browse/trunk/gis/canvec/gml2shp.bat" href="http://code.google.com/p/maphew/source/browse/trunk/gis/canvec/gml2shp.bat" target="_blank" rel="external nofollow">merging the gml files with ogr2ogr</a>, rebuilding the network later in arcgis. Time will tell, I'm not eager to download yet another 12gb until I've worked the process out. :) <a href="http://reboot.yukongis.ca/wp-content/uploads/2013/12/nhn-broken-event-tables.jpg"><img class="alignright size-full wp-image-43" alt="NHN broken event tables" src="http://reboot.yukongis.ca/wp-content/uploads/2013/12/nhn-broken-event-tables.jpg" width="439" height="162" /></a>hmmm. There's more work yet to fix the composition. Flipping to the [source] tab reveals that the Event layers are linked to English-name tables (NHN prefix), but the tables saved in the .mxd are en francais (RHN prefix). I really <em>really </em>wish ESRI used <a title="http://www.cubewerx.com/bxml" href="http://www.cubewerx.com/bxml" target="_blank" rel="external nofollow">binary xml</a> for their project storage format instead of whatever system they've cooked up. At least then we'd be able to fix things like this using tried and true regex with a decent text editor. Arghh. <div id="section_2">
    <h4>
      Let's try <a title="http://arcscripts.esri.com/details.asp?dbid=14456" href="http://arcscripts.esri.com/details.asp?dbid=14456" target="_blank" rel="external nofollow">Arcmap MXD Redirect Data Sources</a>.
    </h4> Win7 install: run Arcmap as administrator when registering the .dll, then exit and run normally. Hrmm. Interactive repair did nothing. Search and replace does better than ArcCatalog's same, in so far as it actually replaced all references, however neither tool fixed the broken event layers. I also tried renaming the english tables to match the french format expected, no change. It's curious that the RHN tables are shown in the [source] tab, yet the event layer properties reference the english tables.
  </div>
</div>

 [1]: http://reboot.yukongis.ca/wp-content/uploads/2013/12/nhn.jpg