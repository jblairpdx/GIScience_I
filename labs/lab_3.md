
---
title: GEOG 4/581 - Lab 3
---

# Lab 3: Spatial Data Types and Querying Values


#### Purpose

Spatial data is commonly represented in either of two formats: raster and vector. This lab will explore, compare, and contrast data in each of these formats.


#### Prerequisites

This excercise builds on skills practiced in Labs 1-2.


#### References & Links

* ArcGIS Desktop: Identifying features.
  - [https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/identifying-features.htm](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/identifying-features.htm)
* ArcGIS Desktop: What is raster data?
  - [https://desktop.arcgis.com/en/arcmap/latest/manage-data/raster-and-images/what-is-raster-data.htm](https://desktop.arcgis.com/en/arcmap/latest/manage-data/raster-and-images/what-is-raster-data.htm)
* UO Libraries: Map & Aerial Photography Library - Learning Commons Data Share.
  - [https://library.uoregon.edu/map/gis_data/data_in_commons.html](https://library.uoregon.edu/map/gis_data/data_in_commons.html)


#### To Turn In

* Single-page map in Portable Document Format (PDF).
* Written document with lab questions in a commonly-accessible format (Microsoft Word, rich text, markdown, etc.)

Submit the documents to the class Canvas page as listed under the lab assignment at your earliest convenience before the start of the next lab.


#### Steps

For best results, read through all instructions before starting the lab.

Note: The questions to answer in this lab relate to the process you complete in these steps. You may find it helpful to answer questions as you create the map rather than waiting until the end. Whichever method you prefer, be sure to contemplate *what you are actually doing* while completing these steps. Remember: the skill is not in following directions (or memorizing them), it's understanding what is happening.

### Part 1 - Map Instructions

Reminder: Save often! it is a good idea to save frequently. You may even want to Save As and give sequential filelenames so that you could revert to a previous version if you make a mistake that you cannot undo or if the ArcMap document gets corrupted.

#### 1.1 - Vector Data

Unlike in previous labs, you will not need to download the vector data for this part. Instead, you will connect to the UO Library's server to acess the data directly.

##### Create a new Lab3 folder and ArcMap document.

Name it Lab3_World_Population.mxd.

##### Connect to the library's Learning Commons Data Share.

Just as you have connected to folders on local and network drives mapped to a drive letter, you can also connect to folders on other servers without a drive letter. Follow the connection instructions on the [data shares website](https://library.uoregon.edu/map/gis_data/data_in_commons.html) to get it connected.

##### Add the countries and cities of the world to the map from the Esri-provided data collection.

* Countries: `\\confusion.uoregon.edu\GISData\Esri_Data\world\data\cntry06.sdc\cntry06`
* Cities: `\\confusion.uoregon.edu\GISData\Esri_Data\world\data\cities.sdc\cities`

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

1. Find the dataset at `R:\Class_Data\Lab3_Data\NAME_HERE`.
  - The dataset is actually from: [http://sedac.ciesin.columbia.edu/data/collection/gpw-v4/sets/browse](http://sedac.ciesin.columbia.edu/data/collection/gpw-v4/sets/browse). We skipped that process here because (a) the website requires registration for downloads, and (b) the download is large (230 MB), no point in everyone downloading it to the same filesystem.
  - Do use the website or the associated PDF for citation information.
2. Reorder the layers in the *Table of Contents*, if necessary, to place the raster layer below the vector layers.

##### Make adjustments to the vector layers.

1. Choose *Stretched* symbology.

TODO: FINISH FROM HERE



##### Set up the layout page.

1. Open the page settings with the menu item `File->Page and Print Setup`.
2. Make sure these sett paper size to *Letter*, and set the map page size to match or use the printer paper settings.
3. Set the orientation to *Portrait*.
4. Be sure to save your map document.

##### Create a data frame of the state of Oregon.

1. Add the state boundaries you downloaded to the map. Remember, SSIL doesn't save your application settings, so you'll need to use the `Connect to Folder` button in ArcCatalog to add your Lab2 folder.
2. Choose a color to symbolize the states with.
3. Rename the data frame.
  1. Open the *Data Frame Properties* dialog window: double-click the data frame's name in the Table of Contents, or right-click and choose `Properties`.
  2. In the *General* tab, the name is listed at the top. Change it to 'Oregon - GCS', then click `OK` to set the new properties.
4. View the coordinate system of the data frame, under the *Coordinate System* tab of the *Properties* dialog window. Note that the data frame is set to display the unprojected *Geographic Coordinate System*.
5. Be sure to save your map document.

When first created, a data frame does not have a projection or coordinate system. It will automatically set itself to the first spatial dataset that is added.

##### Create a data frame of the world's countries.

When in the *Data View* (not *Layout View*), adding a new data frame will cause the area displaying the active data frame (the main body of the application window) to go blank. This is because only the **active** data frame is displayed in *Data View*. ArcMap automatically switches the active data frame to the new one after adding it. The active data frame will have its name in **bold text**. To activate an inactive data frame, right-click on its name and choose `Activate`.

1. Create a new data frame with the menu item `Insert->Data Frame`.
2. Add the country boundaries you downloaded to the map.
3. Choose a color to symbolize the countries with.
4. Rename the data frame to 'World - GCS'.
5. View the coordinate system of the data frame; note that it is set to display the unprojected *Geographic Coordinate System*.

##### Position the data frames in the layout.

1. Switch from *Data View* to *Layout View* with the menu item `View->Layout View` (or using the button at the bottom of the window).
2. Activate the 'Oregon - GCS' data frame.
  1. In *Layout View*, selecting a data frame in the layout will activate it.
  2. You can also activate using the same method as works in the data frame.
3. Open the data frame's properties. Much like activating, this can be done by interacting with the data frame in the *Table of Contents* and the graphical representation of it.
4. Adjust the size and position of the data frame. Where and what to change should be apparent.
  1. Set the top-left corner of the frame to be 0.15 inches from the left (X), and 9.85 inches from the bottom (Y) of the layout.
    - *Position coordinates advance from the bottom-left corner of the layout, just like a standard cartesian coordinate (XY) graph.*
    - Units are set by the Map Page Size in *Page & Print Setup*, which you set near the beginning of the lab. Don't worry about typing them in when entering values.
  2. Set the size of the map to be 4 inches square.
5. Pan the **data frame** so it is centered on Oregon.
6. Zoom the data frame so that the entire state of Oregon appears with margins on all sides.
7. Activate the 'World - GCS' data frame, and repeat steps 3-6 with it using:
  1. Top-left corner's X = 0.15 inches, Y = 4.5 inches.
  2. Width = 2.5 inches, height = 4 inches.

Beware double-clicking a data frame rectangle in the layout! You may assume this will open the properties, but it does not. Instead it will make the space within interactive like you are in *Data View*. If this is happening, the rectangle will have a thicker outline than usual. Clicking out of the frame will bring you out of it. A normally-selected data frame in the layout will have the resizing handles.

##### Duplicate the data frames and project the duplicates.

1. Select one of the data frames in the layout.
2. Copy the data frame. Either right-click on the rectangle, use the menu item `Edit->Copy`, or use the keyboard shortcut `CTRL-C`.
3. Paste the copy into the layout. Either right-click, `Edit->Paste`, or `CTRL-V`.
4. Rename the new data frame. Replace the 'GCS' part of the name with 'Lambert'.
5. Adjust the position of the new data frame (keep the same size).
  1. 'Oregon - Lambert': Top-right corner's X = 8.35 in, Y = 9.85 in.
  2. 'World - Lambert': Top-right corner's X = 8.35 in, Y = 4.5 in.

##### Project the duplicate data frames.

None of the data frames currently have a projection; they're just longitude and latitude expressed as X and Y coordinates. For each of the new data frames ('Oregon - Lambert', 'World - Lambert'):

1. Open the *Data Frame Properties* and go to the *Coordinate System* tab.
2. In the list of coordinate systems, find the projected coordinate system **NAD 1983 (2011) Oregon Statewide Lambert (Meters)**. Hint: typing something in the search bar at the top may help thin the options.

Note: ArcMap will perform reprojection of a coordinate system 'on-the-fly'. The spatial data in the files do not change; rather the software transforms the coordinates to match the data frame just before drawing the display. This is very handy, and not as common in GIS software as you'd hope.

##### Add elements for each map.

Type, style, and place the following elements for each map in the layout (use your judgement). Remember the `Insert` menu!

1. An appropriate (and distinct) title.
2. A brief description of the suitability of the projection for the map considering the scale and type/location of distortion.

Note: When making a visual information product, you should always be sure each map, data graphic, or table is labeled with a title or caption, possibly both. Folks need to know what they're looking at.

##### Add elements for the layout.

Type, style, and place the following elements in the layout.

1. An appropriate title.
2. The author/cartographer's name (that's you). To help your instructors, please put this under the title or in the bottom-right corner.
3. The data source(s).
  1. In a data visualization such as this, naming the individual or organization that collected the data will suffice for citations.
  2. e.g. "Source: OpenStreetMap Contributors".

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

1. When changing the projection of a data frame a warning pop-up windows appeared. What does this warning message mean? What happens when you dismiss the window (click `Yes`)?
2. ArcMap allows you to have multiple data frames (maps) in a single layout. You can drag files from the *Catalog* panel in the *Layout View* to add it to a data frame. If there are multiple data frames, in which one is the new layer added? How is that data frame visually presented in the ArcMap user interface?
3. For which of the four maps you created is it appropriate to include a north arrow as the direction indicator? Briefly describe (1-2 sentences) why a north arrow would not be appropriate for the other maps.
4. For which of the four maps you created is it appropriate to include an indicator of scale (bar or text-ratio). Briefly describe (1-2 sentences) how a map reader would understand or interpret scale in the other maps.
5. For each of the two datasets, (state of Oregon and countries of the world), which of the projections/coordinate systems used in the lab (unprojected geographic coordinates or Lambert Conformal Conic) would you use for making maps similar in scale and extent to the ones you created here? Briefly (1-2 sentences) describe why.


TODO: Image & references for:

TODO: Other:
Double-check the LC Data Share's data used here (SDCs are old, right?).
Create Lab3_Data folder in R:\Class_Data.
Move population density raster into there (be sure to update naming/path-ing).
