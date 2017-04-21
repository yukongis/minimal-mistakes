---
ID: 94
post_title: Backdoor to US Seamless National Elevation Data (MD)
author: matt
post_date: 2007-04-03 23:37:00
layout: post
published: true
---
I recently needed to acquire a large swath of elevation data for Alaska. After fighting through the web map request interface for [Seamless NED ][1]for several hours, I finally discovered that one can go straight to the extractor service and request arbitrary areas with a properly formed URL.

To bypass the map viewer put the coords on the URL like so:

<span style="font-family: Consolas">http://extract.cr.usgs.gov/Website/distreq/RequestSummary.jsp?AL=71.0,56.0,-140.0,-150.0&PL=NAK01HZ</span>

where this is [cheap NBA jerseys][2] your region of interest *north,south *and *east,west* in decimal degrees.

`AL=71.0,56.0,-140.0,-150.0`

and this is data set to choose from, in this case “National Elevation Dataset Alaska (NED) 2 Arc Second”

`PL=NAK01HZ`

This […][3] example will return with “*You have requested an estimated **1,950** MB of data. The maximum currently allowed is**1,500** MB.” *So modify the extents until within limits. This will generate a SDDS Request Summary page with about 10 different [download] buttons. We don’t care about that, we’re just want to know when our area of interest is small enough to work. Keep this page open for reference, we may need some info from it later. Use the [Firefox Web Developer][4] extension and convert the POST form to GET, slap one of the [download] buttons and in the resultant window we [cheap nfl jerseys][5] have a URL which can be easily modified (must be all on one line to work):

`http://extract.cr.usgs.gov/diststatus/servlet/gov.usgs.edc.RequestStatus``<br />
?siz=87<br />
&key=NAK<br />
&ras=1<br />
&rsp=1<br />
&pfm=ArcGRID<br />
&imsurl=-1<br />
&ms=-1<br />
&att=-1<br />
&lay=-1<br />
&fid=-1<br />
&dlpre=<br />
&wmd=1<br />
&mur=http%3A%2F%2Fextract.cr.usgs.gov%2Fdistmeta%2Fservlet%2Fgov.usgs.edc.MetaBuilder<br />
&mcd=NED<br />
&mdf=HTML<br />
&arc=ZIP<br />
&sde=ned.ak_ned<br />
&msd=NED.CONUS_NED_METADATA<br />
&zun=METERS<br />
&prj=0<br />
&csx=5.55555555556E-4<br />
&csy=5.55555555556E-4<br />
&bnd=<br />
&bndnm=<br />
&RC=d9b131a2a5e3589013aaddb1d5f567585db594<br />
&lft=-148.33333333333334<br />
&rgt=-146.66666666666669<br />
&top=63.0<br />
&bot=59.0`

For my purposes, it’s these last four which are useful. Change them [National][6] like so

`&lft=-143&rgt=-140&top=71.0&bot=59.0`

and then each in turn

`&lft=-147&rgt=-143&top=71.0&bot=59.0<br />
&lft=-150&rgt=-147&top=71.0&bot=59.0`

and I have my whole area of interest in three simple requests, plus there is no need go through the bother of mosaicking a bunch of little tiles together. It does take the server about 15 or 20 minutes to process each request though. I didn’t attempt to find the maximum area, as my main goal is to get the data, not find the limits of their server and crash it.

**If you use this technique, please be gentle**. It’s not in our interests to force them to take protective measures and close this avenue.

Further exploration: I suspect many of the parameters can be omitted, *siz *for example which has no apparent effect (my downloads [wholesale jerseys][7] were 350mb each) and I bet the -1 values mean “use the default”. I’m curious [cheap NBA jerseys][8] about *RC* which likes a unique session id or cookie or something. I had no problem [Planned][9] using the same number every time, but I did do it all in one browser session.

Many thanks to Joe H. and John Thull on the QGIS-user mailing list for bumping me in the right direction ([[offtopic] acquiring Alaska data)][10], [Websites][11] Chris Pederick for the web developer extension, and course the USGS for having data interesting enough to go through all this work in the first place!

***UPDATE:***

With regard to ordering the regional CD’s:

*“You can order the entire U.S. in 30 meter resolution in either  
ArcGrid or GridFloat format. The data will be provided on a 250 GB  
external drive at a total price of $1005.00. This includes shipping  
and handling. This will cover the Conterminous U.S., Alaska (at 60  
meter res), Hawaii, and the territorial islands. We no longer provide  
this on CD or DVD media.”*

An incredibly good price in my opinion.

The contact address is <webmapping@usgs.gov>

Customer Service/Webmapping

Data and Applications Support Department  
Science Applications [of][12] International Corporation (SAIC) at  
U.S. Geological Survey – EROS  
(Earth Resources Observation and Science)  
47914 252nd Street  
Sioux Falls, SD 57198-0001

Phone: 1-800-252-4547  
Fax: (605)-594-6589

##### Comments

1.  **[Dave Smith][13]** wrote:
    Thanks for the backdoor tip… I would echo your caveat to not abuse this.
    
    I too have noticed that seamless.usgs.gov seems to have some serious JavaScript disagreements with IE, which results in tremendously sluggish performance (or worse yet, it just dies altogether).
    
    When [cheap jerseys][14] I tried in FireFox, the site worked like a champ.
    
    Posted 31 Mar 2007 at 10:18 am
    
     </li> 
    *   **matt wilkie** wrote:
        hi Dave, thanks for confirming my IE problems with [Beta][15] their site are not local only <img class="wlEmoticon wlEmoticon-smile" alt="Smile" src="http://www.yukongis.ca/wp-content/uploads/2014/02/wlEmoticon-smile.png" />
        
        Posted 03 Apr 2007 at 8:48 am</li> </ol>

 [1]: http://seamless.usgs.gov/
 [2]: https://www.miamidolphinsjerseyspop.com
 [3]: http://charlottetaylor.de/endlich-da-ava-jack/
 [4]: http://chrispederick.com/work/webdeveloper/
 [5]: https://www.cheapjerseyschina.top
 [6]: http://www.yukongis.ca/2007/04/backdoor-to-us-seamless-national-elevation-data/
 [7]: https://www.wholesalejerseys4free.com
 [8]: http://www.wholesalenfljerseysgest.com
 [9]: http://www.roskamforcongress.com/2016/01/life-news-house-votes-to-de-fund-planned-parenthood-abortion-biz-sends-bill-to-obamas-desk/
 [10]: http://www.nabble.com/-offtopic--acquiring-Alaska-data-t3370917.html
 [11]: http://www.fallcomm.com/websites/
 [12]: http://glassworksna.com/benefits-3d-pictures-glass/
 [13]: http://surveying-mapping-gis.blogspot.com/
 [14]: https://www.cheapjerseysfor.com
 [15]: http://www.ahekonkongresi.com/2015/09/14/brooklyn-beta-was-the-most-important-conference-ive-been/
