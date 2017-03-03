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
  - https://ssil.uoregon.edu/ssil/ssil-network-drives-and-connecting-remotely/


#### To Turn In

Nothing: lab is for reference only.


#### Steps

*Windows Explorer* is an application available on the Microsoft Windows operating system that allows you to view and modify the filesystem. Its functionality includes:

* Establishing a connection with a server's filesystem.
* Viewing the filesystem on the local computer and connected servers.
* Creating files and folders.
* Copying, moving, or deleting files.

### 1 - Open *Windows Explorer*

From the Windows Start Menu, type "explorer" and choose from the pick-list *Windows Explorer*. You can also click the folder icon on the menu bar.

Note: You can open a second window of the application using the keyboard shortcut Ctrl+N (meaning hold the Ctrl-button and press the N-button). A second window can be useful when moving files between folders.

### 2 - View the filesystem

The main display in *Windows Explorer* shows a list of the files in the current directory. You can navigate through the filesystem using the address bar at the top of the window, or using the folder tree displayed on the left side of the window.

### Connect to a server

The computers in the SSIL labs are configured to provide you with connections to the SSIL file server from the start. The file system is mapped to the R: drive. If you are working on a computer that has not already been connected, you will need to map the drive to the network location.

1. Open *Windows Explorer*. Make sure you are on 'Computer' in the folder tree.
2. Click the button labeled 'Map Network Drive'.
3. Enter the server address: `\\cs-fs2\CAS-Labs\Classes`.

For additional information, see the [SSIL Network Drives and Connecting Remotely page](https://ssil.uoregon.edu/ssil/ssil-network-drives-and-connecting-remotely/)

Note: To connect to the server from off-campus, you will first need to connect to the UO VIrtual Private Network (VPN). Software and instructions for the VPN are available from the UO IT website (https://it.uoregon.edu/vpn).

### 3 - Explore class-related server locations

Once connected to the R: drive, you should see a folder named 'GEOG481'. Within that folder are three folder that organize the course material.

* R:\GEOG481\Class_Data: Will contain copies of lab assignments and any supporting material.
* R:\GEOG481\Shared_Data: Will contain copies of any datasets referenced in a lab that are not publicly available on the internet.
* R:\GEOG481\Student_Data: Will contain a subfolder with your Duck ID (among others). This will be referred to regularly as your 'student folder'.

**IMPORTANT: Be sure to save your work to your student folder on the R: drive.** The SSIL computers will allow you to save files to the local computer's drives; however files on these drives are deleted regularly, and you should not count on them beyond the immediate time on that computer.
