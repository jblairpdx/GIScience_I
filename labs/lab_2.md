---
title: GEOG 4/581 - Lab 2
---

# Lab 2: Projections


#### Purpose

Understanding projections and spatial data types, and how they are handled in ArcMap.


#### Prerequisites

This excercise builds on skills practiced in Lab 1, inlcuding basic knowledge of how to create an ArcMap document, how to add data and other elements to it, and how to create a shareable document to turn in.


#### References & Links

* ArcGIS Desktop: Quick ways to navigate data frames and layouts.
  * [https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/quick-ways-to-navigate-data-frames-and-layouts.htm](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/quick-ways-to-navigate-data-frames-and-layouts.htm)
* ArcGIS Desktop: Using data frames.
  * [https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/using-data-frames.htm](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/using-data-frames.htm)
* United States Census Bureau: Geography - Maps & Data.
  * [https://www.census.gov/geo/maps-data/](https://www.census.gov/geo/maps-data/)


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

##### Read [*Using data frames*](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/using-data-frames.htm) from the ArcMap documentation site.

##### Create a Lab2 folder in your student folder.

##### Download spatial datasets.

Discover and download the datasets via the link provided. Be sure to note the data source, in order to provide citations on your map.

* States 2015 (1:5,000,000).
  - Link: [https://www.census.gov/geo/maps-data/data/tiger-cart-boundary.html](https://www.census.gov/geo/maps-data/data/tiger-cart-boundary.html)
  - Filename: cb_2015_us_state_5m.zip.
* Countries (without boundary lakes).
  - Link: [http://www.naturalearthdata.com/downloads/110m-cultural-vectors/](http://www.naturalearthdata.com/downloads/110m-cultural-vectors/)
  - Filename: ne_110m_admin_0_countries.zip.

##### Create a new ArcMap document.

Name it Lab2_Projections.mxd and put it in your Lab2 folder.

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

##### Read [*Quick ways to navigate data frames and layouts*](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/quick-ways-to-navigate-data-frames-and-layouts.htm) from the ArcMap documentation site.

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

##### Duplicate & place the data frames.

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
2. A brief description of the how suitable the projection (or lack of) is for the map.
  * Consider the extent the map covers, and the possible distortion effects of the projection.
  * Note: The class lecture on projections occurs on Wednesday of this week. Early lab sections may want to wait until after that class to fill this out, or read up on the projection in question.
    * Wikipedia has great projection pages: [https://en.wikipedia.org/wiki/Lambert_conformal_conic_projection](https://en.wikipedia.org/wiki/Lambert_conformal_conic_projection)
    * [https://jblairpdx.github.io/GIScience_I/slides/lecture_04.html](https://jblairpdx.github.io/GIScience_I/slides/lecture_04.html)

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

  * Note: The class lecture on projections occurs on Wednesday of this week. Early lab sections may want to wait until after that class to fill these out, or read up on the projection in question.
    * Wikipedia has great projection pages: [https://en.wikipedia.org/wiki/Lambert_conformal_conic_projection](https://en.wikipedia.org/wiki/Lambert_conformal_conic_projection)
    * [https://jblairpdx.github.io/GIScience_I/slides/lecture_04.html](https://jblairpdx.github.io/GIScience_I/slides/lecture_04.html)

1. When changing the projection of a data frame a warning pop-up windows appeared. What does this warning message mean? What happens when you dismiss the window (click `Yes`)?
2. ArcMap allows you to have multiple data frames (maps) in a single layout. You can drag files from the *Catalog* panel in the *Layout View* to add it to a data frame. If there are multiple data frames, in which one is the new layer added? How is that data frame visually presented in the ArcMap user interface?
3. For which of the four maps you created is it appropriate to include a north arrow as the direction indicator? Briefly describe (1-2 sentences) why a north arrow would not be appropriate for the other maps.
4. For which of the four maps you created is it appropriate to include an indicator of scale (bar or text-ratio). Briefly describe (1-2 sentences) how a map reader would understand or interpret scale in the other maps.
5. For each of the two datasets, (state of Oregon and countries of the world), which of the projections/coordinate systems used in the lab (unprojected geographic coordinates or Lambert Conformal Conic) would you use for making maps similar in scale and extent to the ones you created here? Briefly (1-2 sentences) describe why.
