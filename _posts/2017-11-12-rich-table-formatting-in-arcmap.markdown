---
title: Rich table formatting in Arcmap
date: 2017-11-12 00:00:00 -08:00
tags:
- arcmap
- cartography
- tables
---

> ***Nutshell: **Copy to Excel, style as desired, copy and paste, size and place to suit.*

# The default, plain, way

Embedding a table in an Arcmap layout has been around since it's inception, and it's pretty easy, though the menu item for making it happen is buried so many don't know about it: Open the attribute table that you want to create the report from, click the Options button on the bottom of the Attribute table window, and select the option to “[Add Table to Layout](http://webhelp.esri.com/arcgisdesktop/9.3/index.cfm?TopicName=Adding_a_table_to_a_layout)“. (An expanded treatment of this method can be found at [Using tables in an ArcMap layout](http://blogs.esri.com/esri/arcgis/2010/01/19/using-tables-in-an-arcmap-layout/) on one of the the Esri blogs.)

![table-arcmap-01.png](/uploads/table-arcmap-01.png)

## Adding some *style*!

This is good and useful, but what if you want some more control over how it looks? A little bit more work, but not too bad and well worth it: [copy the table](http://gis.stackexchange.com/questions/58939/copy-not-export-a-table-from-arcmap) to Excel and do the pretty stuff there.

* Open the attribute table >> select the records of interest >> r-click on the row selector at far left >> Copy selected records

* Open Excel >> Paste

* Apply [Styles](http://chandoo.org/wp/2011/12/05/excel-formatting-tips/) and format [conditionally](http://spreadsheets.about.com/od/advancedexcel/tp/090822-excel-conditional-formatting-hub.htm) as is your wont (To lose the jail cells, fill the background with a pure colour)

* Now reverse the process and copy and paste back to Arcmap, then size place to suit.

**et Voila!**

![table-arcmap-rich-02.png](/uploads/table-arcmap-rich-02.png)

## Limitations

The table is just a dumb graphic. If you see a spelling mistake or need to udpate it for next year you'll need to repeat everything (but that's the same for the native Arcmap embedded tables). To make repeated updates easier, export rather than copy the table ([saving results in a model](http://blogs.esri.com/esri/arcgis/2010/04/02/the-power-of-the-results-window/) for quick repeat), and use [saved styles](http://office.microsoft.com/en-ca/excel-help/save-styles-to-use-in-new-workbooks-HP005202422.aspx) and formatting rules everywhere possible in Excel.