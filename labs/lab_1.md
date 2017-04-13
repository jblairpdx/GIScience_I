---
title: GEOG 4/581 - Lab 1
---

# Lab 1: Using GIS with ArcMap and SSIL


#### Purpose

Getting comfortable using the ArcMap software, and the SSIL computing environment.


#### Prerequisites

To connect to the SSIL server, you will need your Duck ID & password, and be enrolled in the GEOG 4/581 course. If for some reason your student folder has not been set up please see the SSIL lab attendant or your lab's Graduate Employee Teaching Assistant (GE).

You should have basic familiarity with using a personal computer; logging in, viewing files, and browsing the web. See the "Lab 0" document reference for navigating the Windows filesystem and SSIL servers for reference.


#### References & Links

* SSIL website.
  * [https://ssil.uoregon.edu/](https://ssil.uoregon.edu/)
* SSIL: GIS.
  * [https://ssil.uoregon.edu/arcgis-software/](https://ssil.uoregon.edu/arcgis-software/)
* ArcGIS Desktop: A Quick Tour of ArcMap.
  * [https://desktop.arcgis.com/en/arcmap/latest/get-started/introduction/a-quick-tour-of-arcmap.htm](https://desktop.arcgis.com/en/arcmap/latest/get-started/introduction/a-quick-tour-of-arcmap.htm)
* Oregon Spatial Data Library.
  * [http://spatialdata.oregonexplorer.info/geoportal/](http://spatialdata.oregonexplorer.info/geoportal/)


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

##### Read [*A Quick Tour of ArcMap*](https://desktop.arcgis.com/en/arcmap/latest/get-started/introduction/a-quick-tour-of-arcmap.htm) from the ArcMap documentation site.

##### Create a Lab1 folder in your student folder.

##### Download spatial datasets.

1. Open a web browser, and navigate to the [Oregon Spatial Data Library](http://spatialdata.oregonexplorer.info/geoportal/).
2. Browse or search for the following datasets:
  * *Oregon City Limits (2016)*: citylim_2016.zip.
  * *Oregon Counties - 2015*: orcnty2015.zip.
3. Download the files and save them in your student folder's newly-created Lab1 folder (e.g. `R:\GEOG481_3\Student_Data\[Duck ID]\Lab1\Data\orcnty2015.zip`).
4. Make a note of the data source. (Spatial) data has value, and you will want to give credit where due when creating maps or other documents. The data sources should be listed on every map you create.
5. Extract the dataset files from within the zipfiles for each dataset you downloaded.

##### Create a new ArcMap document (.mxd).

1. Open ArcMap from the *Windows Start Menu* (either by finding in the *Start Menu* folders, or by typing the name in the search bar).
2. Select *New Blank Map* from the *Getting Started* window that appears. Alternately, you can just close this window: it achieves the same thing.
3. Right away, save the document: from the top menus, select `File->Save As`, navigate to your Lab1 folder, and save as **Lab1_Oregon.mxd**.

##### Add data to the map.

When you create a new map document, ArcMap automatically creates an initial data frame. Data frames are used to organize the map's layout. Each data frame is shown in the layout as a rectangular element. In this lab we will work with a single data frame.

1. Tell ArcMap where to find the data.
  1. If not open already, open the *Catalog* panel from the menu `Windows->Catalog`.
    - Note: ArcMap panels can float over the main window or be docked along some edge of it. To move or dock the panel, grab (click & hold) the title part of the panel and move it to where you want it to float/dock. 
  2. Click the `Connect to Folder` button at the top of the panel (has a yellow folder with a + over it).
  3. Navigate the filesystem and select the Lab1 folder within your student folder, then click `OK`.
2. Add city limits to the map.
  1. Click the `Add Data` button from the *Standard* toolbar (has a yellow diamond with a + over it).
  2. Navigate the connected folders and select the city limits shapefile you downloaded, and clik `OK` (or just double-click on the file).
3. Add county boundaries to the map.
  1. In the *Catalog* display, navigate to the county shapefile you downloaded.
  2. Drag the shapefile and drop it onto the map window.
4. Observe the difference between how the shapefiles are represented between *Windows Explorer* and the *Catalog* panel.
5. Be sure to save your map document.

##### Organize and symbolize data.

Now that the those shapefile datasets have been added, they're now listed as *layers* in the *Table of Contents* panel (by default on the left of the screen). Under the title of the panel, there are five buttons, of which the first four control how the panel lists layers. Hover your cursor over any button to see its name, and a description of how it lists the layers. It's worth a moment to view these and understand what their purpose is.

1. While in the *List By Draw Order* version of the *Table of Contents* panel, drag the layers around to have the city limits draw on top of the county boundaries.
2. Set the colors for each layer.
  1. Open the *Symbol Selector* window for one layer.
    1. Click on the mini-symbol in the *Table of Contents*.
    2. Alternatively, open the layer properties (double-click on the name or right-click the name and choose `Properties`); then open the `Symbology` tab, then click on the symbol there.
  2. Select a preferred color.
    1. ArcMap provides a set of preset area symbols (fill and outline) on the left side of the *Symbol Selector* window.
    2. You can also individually set *Fill Color*, *Outline Color*, and *Outline Width* on the right. Opening these will display a color palette you may choose from.
    3. If you're still not satisfied, you may choose `More Colors` at the bottom of each palette to opens a *Color Selector*, which will allow you to manipulate individual color components.
  4. Color the counties a subtle color; the cities a bold & contrasting color. Use your judgment; feel free to experiment, and try a number of combinations.
3. Rename the layers to something better for display.
  1. When a dataset is added as a layer, it usually defaults to a version of the file name for the layer name. These can be obtuse for having on maps, so renaming them is a common step.
  2. Open the layer properties (see above), and select the *General* tab.
  3. Write your improved name in the *Layer Name* section.

4. Be sure to save your map document.

##### Create a layout.

1. Open the page settings from the menu `File->Page and Print Setup`.
  1. Set the size.
    1. Choose the paper size *Letter*.
    2. Choose a matching print size: either type the dimensions to match, or check *Use Printer Paper Settings*.
  2. Choose the page orientation *Landscape* or *Portrait* to suit your intended design by clicking the associated button.
  3. Click `OK` to save these settings.
2. Switch to *Layout View* using the menu item `View->Layout View`. Alternatively, there is two buttons in the lower-left corner of the map area to switch between *Layout View* and *Data View* (what you were in).
3. Adjust the size & position of the map by clicking on the map data frame and dragging the handles (the 'knobs' that appear on the outer boundary of the rectangle).
4. Adjust the display of the data frame so it is centered on Oregon using the *Pan* tool. This is the hand button on the *Tools* toolbar.
5. Use the *Zoom* tools to get the entire state of Oregon with a margin on all sides. These tools are the magnifying glass buttons on the *Tools* toolbar.
  1. Clicking on the map after activating the *Zoom* tool will center the map and zoom in/out some.
  2. Holding a click and dragging away from that spot will draw a rectangle which the data frame will zoom and center on.
6. You'll notice that when you switched to *Layout View* that a new toolbar appeared. This is the *Layout* toolbar. The buttons on it are strikingly similar to the ones on the *Tools* toolbar. This is because they perform the same functions, but affecting the view of the page in the layout, and not the view of the data in the frame. Much grief will come from confusing the two.
7. Add standard map elements:
  1. A title using the menu item `Insert->Title`.
  2. A text element with the author, or cartographer (your name): `Insert->Text`.
  3. A text element with the data source.
  4. A north arrow: `Insert->North Arrow`.
  5. A scale bar: `Insert->Scale Bar`. After adding it to the map, adjust the size so that the labels for the total length & subdivisions are whole numbers.
  6. Adjust the size and position of these elements to improve the look & readability of your map.
    - Click on an element to select it.
    - Drag a handle to resize the element.
    - Drag inside the borders to move it without resizing. You can also use the arrow keys to move the element after selecting.
    - Properties of an element can be viewed & modified by double-clicking on the element.

8. Be sure to save your map document.

##### Make a PDF copy of your map.

ArcMap map documents (MXD files) are not particularly portable documents; they not only require a not-very-common application to view, they also require the underlying datasets to be reachable by whoever opens them. For that reason, a number of formats are available for converting the layout into.

1. Open the file export dialog: `File->Export`.
2. Set the output file type: `PDF`.
3. Set the output filename: `Lab1_Oregon.pdf`, and click `OK`.
4. Take a look at your exported PDF through a PDF viewing application or a web browser. **Always look at your output!** Both common and unusual errors slip past creators when they don't look at their outputs.


### Part 3 - Write-up

**Note:** Some of the questions in the write-up relate to the actions you take in making your map; you may find it helpful to answer those questions as you go, rather than waiting until after completion.

##### Instructions

1. Copy & paste the questions below into a document in your preferred word processor/text editor.
  * Be sure to use a commonly-viewable document format, e.g. Word, rich text, markdown.
2. Compose your answers for each question in the document following each question.

##### Questions

1. How many files were contained in the downloaded file *citylim_2016.zip*?
2. What types of files were contained in the downloaded file *citylim_2016* and what data does each one contain? Hint: look at the file extensions and do a web search, e.g., Google or Wikipedia, to find out what they mean.
3. Looking at your final map, what pattern(s) do you notice in the data? How might these perceived patterns change if you plotted cities as points rather than showing the city limits? (1-2 sentences)
4. What changes would you make in a future version of the map to make it easier to read or interpret? (1-2 sentences; there are always changes that can be made, take some time to think and be creative)
5. What happens to files that are saved on the C:\\ drive when you log out of the computers in SSIL?

