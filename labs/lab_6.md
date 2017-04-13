---
title: GEOG 4/581 - Lab 6
---

# Lab 6:  Working with Raster Data—Elevation


#### Purpose

Processing & analysis functions available for raster data differs from that of vector data. Although we have encountered raster data in previous labs, it had played a relatively minor role. In this lab, raster data is at the forefront. This lab explores raster processing that focuses on elevation data, and also includes a quick introduction to a new application in ArcGIS Desktop—ArcScene—which displays 3-dimensional spatial data.


#### Prerequisites

This excercise builds on skills practiced in Labs 1-5.


#### References & Links

* ArcGIS Desktop: Aspect.
  * [https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/aspect.htm](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/aspect.htm)
* ArcGIS Desktop: Contour.
  * [https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/contour.htm](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/contour.htm)
* ArcGIS Desktop: Extract Multi Values to Points.
  * [https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/extract-multi-values-to-points.htm](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/extract-multi-values-to-points.htm)
* ArcGIS Desktop: Hillshade.
  * [https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/hillshade.htm](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/hillshade.htm)
* ArcGIS Desktop: Slope.
  * [https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/slope.htm](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/slope.htm)


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

##### Create a new `Lab6` folder, and download spatial datasets there.

Discover and download the datasets via the link provided. Be sure to note the data source, in order to provide citations on your map.

* Pre-eruption Mt. St. Helens 30-meter Digital Elevation Model (DEM).
  * Link: [http://gis.ess.washington.edu/data/raster/thirtymeter/mtsthelens/](http://gis.ess.washington.edu/data/raster/thirtymeter/mtsthelens/)
  * Filename: `OldMtStHelens.zip`.
* (Current) Mt. St. Helens 30-meter Digital Elevation Model (DEM).
  * Link: [http://gis.ess.washington.edu/data/raster/thirtymeter/mtsthelens/](http://gis.ess.washington.edu/data/raster/thirtymeter/mtsthelens/)
  * Filename: `q2323.zip`.

Hint: The DEM rasters are derived from United States Geological Survey (USGS) data. Unfortunately, their historic DEM website is currently missing, so we're getting these from a secondary source.

Digital elevation models are continuous data that breaks the covered space into a uniform grid of cells, and stores a single elevation value in each cell as sampled from the ground it covers. Though a DEM can be stored in pretty much any raster data format, it is common to see USGS DEM datasets as a *.dem file.

##### Create a new ArcMap document.

1. Name it `Lab6_Mt_St_Helens.mxd`.
2. Add the downloaded datasets to the default data frame.
3. Change the names of your layers to something more descriptive, e.g. `DEM_Before`, `DEM_After`.

##### Create a new shapefile dataset.

1. Using the *ArcCatalog* panel, right-click on your `Lab6` folder, and choose `New -> Shapefile`.
  1. Name the new shapefile `Viewpoints.shp`.
  2. Make the feature type `Point`.
  3. Choose the spatial reference (`Edit` button), match it to the DEMs (NAD 1927 UTM Zone 10N).
2. Add the shapefile as a layer in your data frame, if it doesn't automatically do so.
3. Add at least five points somewhere on the mountain.
  1. Turn on one of the DEMs to make sure you place them where elevation data exists.
  2. Open the *Editor* toolbar: right-click on any toolbar, and choose `Editor`.
  3. In the drop-down menu on the toolbar, choose `Start Editing`. Note: if you have layers from more than one folder or database, it will ask you which folder/database you wish to edit in. Choose your `Lab6` folder; this makes any editable dataset in that 'workspace' open for adding/removing/altering features.
  4. A *Create Features* panel should have opened up. If it has not, under the *Editor* toolbar's drop-down menu it will be available to open under *Editing Windows*.
  5. Click on the point feature that shows in the panel (likely labelled 'Viewpoints' - this chooses the dataset features to create). Then click in locations you wish to create a point at.
  6. Though you've created the points, they are not 'saved' to the file itself. To do that, choose `Save Edits` from the *Editor* toolbar's drop-down menu.
  7. Choose `Stop Editing` from the drop-down. If you haven't saved recent edits, you will be prompted whether you want them saved to the file. Alternately, you can choose to get rid of unsaved edits by stopping an 'Edit Session' and choosing to not save your edits.

#### 1.2 - Analysis & Processing

##### Prepare your application settings for running raster analysis tools.

1. Turn on the *Spatial Analyst* extension (under menu item `Customize -> Extensions`).
2. Set the workspace environment to automatically write output to your `Lab6` folder.
  1. Open the *Environment Settings* dialog via the menu item `Geoprocessing -> Environments`.
  2. Expand the *Workspace* section.
  3. Change the *Current Workspace* & *Scratch Workspace* setting to your lab folder (should be `R:\GEOG481_3\Student_Data\[Duck ID]\Lab6`).

By setting the *Workspace* environment setting, tools will automatically use the `Lab6` folder when creating a default output filepath.

##### Run a collection of elevation analysis tools.

For each tool in the following list:

1. Read the ArcGIS Desktop documentation webpage about the tool.
2. Execute the tool with the **after** DEM as the input raster, with the other parameters as provided.
  * All tools listed are availabe in the `Spatial Analyst -> Surface` section of the *ArcToolbox* panel.
  * If *ArcToolbox* is not open, do so via the menu item `Geoprocessing -> ArcToolbox`.
  * If you wish to see how a long-running tool is doing, open the *Results* panel via the menu item `Geoprocessing -> Results`. This panel has indicators for tool status, messages, and even history of tools run.
4. Examine the output raster.

* Contour [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/contour.htm).
  * Output polyline features: `Contour_After_60m.shp`.
  * Contour interval: `60` (meters; check the coordinate system units).
* Slope [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/slope.htm).
  * Output raster: `Slope_After`.
  * Output measurement: `DEGREE`.
* Aspect [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/aspect.htm).
  * Output raster: `Aspect_After`.
* Hillshade [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/hillshade.htm).
  * Output raster: `Hillshade_After`.

##### Extract the raster values for elevation, slope, and aspect for each of the viewpoints.

You could certainly do this manually, using the *Identify* tool you've used in a previous lab to find the the cell values below each viewpoint. You could even run the *Extract Values to Points* tool that you used in Lab 4 multiple times. However, there is a tool that can automate this some.

1. Read the documentation for [*Extract Multi Values to Points*](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/extract-multi-values-to-points.htm)
2. Open the tool interface, in `ArcToolbox -> Spatial Analyst Tools -> Extraction`.
3. Choose your viewpoints shapefile as the input point features, and add your aspect, slope, and after DEM as your input rasters.
4. Optional: change the *Output field name* for each raster to something more readable. These are the fields that the tool will create on the viewpoints shapefile; you may want not wish to use the raster layer name for the field (e.g. maybe *elevation* makes more sense when on the viewpoints than *DEM_After*.
5. Run the tool.
6. Open the viewpoints attribute table and examine the values in the new fields.


#### 1.3 - 3D Scene Plotting



##TODO: FINISH FROM HERE



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
2. Resize and place the data frames on the page how you think best displays them for viewers.
  1. Consider different sizes for each of the maps.
  2. Consider vertical & horizontal lengths: your map's extent may not be easily represented in a square.
  3. You may need to pan & zoom within the data frame to make sure you're showing all you wish at the right scale.
3. Once you've set the data frames' size, placement, and extent, you may want to re-evaluate your symbolization within your data frames.
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
