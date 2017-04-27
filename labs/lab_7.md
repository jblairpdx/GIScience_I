---
title: GEOG 4/581 - Lab 7
---

# Lab 7: Vegetation Land Cover Report


#### Purpose

A major part of GIS analysis is preparing the data—combining data from diverse sources and extracting portions of a larger dataset that apply to a specific question. This week we will be working with attribute joins in ArcMap, as well as extracting data based on spatial overlap. In Lab 5 where you chose a selection method that best approximated the tsunami's impact zone; those techniques could over- or underestimate, including or excluding taxlots that were only partially touched by the tsunami layer. This lab you will perform spatial operations that will use polygon overlay to exactly match the area of overlap between two sets of polygons.

This lab explores attribute joins and polygon overlays using vegetation layers to illustrate the ideas.


#### Prerequisites

This excercise builds on skills practiced in Labs 1-6.


#### References & Links

* ArcGIS Desktop: Clip.
  * [https://desktop.arcgis.com/en/arcmap/latest/tools/analysis-toolbox/clip.htm](https://desktop.arcgis.com/en/arcmap/latest/tools/analysis-toolbox/clip.htm)
* ArcGIS Desktop: Dissolve.
  * [https://desktop.arcgis.com/en/arcmap/latest/tools/data-management-toolbox/dissolve.htm](https://desktop.arcgis.com/en/arcmap/latest/tools/data-management-toolbox/dissolve.htm)
* ArcGIS Desktop: Joining attributes in one table to another.
  * [https://desktop.arcgis.com/en/arcmap/latest/manage-data/tables/joining-attributes-in-one-table-to-another.htm](https://desktop.arcgis.com/en/arcmap/latest/manage-data/tables/joining-attributes-in-one-table-to-another.htm)
* Oregon Spatial Data Library.
  * [http://spatialdata.oregonexplorer.info/geoportal/](http://spatialdata.oregonexplorer.info/geoportal/)


#### To Turn In

* Single-page map in Portable Document Format (PDF).
* **A short report** describing the GIS analysis conducted and the conclusions you found.

Put a copy of each document:

1. Inside the `Lab#` subfolder in your student folder. It's simplest to just complete the original documents here.
2. Uploaded to the class Canvas site as listed under the lab assignment.

Submit the documents at your earliest convenience before the start of the next lab.


#### Steps

For best results, read through all instructions before starting the lab.


### Part 1 - Map Instructions

Reminder: Save often! it is a good idea to save frequently. You may even want to Save As and give sequential filelenames so that you could revert to a previous version if you make a mistake that you cannot undo or if the ArcMap document gets corrupted.

#### 1.1 - Data

##### Create a new `Lab7` folder, and download spatial datasets there.

Discover and download the datasets via the link provided. Be sure to note the data source, in order to provide citations on your map.

1. Open a web browser, and navigate to the [Oregon Spatial Data Library](http://spatialdata.oregonexplorer.info/geoportal/).
2. Browse or search for the following datasets:
  * *Oregon Historic Vegetation*: `historic_vegetation.zip`.
  * *Oregon Ecoregions*: `ecoregion.zip`.
3. Download them to your lab folder, and extract their contents.
4. Make a copy of the commas-separated value (CSV) file `R:\GEOG481_3\Class_Data\Lab7\Data\gapcodes.csv` in your `Lab7` folder.

Comma-separated value files are text files that are formatted to represent a table of attribute values. They use commas as "separators", dividing each row (represented as individual lines in the text) into columns/fields. Usually, the first row-line holds the field names. I encourage you to open up the file in both the Notepad and Excel applications, to see a raw and formatted version of the data stored within.

Additionally, as part of your map design you should locate additional data layers to provide context. For example, you may want to use Oregon and adjacent state boundaries, county boundaries, rivers, roads, cities, etc. for that purpose. You've been introduced to a numbers of good resources for these purposes: Oregon Spatial Data Explorer, UO MAP Library Learning Commons, and Natural Earth Data to name a few. Use your judgment and what you've been shown in class to choose helpful data layers for your map.

#### 1.2 GIS Analysis & Processing

This GIS analysis will prepare for a comparison between modern and historic vegetation in a specific ecoregion of Oregon. In the first part of the analysis, you will explore and summarize the modern data. In the second part, you will repeat the process for the historic data; but you will need to do a bit of additional manual work to augment the historic data so that it will be comparable to the modern data. The original datasets include a name (or code) describing the vegetation; the comparison will be based on the corresponding landscape types.

##### Create a new ArcMap document.

1. Name it `Lab7_Vegetation_Land_Cover.mxd`.
2. Add the ecoregion data to the data frame, and restrict the dataset to an ecoregion of your choice.
  * Remember, you can use a *Definition Query* to filter the original data, or perform a selection for the ecoregion and export the single ecoregion to a new shapefile.
3. Add the modern vegetation data to the data frame: `R:\GEOG481_3\Class_Data\Lab7\Data\gap_vegetation.shp`.
  * This is a rather large file, so we're going to not make a copy in each lab folder.
4. Rename the data frame to reflect its contents, e.g. 'Modern Vegetation'.

##### Read [*Clip*](https://desktop.arcgis.com/en/arcmap/latest/tools/analysis-toolbox/clip.htm) from the ArcMap documentation site.

##### Extract vegetation data within the chosen ecoregion.

Execute the *Clip* tool to extract the vegetation in the chosen ecoregion. *Clip* is located in the ArcToolbox panel, as `Analysis Tools -> Extract -> Clip`.

##### Recalculate the area for each vegetation polygon

The attribute table for the vegetation has a field called `AREA`. However, this is not an automatically-updated attribute. For features that extended beyond the ecoregion, the *Clip* tool removed the parts outside the ecoregion's polygon interior. Therefore, the attribute value in `AREA` is no longer accurate for those features.

1. Add a new field to the attribute table of the feature class.
  1. Open the attribute table.
  2. Under *Table Options* (the button on the attribute table that looks like a paper with holes & lines in it), choose `Add Field`.
  3. Provide a short name for the field; shapefiles are limited to 10 character names. Tip: you may want to include the units in your field name, so you can better remember them later, e.g. `area_sqmi`/`area_sqkm`.
  4. Choose an appropriate attribute data type to store the area values for the polygons. Remember, `Float` and `Double` are names for decimal number attribute types.
  5. After creating the field, scroll to the right end of the attribute table, which is where new fields are added.
  6. Right-click on the name of the new field, and choose `Calculate Geometry`.
  7. You should receive a warning that you're calculating attribute values outside an 'edit session'. Read the warning to understand its point, but go ahead and choose `Yes`.
  8. Choose `Area` as the property, and specify your desired units (I recommend sqaure miles or kilometers, or you'll be dealing with very large numbers).

Tip: You can rearrange (in ArcMap) the order of fields by clicking on the field name in the table and dragging it to the right or left of other fields columns. Additionally, you can 'freeze' (or 'unfreeze') a column in a visible place, or 'turn a field off' by right-clicking on a field name in the table and choosing the corresponding option. Turning a field back 'on' can be done via `Layer Properties -> Fields`.

##### Read [*Joining attributes in one table to another*](https://desktop.arcgis.com/en/arcmap/latest/manage-data/tables/joining-attributes-in-one-table-to-another.htm) from the ArcMap documentation site.

Tip: When reading ArcMap documentation pages, notice that there is a hierarchy of the documentation contents on the left side of the page. Other pages under the same section heading may also be helpful in understanding what the tools do and how to use them; or perhaps have information for related tools and operations. For example, the section with the above page also has one titled *Esssentials of joining tables* which may be useful in better understanding the join operations.

##### Join the land cover type to the the vegetation features.

1. Add the CSV file table `gapcodes.csv` that you copied to your `Lab7` folder to the data frame.
2. Right-click on the clipped vegetation layer, and choose the menu item `Joins and Relates -> Join`.
3. Fill in the options in the *Join Data* window. Base the join on the numeric code for the vegetation type (`VEG_CODE` on the vegetation layer, `VALUE` in the GAP codes CSV table), and keep all the records.
4. You may choose run the `Validate Join` tool at the bottom beforehand; this just checks to ensure the join will work as advertised. In this case, it will warn you about using a 'reserved word', `VALUE`. Don't worry about this, just `OK` the join.
5. View the layer's attribute table and observe the joined attribute fields. Temporarily turn off the field aliases (`Table Options -> Show Field Aliases`) to see the field names with the table name attached.

Tip: To remove a joined attribute table, ricght-click on the layer with the join, and look under `Joins and Relates -> Join -> Remove Join(s)` for the table in question.

##### Read [*Dissolve*](https://desktop.arcgis.com/en/arcmap/latest/tools/analysis-toolbox/clip.htm) from the ArcMap documentation site.

##### Combine the vegetation features into new landscape type features.

1. Execute the *Dissolve* tool to combine vegetation features in the ecoregion that have the same landscape type. *Dissolve* is located in the ArcToolbox panel, as `Data Management Tools -> Generalization -> Dissolve`.
  * Choose the joined field `Landscape_Type` for the *Dissolve Field(s)*.
  * Include the new area field you calculated values for as the sole *Statistics Field(s)*, with a *Statistic Type* as `SUM`. **Important**: If you don't do this, you will not have the collected area of the newly-merged features, and will have to calculate it again.
  * *Create multipart features*. This option will unify all features with matching dissolve fields, even if they aren't adjacent to each other. This creates 'multipart' features, or features with more than one point/line/polygon representing them. Keep it checked.
2. Open the attribute table; notice that only the dissolve field(s) and statistics field(s) are present in the output. They also may have strange & truncated names. This is because (a) joined fields when exported try to include the table name, (b) statistics fields prefix the statistic type to their name, and (c) shapefiles limit field names to ten characters. Options for handling these screwy names:
  * Change the field name alias via the *Field Properties*—right-click on the field name in the attribute table, choose `Properties`.
  * Change the field name alias via the *Fields* tab in the layer properties.
  * Create a new field with the same data type, and calculate the values from one field to another. This is the only option that changes the underlying shapefile, but it's also the most work.

##### Insert a new data frame for historic vegetation of the ecoregion.

1. Name it to reflect its contents, e.g. 'Historic Vegetation'.
2. Copy your chosen ecoregion layer over from the modern data frame.
3. Add the historic vegetation data you downloaded to the data frame.
4. Extract the vegetation data in your chosen ecoregion—just as you did above for the modern vegetation.
5. Create a new area field and calculate the attribute values for it—just as you did above for the modern vegetation.
  * Use the same units as the modern vegetation!

##### Create a 'lookup' table similar to `gapcodes.csv` to match historic vegetation to landscape types.

Unlike the modern vegetation, the historic vegetation dataset does not carry the vegetation codes (`VEG_CODE`), or use the exact names of the modern version. So we'll need to create a lookup table specifically to match historic vegetation names to landscape types.

1. Open the attribute table of the historic vegetation layer.
2. Right-click on the `VEGNAME` field name and choose `Summarize`. Accept the defaults.
3. Open the *Saving Data* dialog via the button that looks like a folder.
4. In *Save as type* choose `Text File`. This will save it as a csv.
5. Give it a descriptive name and save it.
6. Find the file in File Explorer and open it with the *Notepad* application (`right-click -> Open With -> Notepad`).
  * This is the underlying setup of a CSV-file. It's just text, with columns separated by commas. The applications do all the organizing and data typing work.
7. Now open the CSV file in Excel (this is the default application for that type).
8. Remove the `FID` and `Cnt_VEGNAME` columns; they unnecessary bits the *Summarize* tool added on.
9. Title a new column `Landscape Type` (just like in `gapcodes.csv`).



##TODO: FINISH FROM HERE; INCLUDE A COLORBREWER PART.


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
2. Display the after-DEM above the after-hillshade in the drawing order.
  1. Make it partially-transparent: adjust `Layer Properties -> Display -> Transparency %`.
  2. Symbolize the DEM with a color ramp of your own choosing, to emphasize the elevation atop the hillshade.
3. Display the contour lines so that they're visible.
  1. your call on over or under the transparent elevation layer.
  2. Symbolize them to your satisfaction (color, width).
4. Display & symbolize the viewpoints layer. Be sure to have them stand-out from the background.
5. Add labels to the viewpoints that display the elevation, slope, and aspect a that location.
  1. Navigate to the *Labels* tab in the viewpoints' layer properties.
  2. Check the box for *Label features in this layer*.
  3. Click on the `Expression` button to open the *Label Expression* builder. At the bottom of the window, choose `Python` for the *Parser*. VBScript works fine, but it can't do newlines, and we want stacked labels.
  4. Label expressions are an arcane black magic that combines the parser scripting language with field name tokens that will insert the attribute values where placed. It can be frustrating when the expression doesn't do what you want (or is declared invalid). I would recommend just altering the expression below, changing the field names if they do not match what you labelled them on your viewpoints.
6. Adjust the label formatting to improve their readability & presence.
  1. Go back to the *Labels* tab in the layer properties.
  4. Click on the `Label Styles` button. This will show a list of pre-defined label styles. These are a good starting place to adjust labels from. I recommend for labels overlaying the rich raster information below to use one of the *Banner* styles.
  2. Adjust the font type and size to improve readability. If you change the font, be sure it matches or contrasts with the other text elements in your layout in a satisfying or meaningful way (i.e. don't use different fonts unless you have a good reason to).
  3. You may adjust the font color as well, but beware reducing readability.
  4. You may also adjust the banner box color as well, though it's kind of buried. `Layer Properties -> Labels -> Symbol -> Edit Symbol -> Advanced Text -> Text Background (check) -> Properties -> Symbol`.
7. Welcome to cartography: there's thousands of potential tweaks great and small, and you not only have to decide which to do (or undo), but you also have to avoid spending too much time on them.

```python
# Just use the bottom line for the label expression.
# Brackets contain the field names; single- or double-quotes can contain literal text.
# '\n' is a signifier to Python to start a new line.
'Elevation: ' + [DEM_After] + '\nSlope: ' + [Slope] + '\nAspect: ' + [Aspect] 
```

##### Place the map in the layout.

1. Switch to *Layout View*.
2. Change the paper size to 'tabloid'/11"x17", and choose an orientation: *Portrait* (tall) or *Landscape* (wide). Note: since you will be submitting your map digitally, you can consider the size setting optional. However, there are a few things that layout page size affects even in unprinted maps:
  1. Layout units: the edge rulers and every object's size & position use the page units; larger page = larger range.
  2. Relative size of text & symbols to page; larger page = larger range.
3. Resize and place the data frame on the page how you think best displays them for viewers. Be sure to leave room for the other map and layout elements (you can always make adjustments at any time).
  1. Consider different sizes for the map.
  2. Consider vertical & horizontal lengths: your map's extent may not be easily represented in a square.
  3. You may need to pan & zoom within the data frame to make sure you're showing all you wish at the right scale.
3. Once you've set the data frames' size, placement, and extent, you may want to re-evaluate your symbolization within your data frame.

##### Place the images in the layout.

1. Add the two 3D scene images.
  1. Select the menu item `Insert -> Picture`.
  2. Navigate to one of the images in your `Lab6` folder and choose it.
  3. Repeat for the second image.
2. Resize and place the images on the page how you think best displays them for viewers.
  1. Picture properties are accessible in the same way as a data frame's properties are in *Layout View* (double-click on the picture, or right-click on it and choose `Properties`).
  2. Be sure when resizing an image to have the option `Preserve Aspect Ratio` checked; this will ensure that when changing the width or height, the other value will automatically change in a way that won't warp the image.
  3. Consider their relationship with the other elements, and how they fit in the visual hierarchy of the entire map product.
3. Add a border around the images. Border setting are in the *Picture Properties* window. Style it (thickness/color) as seems appropriate for their role in the map product.

Explore layout designs, finding a way to use the available space. Don't leave gaping holes, but also leave enough empty space so the layout doesn't seem overly crowded. This is an iterative process.

##### Add elements for the maps & layout.

This week, we discussed map composition and the elements of a map product in lecture. Refer to the lecture slides or your notes, and apply this newfound knowledge to create, style, and place the necessary elements in your layout here.

Note: Don't include the hillshade's symbology in the map legend.

##### Make a PDF copy of your map.

1. Filename: `Lab6_Mt_St_Helens.pdf`.
2. Take a look at your exported PDF through a PDF viewing application or a web browser. **Always look at your output!** Both common and unusual errors slip past creators when they don't look at their outputs.


### Part 2 - Write-up

**Note:** Some of the questions in the write-up relate to the actions you take in making your map; you may find it helpful to answer those questions as you go, rather than waiting until after completion.

##### Instructions

1. Copy & paste the questions below into a document in your preferred word processor/text editor.
  - Be sure to use a commonly-viewable document format, e.g. Word, rich text, markdown.
2. Compose your answers for each question in the document following each question.

##### Questions

1. Describe what information is represented by the DEM (1-2 sentences). Consider: the spatial representation; the data model; the attribute value type/measurement scale; as well as what the values represent.
2. What sort of output does the `Contour` tool create: what is created, and what does it represent?
3. In your own words, describe what the values in a `slope` and `aspect` raster dataset represent (2-3 sentences).
4. In your own words, describe what the `hillshade` is representing.
5. Briefly describe the spatial analysis you conducted in this lab. Describe the purpose of the steps, rather than the technical details of them—pretend you are describing this to someone who does not know GIS. (4-5 sentences).
