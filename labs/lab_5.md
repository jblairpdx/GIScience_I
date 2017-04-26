---
title: GEOG 4/581 - Lab 5
---

# Lab 5: Site Selection—Tsunami Relief Center


#### Purpose

In this lab, we will consider possible locations for a relief center in the city of Florence, Oregon, for assistance in the event of a tsunami event. Florence lies in western Lane County along the coast of the Pacific Ocean. This has potential risk from tsunami events around the Pacific Rim, including ones caused by local earthquakes. Check out the website https://pnsn.org/ for more information.


#### Prerequisites

This excercise builds on skills practiced in Labs 1-4.


#### References & Links

* Oregon Spatial Data Library.
  * [http://spatialdata.oregonexplorer.info/geoportal/](http://spatialdata.oregonexplorer.info/geoportal/)
* UO Libraries: Map & Aerial Photography Library - Learning Commons Data Share.
  * [https://library.uoregon.edu/map/gis_data/data_in_commons.html](https://library.uoregon.edu/map/gis_data/data_in_commons.html)


#### To Turn In

* Single-page map in Portable Document Format (PDF).
* Written document with lab questions in a commonly-accessible format (Microsoft Word, rich text, markdown, etc.)

Put a copy of each document:

1. Inside the `Lab#` subfolder in your student folder. It's simplest to just complete the original documents here.
2. Uploaded to the class Canvas site as listed under the lab assignment.

Submit the documents at your earliest convenience before the start of the next lab.


#### Steps

For best results, read through all instructions before starting the lab.

Note: The questions to answer in this lab relate to the process you complete in these steps. You may find it helpful to answer questions as you create the map rather than waiting until the end. Whichever method you prefer, be sure to contemplate *what you are actually doing* while completing these steps. Remember: the skill is not in following directions (or memorizing them), it's understanding what is happening.


### Part 1 - Map Instructions

Reminder: Save often! it is a good idea to save frequently. You may even want to Save As and give sequential filelenames so that you could revert to a previous version if you make a mistake that you cannot undo or if the ArcMap document gets corrupted.

#### 1.1 - Data

##### Create a new Lab5 folder, and download spatial datasets there.

Discover and download the datasets via the link provided. Be sure to note the data source, in order to provide citations on your map.

* Oregon Tsunami Evacutation Zone - 2013.
  * Link: [http://spatialdata.oregonexplorer.info/geoportal/](http://spatialdata.oregonexplorer.info/geoportal/)
  * Filename: `DOGAMI_TsunamiEvacuationZones_2013.zip`.
* Oregon City Limits - 2016.
  * Link: [http://spatialdata.oregonexplorer.info/geoportal/](http://spatialdata.oregonexplorer.info/geoportal/)
  * Filename: `citylim_2016.zip`.

##### Create a new ArcMap document.

1. Name it Lab5_Tsunami_Relief_Center.mxd.
2. Add the downloaded datasets to the default data frame.
2. Change the data frame coordinate system to Oregon's statewide coordinate system: `NAD 1983 HARN Oregon Statewide Lambert`.
  * **Note**: this will automatically happen if the first dataset is one of the above downloaded from the state library.
3. Add taxlots from the Library's Leaning Commons Data Share.

* Lane County Taxlots - 2012.
  * File location: `\\confusion.uoregon.edu\GISData\UO_GIS_Collection\US_states\Oregon\Counties\Lane_Co\Tax_lots\LaneTaxlots_2012.gdb`.
  * Filename: `LaneTaxlots2012`.


#### 1.2 - Analysis & Processing

##### Filter the city limits to only include the city of Florence.

You should now know numerous ways of only having the Florence boundaries:

1. Definition query.
2. Select and export to a new shapefile with a descriptive name (e.g. `Florence.shp`).

Which to choose is a matter of preference. Some like the clean representation of their steps in new datasets. Others prefer to not create lots of extra files. Sometimes a definition query of a large-enough dataset will perform more slowly. Either way, ArcMap will treat them exactly the same.

#####  Filter the tsunami evacuation zones to only include the zones for a 'local' tsunami.

Check the attribute table for the zone types. It's up to you whether to filter the local zones that aren't near Florence (they won't affect the map or analysis).

##### Select taxlots that are in the city of Florence.

Since definition queries cannot perform spatial queries, you'll need to export the results of a spatial selection to a new shapefile with a descriptive name (e.g. `Florence_Taxlots.shp`) and add it to your data frame.

##### Filter Florence taxlots to exclude water and right-of-way taxlots.

It would make no sense to place a relief center in water or a road or other right-of-way. Luckily, the taxlot dataset has ways of identifying these types of lots:

1. Water & right-of-way lots have "taxlot" field values of `'11'`, `'22'`, `'33'`, `'44'`, `'55'`, `'66'`, `'77'`, `'88'`, `'99'` (see a pattern?).
  * If using these, do notice they are text attributes, not integers (i.e. no `<` or `>` can be used).
1. These types of taxlots also do not have a "taxcode" value, while  others do.
  * If using this, remember that null-values have a distinct query syntax: `X is NULL`, not `X = NULL`.

##### Select Florence taxlots that that will be impacted by a local tsunami.

Export a copy of this with a descriptive name (e.g. `Florence_Taxlots_Tsunami.shp`) and add it to your data frame.

##### Compute the total potential improvement damage and number of taxlots affected.

'Improvements' is assessment & taxation jargon for buildings, structures, and any other property of value on a lot beyond its land value.

1. Open the attribute layer for the lots in the tsunami evacuation zone.
2. Find the "impval" field; right-click on the field name and choose `Statistics`.
3. Write down the values mentioned above; you will need them later.

##### Locate potential properties to site a tsunami relief center on.

1. Eligible taxlots will need to meet the following criteria:
  1. Be more than 500 feet from the tsunami evacuation zone;
  2. Have an improvement value less than $10,000;
  3. Cover an area ("mapacres") greater than a half-acre but less than 1 acre;
  4. Have a property class description ("propcldes") of `'COMMERCIAL, VACANT'` or `'COMMERCIAL, IMPROVED'`.
2. Take some time to think about which operations are needed to answer this, including:
  1. The selection method setting when selecting part of the criteria.
  2. The spatial selection method setting when selecting by location.
  2. If combining the attribute selections into a single query, whether you need to enfore query order (parentheses).
3. After you're satisfied your selection queries have the correct result, export the selection as a new shapefile with a descriptive name (e.g. `Potential_Relief_Centers.shp`), and add it to your data frame.


#### 1.2 Map and Infographic

You will create **two** data frames tp place on your page layout. The first will show a local tsunami's impact in historic 'Old Town' Florence, along the bayfront. The second will show impact across all of Florence, as well as the potential locations for relief centers.

##### Create Old Town Florence data frame.

1. Rename the current data frame to 'Old Town Florence'.
2. Symbolize the tsunami-impacted taxlots in categories by the property class description.
  1. Combine the property classes into larger groups or your choosing, e.g. residential, commercial.
  2. When in the *Symbology* tab of the layer properties, select the individual values you wish to group.
    * Hold down the `Ctrl` button and click on the values to select & unselect them.
    * Select a value, then hold the `Shift` button and click another to select them and all values between them.
  3. Right-click on the selected values, and choose `Group Values`.
  4. You can remove values/groups; they will be symbolized with the `<all other values>`. To add them back, click the `Add Values` button, generate a complete list, and select the one(s) you wish to re-add.
  5. Click on the text in the *Label* section for the grouped value to create a simpler name for the group, e.g. 'Residential'.
  6. If using `<all other values>`, change its label. If not, uncheck it on the list to turn it off.
  7. Hint: Changing the text next to where the list says `<Heading>` will impact how a map legend covering these is labelled.
  8. Other hint: create a group to hold other/miscellaneous values. `<all other values>` is listed in map legends rather distinct from the other values for that layer.
3. Symbolize the tsunami evacuation zone with a blue shade, and make it somewhat transparent (*Transparent %* is a setting in the *Display* tab of the layer properties). Set the outline width to `0` (will turn the outline off); place the layer atop the drawing order.
4. Show the taxlots not affected by the tsunami (only the Florence ones). Give this layer a neutral color and place it below the tsunami-impacted lots in the drawing order.
5. Change the names of your layers to something more descriptive.
6. Consider adding a 'basemap'. Basemaps are images of map information that can be placed behind data layers to make a map seem 'more complete'. ArcMap has a number of options for basemaps that you can add to your maps, accessible via the menu item `File -> Add Data ->  Add Basemap`. The data behind these comes across your internet connection, so they tend to draw more slowly.

##### Create all-Florence data frame.

1. Insert a new data frame and name it 'Florence'.
2. Copy (`right-click on name -> Copy`) the following layers from the Old Town data frame and paste (`right-click on data frame name -> Paste`) them in the new one: tsunami zone, and tsunami-impacted taxlots, basemap (if using).
3. If the potential relief center locations and the Florence city limits are in the Old Town data frame, copy & paste them over as well. If not, add them to the new data frame.
4. Change the symbology of the tsunami-impacted taxlots to a single symbol type.
5. Change the symbology of the potential relief center locations and city limits. Make sure the relief center polygons stand out on the map. For the city limits, make sure the outline is visible, and fill draws behind the other non-basemap layers. If you have a basemap, you may wish to not have a fill color on the city at all.
5. Add an extent indicator to show the extent of the Old Town Florence data frame (only visible in *Layout View*).

##### Place the maps in the layout.

1. Switch to *Layout View*.
2. Change the paper size to 11"x17" (called 'tabloid' size).
3. Resize and place the data frames on the page how you think best displays them for viewers.
  1. Consider different sizes for each of the maps.
  2. Consider vertical & horizontal lengths: your map's extent may not be easily represented in a square.
  3. You may need to pan & zoom within the data frame to make sure you're showing all you wish at the right scale.
4. Once you've set the data frames' size, placement, and extent, you may want to re-evaluate your symbolization within your data frames.
  1. Do the outlines seem too thick?
  2. Are the colors distinguishable from each other?

Explore layout designs, finding a way to use the available space. Don't leave gaping holes, but also leave enough empty space so the layout doesn't seem overly crowded. This is an iterative process.

##### Add elements for the maps & layout.

Type, style, and place the following elements in the layout.

1. An appropriate title, representing the data presented.
2. A text caption for each map.
2. The author/cartographer's name (that's you). To help your instructors, please put this under the title or in the bottom-right corner.
3. The data source(s).
4. A direction indicator (north arrow or graticule) for each map, as appropriate.
5. A scale indicator for each map, as appropriate.
6. A legend for the main map (`Insert->Legend`). No need to make this perfect, but do try to make it clean and readable (renaming map layer may help).

Be sure to include the values for total potential improvement damage and number of taxlots affected on your layout. These could be included in the map captions, or as other text elements.

##### Make a PDF copy of your map.

1. Filename: `Lab5_Tsunami_Relief_Center.pdf`.
2. Take a look at your exported PDF through a PDF viewing application or a web browser. **Always look at your output!** Both common and unusual errors slip past creators when they don't look at their outputs.


### Part 3 - Write-up

**Note:** Some of the questions in the write-up relate to the actions you take in making your map; you may find it helpful to answer those questions as you go, rather than waiting until after completion.

##### Instructions

1. Copy & paste the questions below into a document in your preferred word processor/text editor.
  - Be sure to use a commonly-viewable document format, e.g. Word, rich text, markdown.
2. Compose your answers for each question in the document following each question.

##### Questions

1. How many taxlots are potentially impacted by a local tsunami?
2. What is the total potential improvement damage caused by a local tsunami?
3. The answer for question 2 represents the potential economic loss (by destruction of improvements) on taxlots that may be impacted by a local tsunami. How well does this number capture the potential impact? Be creative; consider the selection method you used, accuracy of improvement data, and whether a tsunami's impact is felt primarily by the improvements...
4. How many taxlots met the criteria for a tsunami relief center?
5. Which spatial selection method did you use to determine which taxlots would be impacted by a local tsunami? Why did you choose this method (in contrast to the other methods)?
6. Briefly describe the story that your map product tells. Include a statement about the analysis you performed, or results you obtained (3-4 sentences).
