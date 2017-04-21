---
ID: 34
post_title: Backdoor to US Seamless National Elevation Data
author: matt
post_date: 2007-04-03 22:45:10
layout: post
published: true
---
<div>
  <div id="page-top">
    <div id="pageText">
      <p>
        I recently needed to acquire a large swath of elevation data for Alaska. After fighting through the web map request interface for <a title="http://seamless.usgs.gov/" href="http://seamless.usgs.gov/" target="_blank" rel="external nofollow">Seamless NED </a>for several hours, I finally discovered that one can go straight to the extractor service and request arbitrary areas with a properly formed URL.
      </p>
      
      <p>
        To bypass the map viewer put the coords on the URL like so:
      </p>
      
      <pre>http://extract.cr.usgs.gov/Website/distreq/RequestSummary.jsp?AL=71.0,56.0,-140.0,-150.0&PL=NAK01HZ</pre>
      
      <p>
        where this is your region of interest <em>north,south </em>and <em>east,west</em> in decimal degrees.
      </p>
      
      <p>
        <code>AL=71.0,56.0,-140.0,-150.0</code>
      </p>
      
      <p>
        and this is <a href="http://www.wholesaleijerseys.com">wholesale mlb jerseys</a> data set to choose from, in this case “National Elevation Dataset Alaska (NED) 2 Arc Second”
      </p>
      
      <p>
        <code>PL=NAK01HZ</code>
      </p>
      
      <p>
        This example will return with “<em>You have requested an estimated <strong>1,950</strong> MB of data. The maximum currently allowed is<strong>1,500</strong> MB.” </em>So modify the extents until within limits. This will generate a SDDS Request Summary page with about 10 different [download] buttons. We don’t care about that, we’re just want to know when our area of interest is small enough to work. Keep this page open for reference, we may need some info from it later. Use the <a title="http://chrispederick.com/work/webdeveloper/" href="http://chrispederick.com/work/webdeveloper/" target="_blank" rel="external nofollow">Firefox Web Developer </a>extension and convert the POST form to GET, slap one of the [download] buttons and in the resultant window we have a URL which can be easily modified (must be all on one line to work):
      </p>
      
      <p>
        <code>http://extract.cr.usgs.gov/diststatus/servlet/gov.usgs.edc.RequestStatus</code><code>&lt;br />
?siz=87&lt;br />
&key=NAK&lt;br />
&ras=1&lt;br />
&rsp=1&lt;br />
&pfm=ArcGRID&lt;br />
&imsurl=-1&lt;br />
&ms=-1&lt;br />
&att=-1&lt;br />
&lay=-1&lt;br />
&fid=-1&lt;br />
&dlpre=&lt;br />
&wmd=1&lt;br />
&mur=http%3A%2F%2Fextract.cr.usgs.gov%2Fdistmeta%2Fservlet%2Fgov.usgs.edc.MetaBuilder&lt;br />
&mcd=NED&lt;br />
&mdf=HTML&lt;br />
&arc=ZIP&lt;br />
&sde=ned.ak_ned&lt;br />
&msd=NED.CONUS_NED_METADATA&lt;br />
&zun=METERS&lt;br />
&prj=0&lt;br />
&csx=5.55555555556E-4&lt;br />
&csy=5.55555555556E-4&lt;br />
&bnd=&lt;br />
&bndnm=&lt;br />
&RC=d9b131a2a5e3589013aaddb1d5f567585db594&lt;br />
&lft=-148.33333333333334&lt;br />
&rgt=-146.66666666666669&lt;br />
&top=63.0&lt;br />
&bot=59.0</code>
      </p>
      
      <p>
        For my purposes, it’s these last four which are useful. Change them like so
      </p>
      
      <p>
        <code>&lft=-143&rgt=-140&top=71.0&bot=59.0</code>
      </p>
      
      <p>
        and then each in turn
      </p>
      
      <p>
        <code>&lft=-147&rgt=-143&top=71.0&bot=59.0&lt;br />
&lft=-150&rgt=-147&top=71.0&bot=59.0</code>
      </p>
      
      <p>
        and I have my whole area of interest in three simple requests, plus there is no need go through the bother of mosaicking a <a href="http://mhero.uk/aurora-greenmen-football-player-paul-mcghee-dies-one-day-before-state-semifinals/">Mcghee</a> bunch of little tiles together. It does take the server about 15 or 20 minutes to process each request though. <a href="http://www.legdpl.com/le-blogue-de-pierre/bonjour-tout-le-monde">du</a> I didn’t attempt to find the maximum area, as my main <a href="http://useventdirectory.com/wp-content/themes/Directory/images/tmp/1484875465_67731.pdf"></a> goal is to get the data, not find the limits of their server and crash <a href="http://www.cheapjerseysa.com">cheap jerseys</a> it.
      </p>
      
      <p>
        <strong>If you use this technique, please be gentle</strong>. It’s not in our interests to force them to take protective measures and close this avenue.
      </p>
      
      <p>
        Further exploration: I suspect many of the parameters can be omitted, <em>siz </em>for example which has no apparent effect (my downloads were 350mb each) and I bet the -1 values mean “use the default”. I’m curious about <em>RC</em> which likes a unique session id or cookie or something. I had no problem using the same number every time, but I did do it all in one browser session.
      </p>
      
      <p>
        Many thanks to Joe H. and John Thull on the QGIS-user mailing list for bumping me in the right direction (<a title="http://www.nabble.com/-offtopic--acquiring-Alaska-data-t3370917.html" href="http://www.nabble.com/-offtopic--acquiring-Alaska-data-t3370917.html" target="_blank" rel="external nofollow">[offtopic] acquiring Alaska data)</a>, Chris Pederick for the web developer extension, and course the USGS for having data interesting enough to go through <a href="http://www.cheapujerseys.com">cheap jerseys</a> all this work in the first place!
      </p>
      
      <p>
        <em><strong>UPDATE:</strong></em>
      </p>
      
      <p>
        With regard to ordering the regional CD’s:
      </p>
      
      <p>
        <em>“You can order the entire U.S. in 30 meter resolution in either<br /> ArcGrid or GridFloat format. The data will be provided on a 250 GB<br /> external drive at a total price of $1005.00. This includes shipping<br /> and handling. This will cover the Conterminous U.S., Alaska (at 60<br /> meter res), Hawaii, and <a href="http://autoakkumulatorfutar.hu/033917/816573445.html">wholesale</a> the territorial islands. We no longer provide<br /> this on CD or DVD media.”</em>
      </p>
      
      <p>
        An incredibly good price in my opinion.
      </p>
      
      <p>
        The contact address is <a title="mailto:webmapping@usgs.gov" href="mailto:webmapping@usgs.gov" target="_blank" rel="external nofollow">webmapping@usgs.gov</a>
      </p>
      
      <p>
        Customer Service/Webmapping
      </p>
      
      <p>
        Data and Applications Support Department<br /> Science Applications International Corporation (SAIC) at<br /> U.S. Geological Survey – EROS<br /> (Earth Resources Observation and Science)<br /> 47914 252nd Street<br /> Sioux Falls, SD 57198-0001
      </p>
      
      <p>
        Phone: 1-800-252-4547<br /> Fax: (605)-594-6589
      </p>
      
      <div id="section_1">
        <h3 id="commentz">
          Comments
        </h3>
        
        <ol>
          <li id="comment-41">
            <strong><a href="http://surveying-mapping-gis.blogspot.com/" rel="external nofollow">Dave Smith</a></strong> wrote:<p>
              Thanks for the backdoor tip… I would echo your caveat to not abuse this.
            </p>
            
            <p>
              I too have noticed that seamless.usgs.gov seems to have some serious JavaScript disagreements with IE, which results in tremendously sluggish performance (or worse yet, it just dies altogether).
            </p>
            
            <p>
              When I tried in FireFox, the site worked like a champ.
            </p>
            
            <p>
              Posted 31 Mar 2007 at 10:18 am</li> <li id="comment-43">
                <strong>matt wilkie</strong> wrote:<p>
                  hi Dave, thanks for confirming my IE problems with their <a href="https://www.bcheapjerseys.com">wholesale mlb jerseys</a> site are not local only
                </p>
                
                <p>
                  Posted 03 Apr 2007 at 8:48 am</li> </ol> </div> </div> </div> </div>