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
2. Execute the tool with the **after-eruption** DEM as the input raster, with the other parameters as provided.
  * All tools listed are availabe in the `Spatial Analyst -> Surface` section of the *ArcToolbox* panel.
  * If *ArcToolbox* is not open, do so via the menu item `Geoprocessing -> ArcToolbox`.
  * If you wish to see how a long-running tool is doing, open the *Results* panel via the menu item `Geoprocessing -> Results`. This panel has indicators for tool status, messages, and even history of tools run.
4. Examine the output raster.

* Contour [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/contour.htm).
  * Output polyline features: `Contour_After_60m.shp`.
  * Contour interval: `60` (meters; check the coordinate system units).
* Slope [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/slope.htm).
  * Output raster: `Slope_After.tif`.
  * Output measurement: `DEGREE`.
* Aspect [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/aspect.htm).
  * Output raster: `Aspect_After.tif`.
* Hillshade [(documentation)](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/hillshade.htm).
  * Output raster: `Hillshade_After.tif`.

##### Create a pre-eruption hillshade.

1. Run the Hillshade tool again, this time derived from pre-eruption elevations.
2. Name it descriptively.

##### Extract the raster values for elevation, slope, and aspect for each of the viewpoints.

You could certainly do this manually, using the *Identify* tool you've used in a previous lab to find the the cell values below each viewpoint. You could even run the *Extract Values to Points* tool that you used in Lab 4 multiple times. However, there is a tool that can automate this some.

1. Read the documentation for [*Extract Multi Values to Points*](https://desktop.arcgis.com/en/arcmap/latest/tools/spatial-analyst-toolbox/extract-multi-values-to-points.htm)
2. Open the tool interface, in `ArcToolbox -> Spatial Analyst Tools -> Extraction`.
3. Choose your viewpoints shapefile as the input point features, and add your aspect, slope, and after DEM as your input rasters.
4. Optional: change the *Output field name* for each raster to something more readable. These are the fields that the tool will create on the viewpoints shapefile; you may want not wish to use the raster layer name for the field (e.g. maybe *elevation* makes more sense when on the viewpoints than *DEM_After*.
5. Run the tool.
6. Open the viewpoints attribute table and examine the values in the new fields.


#### 1.3 - 3D Scene Creation

ArcScene is another application in the ArcGIS Desktop suite of applications, alongside ArcMap. This application is a powerful tool for visualizing 3D data. We will only be using a small part of its capabilities.

##### Open ArcScene and create a new document.

1. Open ArcScene from the Windows *Start Menu*.
2. Choose *Blank Scene* from the *Getting Started* window prompt that appears.
3. Do an initial save of the document, to create the document in your `Lab6` folder. Name it similar to your ArcMap document.
4. Take a look around the application interface. This should all look familiar: where things are, how you access certain things is nearly the same as it is in ArcMap, with some considerations for displaying 3D space.

##### Add data to the scene document.

1. Add the following datasets.
  * Pre-eruption/before DEM.
  * Pre-eruption/before hillshade.
  * After-eruption DEM.
  * After-eruption hillshade.
2. Uncheck the DEM layers in the *Table of Contents* to stop displaying them. These layers are only added to provide information.

##### "Drape" the hillshade from the pre-eruption data over its respective elevation model.

1. Open the layer properties, and switch to the *Base Heights* tab.
2. Choose the `Floating on a custom surface` option for *Elevation from surfaces*.
3. Choose the pre-eruption DEM from the drop-down right below.
4. Repeat these steps for the after-eruption hillshade.

##### Move the "observer" around the scene for a better view.

1. Use the tools in the *Tools* toolbar to explore. Hovering the mouse cursor over a tool button for a second will display some explanatory text.
  * `Navigate` (tiny Earth with four triangles pointing out): Rotates the display around - click-and-hold, then move mouse.
  * `Fly` (a bird): Allows you to glide around the scene like a bird. Click the left mouse button to increase speed, right to decrease.
  * `Center on Target` (crosshairs): Recenters the display on wherever you click.
  * `Zoom to Target` (magnifying glass over crosshairs): Attempts to zoom up close to place you click on.
  * `Set Observer` (eye over crosshairs): Attempts to place observer (think of as where the camera would be) where you click.
  * `Zoom In`/`Zoom Out` (magnifying glass with plus or minus): Same concept as in ArcMap.
    * Can also be done whenever using mouse-wheel.
  * `Pan` (hand): Same concept as in ArcMap.
  * `Full Extent` (globe): Returns scene to extent showing all datasets.
    * Handy if you adjusted the view something crazy (e.g. couldn't control that flying).
2. Use the tools to change the view until you have a scene looking southward from the north into the crater.
  * You can turn on a helpful 3D orientation graphic via the menu item `View -> View Settings`, and checking-on `Directional Arrow`.
  * Note: *View Settings* also has the numeric representation of the current scene's view. You can change these here, but it's probably easier to do so with the tools mentioned instead.
3. Turn on & off the before hillshade to see the change the mountain underwent between then and the after-hillshade.

##### Save a 'before' and 'after' image of the scene.

1. Turn off all layers except the pre-eruption hillshade.
2. Export an image of the scene using the menu item `File -> Export Scene -> 2D`.
  1. Choose an image file type (PNG is good).
  2. Give it a descriptive filename, and save it to your Lab6 folder.
3. Repeat the previous steps for the after-eruption hillshade.


#### 1.4 Map and Infographic

The layout will contain:

* One map visualizing after-eruption elevation;
* Two images from the 3D scene (before and after);
* Information from each viewpoint as either labels or a table.

##### Develop the main map in the data frame.

1. Display the after-eruption hillshade with the default grayscale coloring.
2. Display the after-DEM above the after-hillshade. in drawing order.
  1. Make it partially-transparent: adjust `Layer Properties -> Display -> Transparency %`.
  2. Symbolize the DEM with a color ramp of your own choosing. to emphasize the elevation over the hillshade.
3. Display the contour lines so that they're visible.
  1. your call on over or under the transparent layer.
  2. Symbolize them to your satisfaction (color, width).
4. Display & symbolize the viewpoints layer.


##TODO: FINISH FROM HERE


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
