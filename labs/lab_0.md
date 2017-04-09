---
title: GEOG 4/581 - Lab 0
---

# Lab 0: Filesystem and Servers in SSIL


#### Purpose

A basic reference for interacting with files and connecting to servers from SSIL and the UO network. The topics in this lab appy to general Windows computer use, i.e. they are not about ArcMap or any other GIS applciations.


#### Prerequisites

To connect to the SSIL server, you will need your Duck ID & password, and be enrolled in the GEOG 4/581 course. You should have basic familiarity with using a personal computer.


#### References & Links

* SSIL Network Drives and Connecting Remotely.
  - [https://ssil.uoregon.edu/ssil/ssil-network-drives-and-connecting-remotely/](https://ssil.uoregon.edu/ssil/ssil-network-drives-and-connecting-remotely/)


#### To Turn In

Nothing: lab is for reference only.


#### Steps

*File Explorer* is an application available on the Microsoft Windows 10 operating system that allows you to view and modify the filesystem. Its functionality includes:

* Establishing a connection with a server's filesystem.
* Viewing the filesystem on the local computer and connected servers.
* Creating files and folders.
* Copying, moving, or deleting files.

### 1 - Open *File Explorer*

From the Windows Start Menu, type "explorer" and choose from the pick-list *File Explorer*.

Note: You can open a second window of the application using the keyboard shortcut `Ctrl+N` (meaning hold the Ctrl-button and press the N-button). A second window can be useful when moving files between folders.

### 2 - View the filesystem

The main display in *File Explorer* shows a list of the files in the current directory. You can navigate through the filesystem using the address bar at the top of the window, or using the folder tree displayed on the left side of the window.

### Connect to a server

The computers in the SSIL labs are configured to provide you with connections to the SSIL file server from the start. The file system is mapped to the R: drive. If you are working on a computer that has not already been connected, you will need to map the drive to the network location.

1. Open *File Explorer*. Make sure you are on 'This PC' in the folder tree.
2. Click the button labeled `Map Network Drive`.
3. Enter the server address: `\\cs-fs2\CAS-LABS\Classes`.

For additional information, see the [SSIL Network Drives and Connecting Remotely page](https://ssil.uoregon.edu/ssil/ssil-network-drives-and-connecting-remotely/)

Note: To connect to the server from off-campus, you will first need to connect to the UO VIrtual Private Network (VPN). Software and instructions for the VPN are available from the UO IT website: https://it.uoregon.edu/vpn

### 3 - Explore class-related server locations

Once connected to the R: drive, you should see a folder named 'GEOG481_3'. Within that folder are three folder that organize the course material.

* R:\GEOG481_3\Class_Data: Will contain copies of lab assignments and any supporting material.
* R:\GEOG481_3\Shared_Data: Will contain copies of any datasets referenced in a lab that are not publicly available on the internet.
* R:\GEOG481_3\Student_Data: Will contain a subfolder with your Duck ID (among others). This will be referred to regularly as your 'student folder'.

**IMPORTANT: Be sure to save your work to your student folder on the R: drive.** The SSIL computers will allow you to save files to the local computer's drives; however files on these drives are deleted regularly, and you should not count on them beyond the immediate time on that computer.

### 4 - Create folders

To create a new folder on the filesystem:

1. Open *File Explorer*.
2. Navigate to your student folder.
3. Right-click with the mouse in a blank area of the window.
4. Select `New->Folder` from the context menu that appears.
5. A folder will appear in the window. Type the name of the folder.

For each lab, you will create a new subfolder within your student folder. Name the new folder with the word 'Lab' followed by the lab number (e.g. Lab1); no spaces.

### 5 - Select, copy, move, delete, and rename

To select files or folders, you just need to single-click on them. To select more than one, you can:

* Click on one item, hold the shift key, then click on another. The two items plus any between them will be selected.
* Click on one item, hold the Ctrl key, and click on any others you wish to select. All clicked items will stay selected.
* Click and hold in a blank spot in the window, then drag across the items you wish to select.

Initiate copying selected items using the menu item `Home->Copy`, or use the keyoard shortcut `Ctrl+C`. Place the copies somewhere using `Home->Paste` or keyboard shortcut `Ctrl-V`. Be sure to have the window set to the location you want to place the copies in.

To move selected items, drag and drop the icon(s) into the destination folder as represented in the same window, the folder tree, or another window altogether. Alternatively, use the menu item `Home->Cut` of keyboard shortcut `Crtl-X` to initiate a move, then paste it with the same process as copying used.

To delete a selected item, you can: drag and drop it into the Recycle Bin icon; right-click the item and choose `Delete` from the context menu; or press the delete key.

**WARNING:** Non-local files (e.g. on the SSIL server) are permanently deleted when put in the Recycle Bin. This action cannot be undone.

### 6 - Extract files from an archive (zipfile)

Large files and collections of files available on the internet are often combined into a single file and compressed to save space. Once donwloaded, the file will need to be unpacked before its contents can be used. To extract the contents:

1. Open *File Explorer*.
2. Navigate to the location of the archive file.
3. Right-click on the filename, and select `Extract All` from the context menu.
4. Type the name of the folder to create & unpack to when prompted, and click `OK`.
