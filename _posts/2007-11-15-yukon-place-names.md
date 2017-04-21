---
ID: 47
post_title: Yukon Place Names
author: matt
post_date: 2007-11-15 23:20:11
layout: post
published: true
---
*Canadian geographic placenames board now publishes all their data for free via a variety of formats and services on the <a title="http://gnss.nrcan.gc.ca/index_e.html" href="http://gnss.nrcan.gc.ca/index_e.html" target="_top" rel="external nofollow">Canadian Geographical Names Service (CGNS)</a> (yay!). I decided to try and build a script which could be run once a year or on an as-needed basis to update a Yukon Gazateer. The automation part was a failure, but the data part is okay. What follows are my notes to myself, so I don’t know how much you’ll be able to get out of it.  **— Matt Wilkie*

There are 3,937 placenames in the database. Some are withdrawn or recinded though. You’ll need to consult the user guide and the specifications for what that means ( <a title="http://gnss.nrcan.gc.ca/gnss-srt/GNSS_Users_Guide.pdf" href="http://gnss.nrcan.gc.ca/gnss-srt/GNSS_Users_Guide.pdf" target="_top" rel="external nofollow">GNSS_Users_Guide.pdf</a>, <a title="http://cgns-dev.nrcan.gc.ca/cgns_web/standards_spec.html" href="http://cgns-dev.nrcan.gc.ca/cgns_web/standards_spec.html" target="_top" rel="external nofollow">http://cgns-dev.nrcan.gc.ca/cgns_web/standards_spec.html</a> )

**Yukon_Placenames.shp** is the results of my efforts. It’s pretty much ready to use. Some work remains to be done to substitute the <a title="http://gnss.nrcan.gc.ca/gnss-srt/aboriginalEncoder.jsp?srcForm=searchFrm&srcElement=geoname" href="http://gnss.nrcan.gc.ca/gnss-srt/aboriginalEncoder.jsp?srcForm=searchFrm&srcElement=geoname" target="_top" rel="external nofollow">special characters</a> for labeling. *(See update from 15-nov-2007 at end of page)*

**Original_yk-names.txt** is the original data as downloaded and before cleaning.

**yk-names_cleaned.csv** is the cleaned and now true CSV file.

**yk-geonames_cvs.shp** is the cleaned file converted into a point shapefile.

**yk-geonames_gml.shp** is the output from the Web Feature Server. The CSV and the GML files have the same records but different, and useful, attributes so ideally they should be merged together. That’s a whole ‘nother project though.

**Core_fields.txt** has all the nitty gritty details on the attribute schemas and values.

**The download archive is <a href="http://reboot.yukongis.ca/2007/11/yukon-place-names/yk_placenames_distrib/" rel="attachment wp-att-48">yk_placenames_distrib.zip</a> and about 2mb.**

*If you don’t care what trials and tribulations created this dataset stop reading now*. 🙂

<div id="section_1">
  <h2>
    Update
  </h2>
  
  <p>
    <em>15 November 2007</em>
  </p>
  
  <p>
    We can use <a title="http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=gentium" href="http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=gentium" target="_top" rel="external nofollow">Gentium</a>, Charis & Doulos fonts for the accurate rendering of the native placenames, espcially with this helpful character picker as a selection tool: <a title="http://people.w3.org/rishida/scripts/pickers/latin/" href="http://people.w3.org/rishida/scripts/pickers/latin/" target="_top" rel="external nofollow">http://people.w3.org/rishida/scripts/pickers/latin/</a> <em>Soooo</em> much easier than any other method I’ve seen to find the characters one needs! Characters are shown in order of <strong>visual</strong> similarity. No more constant jumping back and forth from one section to another trying find that special X! (use the special ones a the bottom too, and copy/paste the results!)
  </p>
  
  <p>
    Next task: script to convert geonames {32} codes to the appropriate stacked diacriticals: ǭ̈
  </p>
  
  <p>
     
  </p>
  
  <hr size="2" width="100%" />
</div>

<div id="section_2">
  <h2>
    Ugly Details
  </h2>
  
  <p>
    To download the entire Yukon in CSV format, use this url <a title="http://gnss.nrcan.gc.ca/gnss-srt/api?bbox=-142.0,59.0:-123.0,72&regionCode=60&output=csv" href="http://gnss.nrcan.gc.ca/gnss-srt/api?bbox=-142.0,59.0:-123.0,72&regionCode=60&output=csv" target="_top" rel="external nofollow">http://gnss.nrcan.gc.ca/gnss-srt/api?bbox=-142.0,59.0:-123.0,72&regionCode=60&output=csv</a> (be nice to their server. We don’t need to be getting it more than once or twice a year. Also be patient. It takes about three minutes for the entire file to be sent). Saved as<code>original_yk-names.csv</code>
  </p>
  
  <p>
    Huh. The data is there but not in csv format there are pipe symbols <a href="http://enhanceyourcar.co.uk/exclusive-ep-product-will-launch-modified-live/">By</a> as field delimeters <a href="http://www.uitrick.com/javascript/jquery-stay-on-the-same-accordion-tab-after-window-reloads/">tab</a> (|) and html line breaks for record delimters (<br> ). A fairly simple job for regular expression search and replace if you have a decent text editor. Fixed version: <code>yukon-placenames.csv</code>. I submitted a bug report in July and one the developers responded. I gave some more detail and haven’t heard back. When I checked again this morning CVS output was still broken. Oh, there are data problems too. Things like 105O typed as 105 <em>zero</em>.
  </p>
  
  <p>
    Went looking for a script to easily convert lat/long <a href="http://ccvutrongphung.com/condotel-vinpearl-empire-luong-gio-moi-cho-bds-nghi-duong/">d??ng</a> to utm. Haven’t found an <a title="ArcGIS" href="http://www.yukongis.ca/ArcGIS.html" rel="internal">ArcGIS</a> one yet, but this python library is very easy to use: <a title="http://pygps.org/" href="http://pygps.org/" target="_top" rel="external nofollow">http://pygps.org/</a>. Now I need to figure out how to tell it to get the UTM zone by itself. There’s this one too: <a title="http://starship.python.net/crew/jhauser/Gproj.html" href="http://starship.python.net/crew/jhauser/Gproj.html" target="_top" rel="external nofollow">http://starship.python.net/crew/jhauser/Gproj.html</a>
  </p>
  
  <p>
    What about <a title="oldsite/GDAL" href="http://www.yukongis.ca/Tools/GDAL-OGR.html" rel="internal">GDAL</a>/OGR? <em>asked fwtools mailng list. Answer from Frank Warmerdam:</em>
  </p>
  
  <blockquote>
    <p>
      <em>The OGR Projections Tutorial might be helpful for you, though it mostly</em><br /> <em>addresses stuff from the C++ point of view. <a title="http://www.gdal.org/ogr/osr_tutorial.html_" href="http://www.gdal.org/ogr/osr_tutorial.html_" target="_top" rel="external nofollow">http://www.gdal.org/ogr/osr_tutorial.html_</a></p><p>
        The Python script <a title="http://www.gdal.org/srctree/pymod/samples/tolatlong.py" href="http://www.gdal.org/srctree/pymod/samples/tolatlong.py" target="_top" rel="external nofollow">http://www.gdal.org/srctree/pymod/samples/tolatlong.py</a><br /> _should show a bit of how to use projections stuff in Python. In your</em><br /> <em>case you want to go from lat/long to utm. There is nothing pre-baked</em><br /> <em>in OGR to identify the optimal UTM zone for a given point, but it is</em><br /> <em>relatively easy to find the nearest central meridian since they are all</em><br /> <em>in six degree increments.</em>
      </p>
      
      <p>
        <em>Sorry I don’t have something a bit more specific!</em>
      </p></blockquote>
      
      <p>
        bah humbug. If ArcCatalog starts crashing everytime you start it, before it even finishes drawing the gui, try deleting/renaming <strong><em>%appdata%/ESRI/ArcCatalog/ArcCatalog.gx.</em></strong> Ahhh, there’s a better fix: just rename/move the last opened directory or add a new data file to it. <strong><em>(bug logged, incident #75755)</em></strong>
      </p>
      
      <div id="section_3">
        <h3>
          Code to calc UTMX/Y for a point shapefile loaded in <a title="oldsite/ArcMap" href="http://www.yukongis.ca/oldsite/ArcMap.html" rel="internal">ArcMap</a>.
        </h3>
        
        <p>
          <strong>Procedure:</strong> set data frame coordinate system to desired UTM zone > Select only those points in the Zone (requires point-on-poly overlay with utm_zones poly) > Open Attributes > Select UTM_X column (which is Longitude) > Calc Values > Advanced > paste code block from below > Set Output to equal X or Y depending on which column you are doing. Lather, Rinse, Repeat until done. (courtesy of <a title="http://forums.esri.com/Thread.asp?c=93&f=982&t=54791#135972" href="http://forums.esri.com/Thread.asp?c=93&f=982&t=54791#135972" target="_top" rel="external nofollow">http://forums.esri.com/Thread.asp?c=93&f=982&t=54791#135972</a>)
        </p>
        
        <p>
           
        </p>
        
        <pre>dim pMxDoc as imxdocument
set pMxDoc = thisdocument
dim pMap as IMap
set pMap = pMxDoc.focusmap
dim pGeometry as IGeometry
set pGeometry = [Shape]
pGeometry.Project  <a href="http://littlebuddhalover.com/cultural-corner-january/">(January)</a>  pMap.SpatialReference
dim pPoint as IPoint
set pPoint = pGeometry
X = pPoint.X
Y = pPoint.Y</pre>
      </div>
      
      <div id="section_4">
        <h3>
          code to grab yukon names from the CGNS web feature server:
        </h3>
        
        <p>
          <a title="http://www.cubewerx.com/cwpost/cwpost.cgi?serverUrl=http://cgns-dev.nrcan.gc.ca/cgi-bin/cubeserv.cgi?service=wfs%26datastore=cgns&postBody=Paste%20your%20transaction%20here" href="http://www.cubewerx.com/cwpost/cwpost.cgi?serverUrl=http://cgns-dev.nrcan.gc.ca/cgi-bin/cubeserv.cgi?service=wfs%26datastore=cgns&postBody=Paste%20your%20transaction%20here" target="_top" rel="external nofollow">http://www.cubewerx.com/cwpost/cwpost.cgi?serverUrl=http://cgns-dev.nrcan.gc.ca/cgi-bin/cubeserv.cgi?service=wfs%26datastore=cgns&postBody=Paste%20your%20transaction%20here</a>
        </p>
        
        <p>
          What the heck am I doing trying to convert broken CSV to shape, when they have a server which can spit the same thing out already baked <a href="http://www.newyorkjetsjerseyspop.com">wholesale nba jerseys</a> into a spatial format? This will chop Excel/OpenOffice Calc out of the loop and then we won’t have to fix the broken NTS names (those fine programs like to change <em>105e15</em> into <em>1.05e+15</em>)
        </p>
        
        <pre>&lt;?xml version="1.0" encoding="ISO-8859-1" ?&gt;
&lt;GetFeature srsName="EPSG:4269"&gt;
&lt;Query typeName="GEONAMES"&gt;
&lt;Filter&gt;
&lt;PropertyIsEqualTo&gt;
&lt;PropertyName&gt;REGION_CODE&lt;/PropertyName&gt;
&lt;Literal&gt;60&lt;/Literal&gt;
&lt;/PropertyIsEqualTo&gt;
&lt;/Filter&gt;
&lt;/Query&gt;
&lt;/GetFeature&gt;</pre>
        
        <p>
          The user guide says one can stick <em>output=”SHAPE”</em> in the <em>GetFeature</em> line, but I get an error with that:
        </p>
        
        <pre>&lt;?xml version="1.0" encoding="ISO-8859-1"?&gt;
&lt;ServiceExceptionReport version="1.1.3" xmlns=" http://www.opengis.net/ows "
xmlns:xsi=" http://www.w3.org/2001/XMLSchema-instance "
xsi:schemaLocation=" http://www.opengis.net/ows http://schemas.cubewerx.com/schemas/wms/1.1.3/ServiceExceptionReport.xsd "&gt;
&lt;ServiceException&gt;
CubeSERV-00002: Syntax error detected in XML stream "(stdin)" on line 2 char pos
               46 (raised in function CwXmlScanText_ReadString() of file
               "cw_xmlscan.c" line 2243)
&lt;/ServiceException&gt;
&lt;ServiceException&gt;
CubeSERV-00002: Hit unexpected character #x94 while  <a href="http://www.yukongis.ca/2007/04/backdoor-to-us-seamless-national-elevation-data-2/">Elevation</a>  scanning XML token (raised
               in function CwXmlScanText_ReadString() of file "cw_xmlscan.c"
               line 2200)
&lt;/ServiceException&gt;
&lt;/ServiceExceptionReport&gt;</pre>
        
        <p>
          Oh, that’s why not use WFS. It’s broken (or I’m not using it properly. Okay, spending too much time on that. Go back to kludge-ville and <strong>regex search & replace the NTS names:</strong><br /> open yk_names_25jul2006.dbf in Excel, copy NTS column to Vim (we really should be doing this in python to make it easily repeatable), then:
        </p>
        
        <pre># match 115A08  <a href="http://shareneighborhood.com/czy-wladze-beda-odbierac-ludziom-takze-krowy-w-powiecie-dabrowskim/">w?adze</a>  and delete last trailing two digits
/\(\d\d\d\a\)\d\d/\1/g
# strip MCR130
/mcr130,//g
# fix  <a href="https://www.cheapjerseys4you.com">wholesale nba jerseys</a>  false exponents (delete periods and trailing +0##)
/\.//g
/+\d\d\d//g
# change incorrect 105zerozerozero... to 105o 
/00\+/O/g</pre>
        
        <p>
          Next problem is to merge dupes (105a,105a,105a,105b —> 105a,105b). Hmmm. I think I’ve gone beyond what’s easy in vim, and now there’s no choice but to learn the python way.
        </p>
        
        <p>
          Going back and looking at some of the intermediate WFS request outputs, I see that there is inconsistency in the attributes. This needs a more studied look but the one of immediate relevance is that there is a <em>Relevance At Scale (r_vlaue)</em> field which in the API cvs file is filled with many blanks while the GML output for that field is fully populated. That’s enough to tell me it is foolish to rely on the cvs as <a href="http://www.yukongis.ca/2007/04/backdoor-to-us-seamless-national-elevation-data/">Backdoor</a> an authoritative source, so I’m backing up and going to start from the GML.
        </p>
      </div>
      
      <div id="section_5">
        <h3>
          Try#2 at downloading from Geonames WFS server
        </h3>
        
        <p>
          1. download with wget, using example command line from section 4.3 of the <a title="http://gnss.nrcan.gc.ca/gnss-srt/GNSS_Users_Guide.pdf" href="http://gnss.nrcan.gc.ca/gnss-srt/GNSS_Users_Guide.pdf" target="_top" rel="external nofollow">GNSS User Guide</a>. It failed before because of line length limitations in CMD. Workaround is to save the command into a text file and run with:
        </p>
        
        <pre>wget -O output_file.gml -i http_command.txt</pre>
        
        <p>
          2. We use ogr2ogr to convert GML to shape, but shape has an attribute name length limit. To get the proper attribute names in Arc we need to dance around a little: Use <em>ogrinfo output_file.gml</em> to generate attribute schema<em>(output_file.gfs)</em>, edit .gfs and strip leading “GEONAMES.” from each <Name>. Then convert to shape using <em>ogr2ogr</em> which will generate an empty shapefile with <a href="http://www.dallascowboysjerseyspop.com">cheap mlb jerseys</a> the correct headings. <em>.</em> Edit the .dbf file with Excel and <a href="http://www.cheapjerseyslan.com">cheap mlb jerseys</a> copy the column headings. Undo the edits to .gfs (or delete it all together), and convert again to shape. Open the second .dbf in Excel and copy the proper field headings, save and exit.
        </p>
        
        <pre>ogrinfo yk_names.gml
vim yk_names.gfs # :%s/GEONAMES\.//g; save
ogr2ogr -a_srs EPSG:4269 yk_names yk_names.gml
# excel yk_names/geonames.dbf; copy 1st row; close dbf
del yk_names.gfs
ogr2ogr -a_srs EPSG:4269 yk_names/ yk_names.gml
# excel yk_names/geonames.dbf; paste 1st row; close dbf</pre>
        
        <p>
          <em>and that’s all for now folks!</em>
        </p>
        
        <address>
          <a title="mailto:Matt.Wilkie@gov.yk.ca" href="mailto:Matt.Wilkie@gov.yk.ca" target="_blank" rel="external nofollow">Matt.Wilkie@gov.yk.ca</a></p><p>
            Geographic Information,<br /> Information Management and Technology,<br /> Yukon Department of Environment<br /> 10 Burns Road * Whitehorse, Yukon * Y1A 4Y9<br /> 867-667-8133 Tel * 867-393-7003 Fax<br /> <a title="http://environmentyukon.gov.yk.ca/geomatics/" href="http://environmentyukon.gov.yk.ca/geomatics/" target="_blank" rel="external nofollow">http://environmentyukon.gov.yk.ca/geomatics/</a></address> </div> </div>