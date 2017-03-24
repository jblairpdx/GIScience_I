
---
title: GEOG 4/581 - Lab 4
---

# Lab 4: Spatial Selection and Attribute Queries


#### Purpose

Datasets are often large collections of like features, of which only a subset is of interest in answering a specific question. This lab will demonstrate seveal ways to accomplish the tasks of selecting and filtering data. It will also introduce a way to summarize numeric data and display that data in an infographic—a chart).


#### Prerequisites

This excercise builds on skills practiced in Labs 1-3.


#### References & Links

* ArcGIS Desktop: Using Select By Location.
  - [http://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/using-select-by-location.htm](http://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/using-select-by-location.htm)
* The National Map - Small-Scale Data Download.
  - [https://nationalmap.gov/small_scale/atlasftp.html](https://nationalmap.gov/small_scale/atlasftp.html)
* United States Census Bureau: Geography - Maps & Data.
  - [https://www.census.gov/geo/maps-data/](https://www.census.gov/geo/maps-data/)
* UO Libraries: Map & Aerial Photography Library - Learning Commons Data Share.
  - [https://library.uoregon.edu/map/gis_data/data_in_commons.html](https://library.uoregon.edu/map/gis_data/data_in_commons.html)
* Washington State Geospatial Portal - GIS Data Catalog.
  - [https://geography.wa.gov/node/111](https://geography.wa.gov/node/111)


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

ArcMap has a way to make a selection—a subset of features that have been chosen in some way to be highlighted and available for other functions to interact with separate the rest of the features.

**Selection**

* The selection is a temporary state in the application, displayed in the map and attribute table.
  - The default graphical representation of the selection is a bright teal outline of the feature geometry in the map and row in the attribute table.
* Selections are mutable: features can be added and removed, or the selection set can be completely re-evaluated.
* Selections are ephemeral: selections are not encoded in the dataset/feature class itself (though it can persist in the map document).
  - To make a more permanent copy of a selection, one should create a new feature class with the selected features.

### Part 1 - Map Instructions

Reminder: Save often! it is a good idea to save frequently. You may even want to Save As and give sequential filelenames so that you could revert to a previous version if you make a mistake that you cannot undo or if the ArcMap document gets corrupted.

#### 1.1 - Data

The purpose of the map that you create is to show the distribution of observed precipiation across cities in the state of Washington. Though there may be a Washington-specific feature class for precipitation, we will be developing our own using selection and querying techniques.

##### Create a new Lab4 folder, and download spatial datasets there.

Discover and download the datasets via the link provided. Be sure to note the data source, in order to provide citations on your map.

* States 2015 (1:500k).
  - Link: [https://www.census.gov/geo/maps-data/data/tiger-cart-boundary.html](https://www.census.gov/geo/maps-data/data/tiger-cart-boundary.html)
  - Filename: cb_2015_us_state_5m.zip.
* Counties 2015 (1:500k).
  - Link: [https://www.census.gov/geo/maps-data/data/tiger-cart-boundary.html](https://www.census.gov/geo/maps-data/data/tiger-cart-boundary.html)
  - Filename: cb_2015_us_county_500k.zip.
* Cities and Towns, One Million Scale.
  - Link: [https://nationalmap.gov/small_scale/atlasftp.html](https://nationalmap.gov/small_scale/atlasftp.html)
  - Filename: citiesx010g_shp_nt00962.tar.gz.
  - **Note**: Unlike the other downloads, this isn't stored in a zipfile archive. Rather, it's stored in a tar-archive which is then in a gzip-archive. Windows doesn't natively read from these kinds of archives. To extract this archive, use the PeaZip utility application (twice, it's double-archived), which you can find at `R:\Class_Data\Utilities\PeaZip\peazip.exe`.
* Precipitation Intensities (Western Washington).
  - Link: [https://geography.wa.gov/node/111](https://geography.wa.gov/node/111)
  - Filename: precipevents.zip.
  - Raster dataset name: maprecip (for 'mean annual precipitation').
  - **Note**: This portal is not the origin of the dataset: be sure to investigate the website and/or metadata for the source.

##### Create a new ArcMap document.

1. Name it Lab4_Washington_Precipitation.mxd.
2. Rename the default data frame `Washington State`.
3. Change the data frame coordinate system to Washington's state plane (north) coordinate system: `NAD 1983 HARN StatePlane Washington North FIPS 4601`.

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
7. Examine the *Spatial selection method for target layer feature(s)* options. This is a description of the relationship between the source geometry (Washington) and the target geometry (cities) you'll be selecting. You'll be fine with the default `intersect the source feature layer.


##TODO: FINISH FROM HERE



##### Add the following datasets from the library's Learning Commons Data Share.

See instructions on the [data shares website](https://library.uoregon.edu/map/gis_data/data_in_commons.html).

* Canada Provinces: `\\confusion.uoregon.edu\GISData\Esri_Data\canada\data\province.sdc`









##### Make adjustments to the vector layers.

1. Rename the countries layer to something more understandable.
2. Symbolize the countries with a dark color for the outline and 'No Color' for the fill.
3. Symbolize the cities using a point symbol and color of your choice.

##### Open and inspect the *Attribute Table* for the cities layer.

1. Right-click with the cursor on the name of the layer.
2. Select `Open Attribute Table`.

##### Use the *Identify* tool with the vector layers.

1. Read the webpage ['Identifying Features'](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/identifying-features.htm).
2. Enable the *Identify* tool by clicking on the button in the *Tools* toolbar.
  - It looks like a white lowercase 'i' in front of a blue globe.
3. Click on features displayed in the data frame to see more information about those features.
  - The *Identify* panel (which will appear after clicking the tool on a feature) displays the attributes for a single feature in a slightly different way than the *Attribute Table*.
4. Try a few options from the the *Identify* panel's 'Identify from' menu.

#### 1.2 - Raster Data

##### Read the webpage ['What is raster data?'](https://desktop.arcgis.com/en/arcmap/latest/manage-data/raster-and-images/what-is-raster-data.htm)

##### Add the world population (2015) raster dataset as a layer to the data frame.

1. Find the dataset at `R:\Class_Data\Lab3\Data\gpw-v4-population-density-2015.tif`.
  - The dataset is actually from the [Socioeconomic Data and Applications Center (SEDAC)](http://sedac.ciesin.columbia.edu/data/set/gpw-v4-population-density). We skipped the download process here because (a) the website requires registration for downloads, and (b) the download is large (230 MB), no point in everyone downloading it to the same filesystem.
  - Do use the website or the associated PDF in the folder for citation information and any other details you may be interested in.
2. Reorder the layers in the *Table of Contents*, if necessary, to place the raster layer below the vector layers.

##### Make adjustments to the raster layer.

1. Rename the layer to something more understandable.
2. Symbolize the raster with *Stretched* symbology.
3. Choose a color ramp that displays values from light-to-dark that is of a contrasting color in comparison to the city symbols.
4. Try the different choices under *Stretch Type*, located toward the bottom of the *Symbology* tab after choosing *Stretched*. Choose the one that you believe makes the data most clear.

##### Inspect the attribute values for the raster layer.

Raster datasets only have a single value for each pixel (ignoring concepts like multi-band and related attribute tables).

1. Use the *Identify* tool again to inspect some raster pixel values across the map. Feel free to zoom in for more accuracy in choosing pixels.
  - The *Pixel value* is the actual attribute value at that point.
  - The *Stretched value* is the conversion of the pizel value into a position on the color ramp (from 0 to 255 from left-to-right). The details of the conversion are defined in the *Stretch Type*

#### 1.3 - Design layout & add context map.

#### Adjust & place current data frame.

1. Choose a country to be the focus of the current data frame, and adjust the position and scale to set that focus.
2. Using what you learned from Lab 2 and the projections lecture, set a projection that is suitable for the data. You'll want to minimize distortion for your chosen country, and preserve properties related to the data (hint: population density is area-based).
3. In *Layout View*, adjust the size of the data frame to fill the majority of the page.
4. You may need to readjust the scale & position so that the focus is how you want it.

#### Create a context map.

Context maps are useful for readers to understand the map's location in a greater extent. Here we will make a context map that shows the location of the country of focus in the wider world.

1. Insert a new data frame.
2. Add the countries dataset to the new data frame.
3. Symbolize the countries with a neutral fill color.
4. Set the data frame's projection to be an area-preserving world projection.
5. Adjust the size of the data frame in the layout to fit in available space.
  - It's certainly possible to have the context data frame overlap the main map or be within a data-free section of it. Use your judgement regarding whether that makes sense design-wise. You will need to change the data frame background fill color, though (it's clear at first).
6. Zoom to the extent of the data (worldwide).
  1. You can zoom using methods you've learned in previous labs, but there is also some other ways to zoom that may be helpful:
    + Right-click on a layer name and choose `Zoom to Layer` from the context menu.
    + Select features in a layer you wish to zoom to; `Select Features` white arrow and `Clear Selected Features` button are on the *Tools* toolbar. You can select features by: clicking on them (hold shift to select more), or dragging a box around the ones you want (hold shift to select more). After selecting them, right-click the layer name and choose `Selection->Zoom to Selected Features`. Don't forget to clear the selection when you're done.
7. Add a graticule (a grid of parallels and meridians) as the direction indicator.
  1. Open the context map data frame's properties and go to the *Grids* tab.
  2. Add a new grid, and step through the 'wizard' to set up how it is displayed. Lines every 30 degrees is recommended.
8. Add an extent indicator to show the location of your main map in the context map.
  1. Open the context map data frame properties, and go to the *Extent Indicators* tab.
  2. Move the data frame for the main map into the *Show extent indicator for these data frames* box.
  3. If you wish, you may choose to adjust the options for the extent indicator when they appear below the box.

##### Add elements for the layout.

Type, style, and place the following elements in the layout.

1. An appropriate title, representing the data presented.
2. A text caption for each map.
2. The author/cartographer's name (that's you). To help your instructors, please put this under the title or in the bottom-right corner.
3. The data source(s).
4. Direction indicator each map (north arrow or graticule), as appropriate.
5. Scale indicator, as appropriate.
6. A legend for the main map (`Insert->Legend`). No need to make this perfect, but do try to make it clean and readable.

##### Make a PDF copy of your map.

1. Filename: `Lab2_Projections.pdf`.
2. Take a look at your exported PDF through a PDF viewing application or a web browser. **Always look at your output!** Both common and unusual errors slip past creators when they don't look at their outputs.


### Part 3 - Write-up

**Note:** Some of the questions in the write-up relate to the actions you take in making your map; you may find it helpful to answer those questions as you go, rather than waiting until after completion.

##### Instructions

1. Copy & paste the questions below into a document in your preferred word processor/text editor.
  - Be sure to use a commonly-viewable document format, e.g. Word, rich text, markdown.
2. Compose your answers for each question in the document following each question.

##### Questions
##TODO: have try all-caps, all lower, mixed attribute in state query. have try same with attribute/field name.try without double-quites around fieldname. try without single quotes around attribute value.
1. Vector features are represented as points, (poly)lines, or area features (polygons). The cities data are represented as _____________ and the countries are represented as _____________.
2. What does one row in the attribute table for the cities layer represent?
3. What city is at the location -3.01° longitude and 16.76° latitude?
  * Note: As you move the cursor in the map area, the coordinates of the cursor are shown in the bottom bar of the application. You may need to `Pan` and `Zoom` (on the *Tools* toolbar) the map display to focus on the area of interest.
4. In what country is the city named in question 3 located?
5. What does one cell in the population density raster represent?
6. What is the population density ('pixel value') in the city named in question 3?
  * Note: Zoom in far enough to see the individual grid cells; the city is represented by a point in the vector layer, and that point lies in exactly one cell (even though the extent of the city in the real world covered the area of many grid cells).
6. What are the units for the pixel values? Hint: check the documents that came with the dataset.
7. What are the pixel values for the color-free area inside Greenland, and over the oceans? Can you find a setting to make these cells a specific color instead of transparent? Where is it?
8. Which projection did you choose for your map? Provide a brief justification for your choice.

TODO: Other:
Double-check the LC Data Share's data used here (SDCs are old, right?).
Create Lab3_Data folder in R:\Class_Data.
Move population density raster into there (be sure to update naming/path-ing).
