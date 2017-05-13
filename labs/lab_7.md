---
title: GEOG 4/581 - Lab 7
---

# Lab 7: Vegetation Landscapes Report


#### Purpose

A major part of GIS analysis is preparing the data—combining data from diverse sources and extracting portions of a larger dataset that apply to a specific question. This week we will be working with attribute joins in ArcMap, as well as extracting data based on spatial overlap. In Lab 5 where you chose a selection method that best approximated the tsunami's impact zone; those techniques could over- or underestimate, including or excluding taxlots that were only partially touched by the tsunami layer. This lab you will perform spatial operations that will use polygon overlay to exactly match the area of overlap between two sets of polygons.

This lab explores attribute joins and polygon overlays using vegetation layers to illustrate the ideas.


#### Prerequisites

This excercise builds on skills practiced in Labs 1-6.


#### References & Links

* ArcGIS Desktop: Calculate Field examples.
  * [https://desktop.arcgis.com/en/arcmap/latest/manage-data/tables/calculate-field-examples.htm](https://desktop.arcgis.com/en/arcmap/latest/manage-data/tables/calculate-field-examples.htm)
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
* **A short report** (3-4 pages) describing the GIS analysis conducted and the conclusions you found.

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
4. Make a copy of the commas-separated value (CSV) file `R:\GEOG481_3\Class_Data\Lab7\gapcodes.csv` in your `Lab7` folder.

Comma-separated value files are text files that are formatted to represent a table of attribute values. They use commas as "separators", dividing each row (represented as individual lines in the text) into columns/fields. Usually, the first row-line holds the field names. I encourage you to open up the file in both the Notepad and Excel applications, to see a raw and formatted version of the data stored within.

Additionally, as part of your map design you should locate additional data layers to provide context. For example, you may want to use Oregon and adjacent state boundaries, county boundaries, rivers, roads, cities, etc. for that purpose. You've been introduced to a numbers of good resources for these purposes: Oregon Spatial Data Explorer, UO MAP Library Learning Commons, and Natural Earth Data to name a few. Use your judgment and what you've been shown in class to choose helpful data layers for your map.

#### 1.2 GIS Analysis & Processing

This GIS analysis will prepare for a comparison between modern and historic vegetation in a specific ecoregion of Oregon. In the first part of the analysis, you will explore and summarize the modern data. In the second part, you will repeat the process for the historic data; but you will need to do a bit of additional manual work to augment the historic data so that it will be comparable to the modern data. The original datasets include a name (or code) describing the vegetation; the comparison will be based on the corresponding landscape types.

##### Create a new ArcMap document.

1. Name it `Lab7_Vegetation_Land_Cover.mxd`.
2. Add the ecoregion data to the data frame, and restrict the dataset to an ecoregion of your choice.
  * Remember, you can use a *Definition Query* to filter the original data, or perform a selection for the ecoregion and export the single ecoregion to a new shapefile.
3. Add the modern vegetation data to the data frame: `R:\GEOG481_3\Class_Data\Lab7\gap_vegetation.shp`.
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

##### Read [*Dissolve*](https://desktop.arcgis.com/en/arcmap/latest/tools/data-management-toolbox/dissolve.htm) from the ArcMap documentation site.

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

Unlike the modern vegetation, the historic vegetation dataset does not carry the vegetation codes (`VEG_CODE`), or use the same names of the modern version. So we'll need to create a lookup table specifically to match historic vegetation names to landscape types.

1. Open the attribute table of the historic vegetation layer.
2. Right-click on the `VEGNAME` field name and choose `Summarize`. Accept the defaults.
3. Open the *Saving Data* dialog via the button that looks like a folder.
4. In *Save as type* choose `Text File`. This will save it as a csv.
5. Give it a descriptive name and save it. Make sure you give it the file extension `.csv` instead of the default `.txt`.
6. Find the file in File Explorer and open it with the *Notepad* application (`right-click -> Open With -> Notepad`).
  * This is the underlying setup of a CSV-file. It's just text, with columns separated by commas. The applications do all the organizing and data typing work.
7. Now open the CSV file in Excel (this is the default application for that type).
8. Remove the `FID` and `Cnt_VEGNAME` columns; they unnecessary bits the *Summarize* tool added on.
9. Title a new column `Landscape Type` (just like in `gapcodes.csv`).
10. Open the other CSV file, `gapcodes.csv`, and place it side-by-side with the historic one you're completing.
  * Recent Excel versions open multiple files in the same application window, which makes this slightly more difficult. To place them side-by-side, either (a) Go to the *View* tab on the Excel option ribbon, and choose `Arrange All`. The *Vertical* option will place all spreadsheets side-by-side; or (b) open an entirely new instance of Excel from the application menu, and open the other CSV in that.
11. Using the modern GAP codes as a guide, copy/type the Landscape type that you believe would correspond to each historic vegetation type.
12. Once finished, save the CSV file. You will get a warning about CSV files not being able to save all features of Excel spreadsheets; click `Yes` to keep the format.
13. Add the CSV file to your historic data frame.

**Matching note**: Some of the text descriptions may be quite easy for human eyes to match between the GAP and historic vegetation. For example, `Sitka sprice-western hemlock` is quite comparable to `Sitka-Spruce-W. Hemlock Maritime Forest`; this could then be given the corresponding landscape type: `FOREST AND WOODLAND`. Others may not correspond so easily, but have an obvious landscape: if it talks only about trees (forest), if it highlights grass or shrubs, or if it highlights riparian or wetland components. Others may require more research—look up tree species or terms you're not familiar with to get a better picture.

##### Create a new historic landscape type feature class for your chosen ecoregion.

1. Join the historic CSV table you created to the historic vegetation, just as you had above excepting the join this time will be based on the `VEGNAME` field in the shapefile and table.
2. Dissolve the joined datasets into a dataset of landscape features, just as you had above. Don't forget to sum the newly-calculated area.

##### Create a landcover area change table.

1. Create a summary table of the landscape type on the historic vegetation layer, including the sum of your newly-calculated area.
2. Create a summary table of the landscape type on the modern vegetation layer, including the sum of your newly-calculated area.
3. Look at the two summary tables; are there any landscape types on one table that aren't represented on the other? If so, you need to edit the table and add new rows for them in the table.
  * Edit session: `Editor toolbar -> Editor menu -> Start Editing`.
  * If a landscape isn't represented initially, that's because it doesn't cover that ecoregion in that dataset. Hence, area = 0.
3. Join the two summary tables. In this case, the join will have a one-to-one relationship (i.e. only one row in each table for each landscape type), so it doesn't matter which is the *source table* or the *destination table*.
4. Export the joined summary tables as a new 'landscape change' table. Save it as a dBase file.
  * You may want to 'turn off' some of the unecessary fields before exporting.
5. The unfortunate part of using shapefiles and dBase tables is that we can't rename fields in our datasets. Let's replace the badly named fields with better-named ones.
  * Look at the field properties for ones you would like to replace, identifying the *Type*.
  * Add a new field of the same type, but with a better name.
  * Open the *Field Calculator* (right-click on the new field's name in the attribute table & select).
  * Double-click on the name of the field you are going to replace. Once you click `OK`, this will copy the values of the old field into the new one.
  * Once you've moved the values to the new field, you can choose to hide or delete the field.
  * Repeat these steps for any other fields you wish to rename.
5. Add a new floating point (or double) fields for percent change in area (`pct_change`).
6. Use the *Field Calculator* to calculate the percent change in area between the historic and modern dataset.
  * Right-click on the field name in the attribute table to find the *Field Calculator*.
  * This tool operates similarly to the *Query Builder* used for selecting with SQL syntax; however this uses *VB Script* (default) or *Python* scripting syntax, which are different enough to make things difficult for unfamilar users. Don't sweat it, the math is written how you would expect it to be, with standard symbols.
  * Percent change: ([modern area field] - [historic area field]) / [historic area field] * 100

Warning! If your ecoregion has a landscape type that didn't exist in the historic dataset (but does in the modern), you'll notice the value in `pct_change` didn't change from `0`. This isn't because that's the answer: it's because the *Field Calculator* skipped over it because your equation asked it to divide by zero, which is impossible in math. The percent increase from 0 to anything is uncalculable because of this. Be aware of this when working on your report.

If you are interested in learning more about how to build field calculations, I encourage you to read [*Calculate Field examples*](https://desktop.arcgis.com/en/arcmap/latest/manage-data/tables/calculate-field-examples.htm) from the ArcMap documentation site.

#### 1.3 Map and Data Graphics

The products of this lab will be a one-page map layout to accompany a short document. The map layout can be designed with your choice of paper size and orientation (landscape or portrait). You may choose to include additional maps, data graphics, or tables in your layout or short document as needed to illustrate the narrative.

* Be sure to include all necessary map elements as discussed in [lectures 10 and 11](https://jblairpdx.github.io/GIScience_I/slides/lecture_10_11.html).
* We also discussed controlling factors on map design, visual variables, thematic symbolization types, visual hierarchy, and things to do for better maps. Take your newfound knowledge fromn those lectures and the readings, and apply them to creating a map layout that communicates the analysis you performed and the document it accompanies.
* Tip: I highly recommend working on any color schemes using the [ColorBrewer web app](http://colorbrewer2.org/).
  * When changing a color in ArcMap, you'll see the option below the color picker for *More Colors*. A *Color Selector* will appear with prompts for the red, green, and blue (RGB) values to mix into the color. You can switch the ColorBrewer colors from `HEX` to `RGB` to see the numbers you can enter in the *Color Selector*.

##### Make a PDF copy of your map.

1. Filename: `Lab6_Mt_St_Helens.pdf`.
2. Take a look at your exported PDF through a PDF viewing application or a web browser. **Always look at your output!** Both common and unusual errors slip past creators when they don't look at their outputs.


### Part 2 - Write-up

In contrast to previous weeks, you will write a short report instead of answering questions provided here. The report should be 3-4 pages double-spaced. 

The content should describe the GIS analysis conducted and the results of that analysis. It should be organized in a way that is easy to follow, *avoids excessive technical detail and jargon* (or defines any jargon used), and uses complete sentences.

The report may include a description of steps where you made decisions (e.g. what selection method was used, how you solved problems assigning landscape types, etc.), or where you had to be creative in finding solutions/avoiding pitfalls.

In addition to the narrative, the report may optionally contain small maps, data graphics, or data tables.

Sources of GIS data should be listed on the map layout. If the data from a GIS source is used to create a figure, map, table, or graphic in the report, list the data source in the caption of that figure.
