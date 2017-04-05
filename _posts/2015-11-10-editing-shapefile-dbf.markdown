---
title: Editing Shapefile DBF
date: 2015-11-10 03:56:00 -08:00
categories:
- tables
tags:
- dbf
---

*Excel 2007 is the last version that supported in place editing of .dbf files. Access 2010 is the last version that can import .dbf files (though Excel 2010 and 2013 can still read them, via drag and drop). What to do?*

If it's Excel's usability you're after (extended search and replace, repeat previous values, fill, ...) and you can change the default storage format: use personal-geodatabase instead of shapefiles. Then you can just open the .mdb in Access and edit there or push/pull from .xls as needed.

Remember it's important to keep the ObjectID or FID intact, so no adding or deleting rows from the Access and Excel side, and be careful to only touch the feature class tables. As long as you keep backups and tread with care and attention you'll be fine.

An added benefit is being able to use Longer_Field_Names and increased row limits.

…

For just *get up and go* without any changes to formats or workflow the best current method I’ve found for direct editing of DBF files outside of ArcGIS is via **[DBF Viewer Plus](http://www.alexnolan.net/software/dbf.htm)**. It free and comes in a single file portable executable (voluntary payment asked for, no nagging though).

In the event DBF Viewer Plus disappears my next fall back would be **[DBF Manager](http://dbfmanager.com/), **$45 - $60 USD**.**

If it’s important to stay inside Excel, then the route is with **[SaveDBF addon](http://thexlwiz.blogspot.ca/)**, but note development and support stopped as of January 2015 so this is only an interim solution.

A heavy weight solution which should work pretty much in perpetuity is **[LibreOffice](https://www.libreoffice.org/)** or **[OpenOffice](http://www.openoffice.org/)**.

Further reading

* **[DBF creation and manipulation without excel 2003](http://gis.stackexchange.com/questions/3302/dbf-creation-and-manipulation-without-excel-2003)**