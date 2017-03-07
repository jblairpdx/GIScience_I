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
  - [https://ssil.uoregon.edu/](https://ssil.uoregon.edu/)
* SSIL: GIS.
  - [https://ssil.uoregon.edu/arcgis-software/](https://ssil.uoregon.edu/arcgis-software/)
* ArcGIS Desktop: A Quick Tour of ArcMap.
  - [https://desktop.arcgis.com/en/arcmap/latest/get-started/introduction/a-quick-tour-of-arcmap.htm](https://desktop.arcgis.com/en/arcmap/latest/get-started/introduction/a-quick-tour-of-arcmap.htm)
* Oregon Spatial Data Library.
  - [http://spatialdata.oregonexplorer.info/geoportal/](http://spatialdata.oregonexplorer.info/geoportal/)


#### To Turn In

* Single-page map in Portable Document Format (PDF).
* Written document with lab questions in a commonly-accessible format (Microsoft Word, rich text, markdown, etc.)

Submit the documents to the class Canvas page as listed under the lab assignment within the first ten minutes of the start of the next lab.


#### Steps

For best results, read through all instructions before starting the lab.

Note: The questions to answer in this lab relate to the process you complete in these steps. You may find it helpful to answer questions as you create the map rather than waiting until the end. Whichever method you prefer, be sure to contemplate *what you are actually doing* while completing these steps. Remember: the skill is not in following directions (or memorizing them), it's understanding what is happening.

### 1 - Map Instructions

##### Read [*A Quick Tour of ArcMap*](https://desktop.arcgis.com/en/arcmap/latest/get-started/introduction/a-quick-tour-of-arcmap.htm) from the ArcMap documentation site.

##### Create a Lab1 folder in your student folder.

##### Download spatial datasets.

1. Open a web browser, and navigate to the [Oregon Spatial Data Library](http://spatialdata.oregonexplorer.info/geoportal/).
2. Browse or search for the following datasets:
  - *Oregon City Limits (2016)*: citylim_2016.zip.
  - *Oregon Counties - 2015*: orcnty2015.zip.
3. Download the files and save them in your student folder's newly-created Lab1 folder (e.g. R:\GEOG481\<Duck ID>\Lab1\Data\orcnty2015.zip).
4. Make a note of the data source. (Spatial) data has value, and you will want to give credit where due when creating maps or other documents. The data sources should be listed on every map you create.
5. Extract the dataset files from within the zipfiles for each dataset you downloaded.

##### Create a new ArcMap document (.mxd).

1. Open ArcMap from the *Windows Start Menu* (either by finding in the *Start Menu* folders, or by typing the name in the search bar).
2. Select *New Blank Map* from the *Getting Started* window that appears. Alternately, you can just close this window: it achieves the same thing.
3. Right away, save the document: from the top menus, select *File->Save As*, navigate to your Lab1 folder, and save as **Lab1.Oregon.mxd**.

##### Add data to the map.

When you create a new map document, ArcMap automatically creates an initial data frame. Data frames are used to organize the map's layout. Each data frame is shown in the layout as a rectangular element. In this lab we will work with a single data frame.

1. Tell ArcMap where to find the data.
  1. Click
