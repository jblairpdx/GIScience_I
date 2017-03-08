---
title: GEOG 4/581 - Lab 2
---

# Lab 2: Projections


#### Purpose

Understanding projections and spatial data types, and how they are handled in ArcMap.


#### Prerequisites

This excercise builds on skills practiced in Lab 1, inlcuding basic knowledge of how to create an ArcMap document, how to add data and other elements to it, and how to create a shareable document to turn in.


#### References & Links

* ArcGIS Desktop: Using data frames.
  - [https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/using-data-frames.htm](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/using-data-frames.htm)


#### To Turn In

* Single-page map in Portable Document Format (PDF).
* Written document with lab questions in a commonly-accessible format (Microsoft Word, rich text, markdown, etc.)

Submit the documents to the class Canvas page as listed under the lab assignment at your earliest convenience before the start of the next lab.


#### Steps

For best results, read through all instructions before starting the lab.

Note: The questions to answer in this lab relate to the process you complete in these steps. You may find it helpful to answer questions as you create the map rather than waiting until the end. Whichever method you prefer, be sure to contemplate *what you are actually doing* while completing these steps. Remember: the skill is not in following directions (or memorizing them), it's understanding what is happening.

### Part 1 - Map Instructions

Reminder: Save often! it is a good idea to save frequently. You may even want to Save As and give sequential filelenames so that you could revert to a previous version if you make a mistake that you cannot undo or if the ArcMap document gets corrupted.

##### Read [*Using data frames*](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-arcmap/using-data-frames.htm]) from the ArcMap documentation site.

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

##### Set up the layour page.

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

When in the *Data View* (not *Layout View*), adding a new data frame will cause the area displaying the active data frame (the main body of the application window) to go blank. This is because only the **active** data frame is displayed in *Data View*. ArcMap automatically switches the active data frame to the new one after adding it. To activate an inactive data frame, right-click on its name and choose `Activate`.

1. Create a new data frame with the menu item `Insert->Data Frame`.
2. Add the country boundaries you downloaded to the map.
3. Choose a color to symbolize the countries with.
4. Rename the data frame to 'World - GCS'.
5. View the coordinate system of the data frame; note that it is set to display the unprojected *Geographic Coordinate System*.



TODO: FINISH MAP INSTRUCTIONS.
TODO: OVERWRITE WRITE-UP WITH NEW QUESTIONS





### Part 3 - Write-up

**Note:** Some of the questions in the write-up relate to the actions you take in making your map; you may find it helpful to answer those questions as you go, rather than waiting until after completion.

##### Instructions

1. Copy & paste the questions below into a document in your preferred word processor/text editor.
  - Be sure to use a commonly-viewable document format, e.g. Word, rich text, markdown.
2. Compose your answers for each question in the document following each question.

##### Questions

1. How many files were contained in the downloaded file *citylim_2016.zip*?
2. What types of files were contained in the downloaded file *citylim_2016* and what data does each one contain? Hint: look at the file extensions and do a web search, e.g., Google or Wikipedia, to find out what they mean.
3. Looking at your final map, what pattern(s) do you notice in the data? How might these perceived patterns change if you plotted cities as points rather than showing the city limits? (1-2 sentences)
4. What changes would you make in a future version of the map to make it easier to read or interpret? (1-2 sentences; there are always changes that can be made, take some time to think and be creative)
5. What happens to files that are saved on the C:\\ drive when you log out of the computers in SSIL?


TODO: Image & references for: 
Data Frame Properties - Coordinate System tab.
