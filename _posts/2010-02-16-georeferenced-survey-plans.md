---
ID: 39
post_title: Georeferenced Survey Plans
author: matt
post_date: 2010-02-16 22:53:45
layout: post
published: true
---
*The federal government has plans for all surveyed parcels online as images, but they aren't georeferenced. Here is a short recipe and dataset for fixing that.* <div id="section_1">
  <h2>
    Process:
  </h2>
  
  <ol>
    <li>
      Download plan as regular tiff from Canada Centre for Cadastral Management (CCM) -<a title="http://www.lsd.nrcan.gc.ca/english/srisdocs_e.asp?RG=YT&PLN=93521" href="http://www.lsd.nrcan.gc.ca/english/srisdocs_e.asp?RG=YT&PLN=93521" target="_top" rel="external nofollow">http://www.lsd.nrcan.gc.ca/english/srisdocs_e.asp?RG=YT&PLN=93521</a> where RG=YT is <em>Region = Yukon</em>, and PLN=93521 is <em>Plan# 93521</em>. For bulk download see <a title="http://sydney.freeearthfoundation.com/mattwilkie/Survey_Plans/scripts/" href="http://sydney.freeearthfoundation.com/mattwilkie/Survey_Plans/scripts/" target="_top" rel="external nofollow">scripts</a>: <code>    fetch-CLSplans 84574 85779 86458 etc...</code>
    </li>
    <li>
      Load into <a title="oldsite/ArcMap" href="http://www.yukongis.ca/oldsite/ArcMap.html" rel="internal">ArcMap</a> along with <em>Surveyed_Parcels</em> layer from Geomatics Yukon Corporate Spatial Warehouse (CSW), use Yukon Albers projection. <em>Note</em>: This same cadastre data also available from <a title="ftp://ftpyukoncccm.nrcan.gc.ca/" href="ftp://ftpyukoncccm.nrcan.gc.ca/" target="_top" rel="external nofollow">ftp://ftpyukoncccm.nrcan.gc.ca/</a>.
    </li>
    <li>
      Use the Georeferencing toolbar, georeference the image (using <em>Update Georeferencing</em> rather than <em>Rectify</em>)
    </li>
    <li>
      Move result from <em>noref</em> to <em>georef</em> folder.
    </li>
    <li>
      Add to unmanaged raster catalog <em>Survey_Plans</em> in file geodatabase.
    </li>
  </ol> Feel free to extend the set of georeferenced images and share the results. Temporary home for this project is 
  
  <a title="http://sydney.freeearthfoundation.com/mattwilkie/Survey_Plans/" href="http://sydney.freeearthfoundation.com/mattwilkie/Survey_Plans/" target="_top" rel="external nofollow">http://sydney.freeearthfoundation.com/mattwilkie/Survey_Plans/</a>
</div>