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
  * [https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/identifying-features.htm](https://desktop.arcgis.com/en/arcmap/latest/map/working-with-layers/identifying-features.htm)
* ArcGIS Desktop: What is raster data?
  * [https://desktop.arcgis.com/en/arcmap/latest/manage-data/raster-and-images/what-is-raster-data.htm](https://desktop.arcgis.com/en/arcmap/latest/manage-data/raster-and-images/what-is-raster-data.htm)
* Socioeconomic Data and Applications Center (SEDAC): Gridded Population of the World (GPW), v4 - Population Density, v4.
  * [http://sedac.ciesin.columbia.edu/data/set/gpw-v4-population-density](http://sedac.ciesin.columbia.edu/data/set/gpw-v4-population-density)
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

#### 1.1 - Vector Data

Unlike in previous labs, you will not need to download the vector data for this part. Instead, you will connect to the UO Library's server to acess the data directly.

##### Create a new Lab3 folder and ArcMap document.

Name it Lab3_World_Population.mxd.

##### Connect to the library's Learning Commons Data Share.

Just as you have connected to folders on local and network drives mapped to a drive letter, you can also connect to folders on other servers without a drive letter. Follow the connection instructions on the [data shares website](https://library.uoregon.edu/map/gis_data/data_in_commons.html) to get it connected.

Note: As the website states, the Learning Commons are only accessible on UO computers, or directly connected to the UO network: the VPN will not work. Also, we recently discovered that the data share was not accessible to the SSIL computers. If this is still the case at lab time, use the alternative downloads instead.

##### Add the countries and cities of the world to the map from the Esri-provided data collection.

* Countries: `\\confusion.uoregon.edu\GISData\Esri_Data\world\data\cntry06.sdc\cntry06`
* Cities: `\\confusion.uoregon.edu\GISData\Esri_Data\world\data\cities.sdc\cities`

Alternative downloads:
* Site: [http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip](http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip)
* Countries alt: `Admin 0 - Countries`
* Cities alt: `Admin 1 - Populated Places`

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

1. Find the dataset at `R:\GEOG481_3\Class_Data\Lab3\Data\gpw-v4-population-density-2015.tif`.
  * The dataset is actually from the [Socioeconomic Data and Applications Center (SEDAC)](http://sedac.ciesin.columbia.edu/data/set/gpw-v4-population-density). We skipped the download process here because (a) the website requires registration for downloads, and (b) the download is large (230 MB), no point in everyone downloading it to the same filesystem.
  * Do use the website or the associated PDF in the folder for citation information and any other details you may be interested in.
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

##### Add elements for the maps & layout.

Type, style, and place the following elements in the layout.

1. An appropriate title, representing the data presented.
2. A text caption for each map.
2. The author/cartographer's name (that's you). To help your instructors, please put this under the title or in the bottom-right corner.
3. The data source(s).
4. A direction indicator (north arrow or graticule), as appropriate.
5. A scale indicator, as appropriate.
6. A legend for the main map (`Insert->Legend`). No need to make this perfect, but do try to make it clean and readable.

##### Make a PDF copy of your map.

1. Filename: `Lab3_World_Population.pdf`.
2. Take a look at your exported PDF through a PDF viewing application or a web browser. **Always look at your output!** Both common and unusual errors slip past creators when they don't look at their outputs.


### Part 3 - Write-up

**Note:** Some of the questions in the write-up relate to the actions you take in making your map; you may find it helpful to answer those questions as you go, rather than waiting until after completion.

##### Instructions

1. Copy & paste the questions below into a document in your preferred word processor/text editor.
  - Be sure to use a commonly-viewable document format, e.g. Word, rich text, markdown.
2. Compose your answers for each question in the document following each question.

##### Questions

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
