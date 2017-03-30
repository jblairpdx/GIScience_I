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
* Oregon City Limits - 2015.
  * Link: [http://spatialdata.oregonexplorer.info/geoportal/](http://spatialdata.oregonexplorer.info/geoportal/)
  * Filename: `citylim_2016.zip`.

##### Create a new ArcMap document.

1. Name it Lab5_Tsunami_Relief_Center.mxd.
2. Add the downloaded datasets to the default data frame.
2. Change the data frame coordinate system to Oregon's statewide coordinate system: `NAD 1983 HARN Oregon Statewide Lambert`.
  * **Note**: this will automatically happen if the first dataset is one of the above downloaded from the state library.
3. Add taxlots from the Library's Leaning Commons Data Share.

* Lane County Taxlots - 2012.
  * File location: `\\confusion.uoregon.edu\GISData\UO_GIS_Collections\US_states\Oregon\Counties\Lane_Co\Tax_lots\LaneTaxlots_2012.gdb`.
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

Since definition queries cannot perform spatial queries, you'll need to export the results of a spatial selection to a new shapefile with a descriptive name (e.g. `Florence_Taxlots.shp`).

##### Filter Florence taxlots to exclude water and right-of-way taxlots.

It would make no sense to place a relief center in water or a road or other right-of-way. Luckily, the taxlot dataset has ways of identifying these types of lots:

1. Water & right-of-way lots have "taxlot" field values of `'11'`, `'22'`, `'33'`, `'44'`, `'55'`, `'66'`, `'77'`, `'88'`, `'99'` (see a pattern?).
  * If using these, do notice they are text attributes, not integers (i.e. no `<` or `>` can be used).
1. These types of taxlots also do not have a "taxcode" value, while  others do.
  * If using this, remember that null-values have a distinct query syntax: `X is NULL`, not `X = NULL`.

##### Select Florence taxlots that that are within by the tsunami evacuation zone.

Export a copy of this with a descriptive name (e.g. `Florence_Taxlots_Tsunami.shp`).

##### Compute the total potential improvement damage and number of taxlots affected.

'Improvements' is assessment & taxation jargon for buildings, structures, and any other property of value on a lot beyond its land value.

1. Open the attribute layer for the lots in the tsunami evacuation zone.
2. Find the "impval" field; right-click on the field name and choose `Statistics`.
3. Write down the values mentioned above.

##TODO: FINISH FROM HERE.

##### Add & filter states.

1. Add state boundaries to the map.
2. Filter the state boundaries to show only the state of Washington using a `Definition Query`.
  1. Open the *Layer Properties*, and go to the *Definition Query* tab.
  2. Construct a query that will return features for which the `NAME` field/attribute value is `'Washington'`. You can take a crack at typing this out, but I would recommend using the *Query Builder* tool available. It helps avoid formatting errors and typos.

A definition query omits features that do not satisfy the logic of the query from display in the data frame map or attribute table. Any functions or processing that occurs on the layer while the definition query is in place will only use the features still showing; however the query does not change the contents of the actual dataset—the file is still the same.

##### Add & spatially select cities.

There are three different tools to perform a spatial selection in ArcMap, and they vary by the level of interaction they provide.

* `Select Features` tool on the `Tools` toolbar (white arrow over a white square) (highest level of interaction).
* `Select By Location` dialog in the `Selection` menu.
* `Select Layer By Location` tool in the `Data Management` toolbox in the `ArcToolbox` panel (lowest level of interaction).

Though you may investigate the other tools, this step will use the middle option.

1. Add U.S. cities to the map.
2. Read the webpage ['Using Select By Location'](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/using-select-by-location.htm).
3. Open the tool dialog at `Selection->Select By Location`.
4. Examine the *Selection method* options. You'll be fine with the default `select features from`.
5. *Target layer(s)* are the layers that you want to select the features from. We want to select cities.
6. *Source layer* is the layer that has the features you want to define the spatial area to select with. We want to select cities within the state of Washington.
7. Examine the *Spatial selection method for target layer feature(s)* options. This is a description of the relationship between the source geometry (Washington) and the target geometry (cities) you'll be selecting. You'll be fine with the default `intersect the source layer feature`/

Note: The selection can be cleared via the menu item `Selection -> Clear Selected Features`; or using the icon in the *Tools* toolbar with the same button icon as the menu item (white square).

##### Alter selection using population attribute.

If you look at the population attributes for the cities, you'll notice a number of places with a 2010 population of -999. Data maintainers often use obviously incorrect numbers such as this to indicate 'no value' when the data model doesn't support an explicit lack of value. In this case, these are 'cities' that the Census no longer counts a population for (usually a city that no longer exists or one that was subsumed by a different city).

Let's remove these population-less cities from our selection. There are two tools to perform an attribute selection in ArcMap.

* `Select By Attributes` dialog in the `Selection` menu.
* `Select Layer By Attributes` tool in the `Data Management` toolbox in the `ArcToolbox` panel.

This step will use the first one.

1. Read the webpage ['Using Select By Attributes'](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/using-select-by-attributes.htm).
2. Open the attribute selection tool via `Selection -> Select By Attributes`.
3. Examine the *Method* options. This is description of the relationship (if any) this selection will have with the 'current selection'. For our purposes here, we should choose `Select from current selection`.
4. Use the field & value boxes and operator buttons to create an attribute query that will select cities that do not have a 2010 population with the value -999.

##### Export selected citites to new dataset.

1. Right-click on the name of the cities layer, and choose `Data -> Export Data`.
  1. The default export option when the layer has a selection set is to export the selected features. Keep this.
  2. It doesn't matter a whole lot for our purposes here, but use the layer's source data to set the output's coordinate system.
  3. Place output in your Lab4 folder, specifying a descriptive filename (e.g. `City_WA_5000.shp`).
2. Once the output is exported, ArcMap will ask whether you want to add the exported data to the map; choose yes.
3. Turn off (uncheck the box) or remove (right-click on name, choose `Remove`) the original cities layer.

##### Add precipitation data (maprecip) to the map.

##### Determine the precipitation value at each city.

In Lab 2, you used the `Identify` tool to find the raster value at a given city; you had to zoom in to the city-point to determine the cell that lay under it. It's more efficient when dealing with lots of data points to let the computer do the work.

1. Read the webpage ['Extract Values to Points'](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/extract-values-to-points.htm).
2. Turn on the *Spatial Analyst* extension: the *Extract Values to Points* tool will only work with the extension turned-on.
  1. Open the *Extensions* dialog via `Customize -> Extensions`.
  2. Mark the checkbox next to *Spatial Analyst*.
3. Open *ArcToolbox* via the menu item `Geoprocessing -> ArcToolbox`. ArcToolbox is a large collection of tools available for GIS processing. Much of the deeper functions are contained here.
4. In ArcToolbox, navigate to and open the *Extract Values to Points* tool: `Spatial Analyst Tools -> Extraction -> Extract Values to Points`. Alternatively, you could search for the tool via the Search panel (if not present on your sidebar, it can be opened via `Windows -> Search`).
5. Enter your Washington cities layer as the `Input point features` by choosing it from the drop-down menu.
6. Enter the precipitation raster as the `Input raster`.
7. Set `Output point features` to be in your Lab4 folder and have a descriptive filename (e.g. `City_Precip.shp`).
8. Leave the rest of the options with their default settings.
9. After running the tool, open the attribute table for the output layer. At the far right side of the table, you'll see a field named `RASTERVALU`; this was added to the city attributes by the tool, containing the values for the cell at the same location as the city-point.
10. Turn off or remove the Washington cities layer that does not have the precipitation values added.
11. The `maprecip` raster layer will be of no more use. Feel free to turn it off or remove.

Spatial dataset output in a file folder will default to the *shapefile* type; the file extension `.shp` will automatically be added at the end of the filename if not already there.

##### Summarize precipitation data by county.

We will be creating an infographic to supplement our map. First, we need to summarize the information we've integrated.

1. Open the attribute table for your new cities-precipitation layer.
2. Find the `COUNTY` attribute field; right-click on the field name and choose `Summarize`.
3. `Select a field to summarize` is already filled-out, defaulting to the field you clicked on.
4. Find `RASTERVALU`in the field list for option 2; pick `Average` as the statistic to summarize for each county.
5. Set the output table to be in your Lab4 folder and have a descriptive filename (e.g. `Precip_County_Summary.dbf`).

Summary output does not have spatial attributes (i.e. a geometry). Hence it does not appear in the map view of the data frame, nor does it appear in the default Table of Contents style, which is called the *List By Drawing Order* TOC. To be able to see the table listed, change the Table of Contents to the *List By Source* style, which can be activated by clicking on the second button between where it says 'Table of Contents' and the list of layers.

Table output in a file folder will default to the *dBase* type; the file extension `.dbf` will automatically be added at the end of the filename if not already there.

##### Add Canadian provinces and Washington counties for context.

1. Canada provinces: `\\confusion.uoregon.edu\GISData\Esri_Data\canada\data\province.sdc`. See instructions on the [data shares website](https://library.uoregon.edu/map/gis_data/data_in_commons.html) to refresh how to access this.
2. You've already downloaded counties, but they're nationwide. Apply what you've learned so far to get what you need.

#### 1.2 Map and Infographic

##### Symbolize cities using graduated symbols that represent the precipitation value.

1. Read the webpage ['Using Graduated Symbols'](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/using-graduated-symbols.htm).
2. Open the layer properties for the city-precipitation layer, and select the *Symbology* tab.
3. Choose `Quantities -> Graduated symbols` for the *Show* option on the left.
4. Set *Fields -> Value* to be `RASTERVALU`, your precipitation attribute.
6. Change the template symbol to the fill color of your preference.
5. Use the defaults for the other options; feel free to investigate at your leisure, though.

##### Symbolize & label counties

1. Set a visible border and no fill color.
2. Turn on the labels: right-click the layer name and choose `Label Features`. Alternatively, you can open the layer properties and check the box at the top of the *Labels* tab. This is also where you would go to change the label defaults.

##### Symbolize & label surrounding provinces.

Use a subtle color: let Washington stand out.

##### Symbolize & label states.

1. You want to show the surrounding states along with Washington now, so remove the definition query.
2. Color Washington to stand out from the surrounding states.
  1. Open the *Symbology* tab in the states layer properties, and choose `Categories -> Unique Values` from the *Show* option.
  2. Set the *Value Field* to `NAME`
  3. Click the `Add Values` button, find and select `'Washington'`. Washington now appears in the symbol list on its own.
  4. Choose a bold color for Washington, aand a subtle color for `<all other values>` that matches the color for the provinces above.
3. Label the surrounding states (not Washington; its name will be in the map title).
  1. Open the *Labels* tab of the layer properties, and check the `Label features in this layer` box.
  2. Change the *Method* option to `Define classes of features and label each class differently`.
  3. Open the now-available `SQL Query` tool, and use what you've learned about attribute queries to label all states that **are not** Washington.

##### Re-evaluate the symbolization.

Adjust the color scheme to best emphasize the map data and area of interest. Also be sure to not overwhelm the labels.

##### Place the map in the layout.

1. Switch to *Layout View*.
2. Change the paper size to 11"x17" (called 'tabloid' size).
2. Resize and place the Washington State data frame to fill a large portion of the page.
3. Pan the data frame to center on the state of Washington and zoom in so that the Washington fills most of the data frame.

##### Create an inset map.

1. Copy the current data frame & paste the copy in the layout.
2. Rename the new data frame `Olympic Peninsula`.
3. Adjust the position and size of the new data frame to fit in your layout design.
4. Pan & zoom the new data frame to capture the Olympic Peninsula as the focus. This is the large peninsula that occupies the western part of the state.
5. Add an extend indicator for the new data frame in the Washington State data frame (see Lab 3).

##### Create a county precipitation graph.

1. Open the county precipitation summary table you created (remember, only visible in *List By Source* style of Table of Contents).
2. From the *Table Options* menu (notecard-like button in upper-left corner of *Table* panel), choose `Create Graph`.
3. Step through the *Create Graph Wizard* that opened, and configure a graph that shows the precipitation by county. The color used in the graph should complement the color you used to symbolize precipitation in the map.
  1. A simple graph would be a vertical bar graph using the value `Average_RASTERVALU` (Y-value) and an X-value from the `COUNTY` field.
  2. As you alter settings, the preview will update. Make adjustments until you feel the graph is satisfactory. I would recommend improved title and labels, and possibly dropping the graph legend.
4. When you finish, the graph will appear in its own window. Right-click on the graph, and choose `Add to Layout`.
5. Resize and place the graph as appropriate in your layout.

ArcMap was designed to process and display spatial data as maps; the tools for other infographics are fairly limited in comparison to other applications. It is important to have labels and complete data on infographics, but less important to perfect the graphic design here. In a more professional GIS project workflow, infographics would probably be developed (or at least completed) in an application more attuned to graphic design.

##### Make final adjustments of graphs & maps.

Explore layout designs, finding a way to use the available space. Don't leave gaping holes, but also leave enough empty space so the layout doesn't seem overly crowded. This is an iterative process.

##### Add elements for the maps & layout.

Type, style, and place the following elements in the layout.

1. An appropriate title, representing the data presented.
2. A text caption for each map.
2. The author/cartographer's name (that's you). To help your instructors, please put this under the title or in the bottom-right corner.
3. The data source(s).
4. A direction indicator (north arrow or graticule), as appropriate.
5. A scale indicator, as appropriate.
6. A legend for the main map (`Insert->Legend`). No need to make this perfect, but do try to make it clean and readable (renaming map layer may help).

##### Make a PDF copy of your map.

1. Filename: `Lab4_Washington_Precipitation.pdf`.
2. Take a look at your exported PDF through a PDF viewing application or a web browser. **Always look at your output!** Both common and unusual errors slip past creators when they don't look at their outputs.


### Part 3 - Write-up

**Note:** Some of the questions in the write-up relate to the actions you take in making your map; you may find it helpful to answer those questions as you go, rather than waiting until after completion.

##### Instructions

1. Copy & paste the questions below into a document in your preferred word processor/text editor.
  - Be sure to use a commonly-viewable document format, e.g. Word, rich text, markdown.
2. Compose your answers for each question in the document following each question.

##### Questions

1. To filter the states to show only the state of Washington, we set a *Definition Query*; to filter the cities to consist of a subset of all U.S. cities, we performed a selection (*Select By Location*) and exported the result to a new file. What are the differences between a *Definition Query* and a selection export from the perspective of the files saved on the computer?
2. What are the differences between a *Definition Query* and a selection from the perspective of the data displayed on the map?
3. The *Extract Values to Points* tool was run after the original cities dataset had been filtered to include on the cities in Washington. What difference would it have made to perform those actions in the opposite order?
4. Briefly describe the pattern that you see in the distribution of precipitation in Washington (1-2 sentences).
5. Briefly describe the pattern that you see in the distribution of precipitation in the Olympic Peninsula. 
6. Review the *Table of Contents* styles (buttons directly above the layer contents of the TOC panel). List the four styles, and suggest a reason each style would be useful.

##TODO: Other:
Double-check the LC Data Share's data used here (SDCs are old, right?).
