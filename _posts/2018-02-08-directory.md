---
layout: post
title:  "Directory"
date:   2018-02-09 22:01:43 +0530
categories: Aris Guide
---

There are two ways to start directories search. 
1. input cd and hit enter
2. directly input 'cd {directory of file you need}. For instance, if yuo'd like to check directory /downloads in the root, simply use
  cd downloads

Please note that once you're in directory mode, do not use 'cd' again, which is different with Linux.

Once you're in directory search mode, you will be in the root directory of external storage. You won't be able to search any other applications or plugins under this mode, until a file is executed or 'exit' is executed. If the file you execute is an folder, you'll go into that folder and you'll be able to search all the files under that folder. The indicator area will display the current directory. 

You can connect a certain file to another plugin, notablly, another application. After connect operation, you will be able to search all the other plugins including applications. For instance, there's this file

    /download/wallpaper.png

If you want to share this file in WhatsApp, you can do this(with 3 steps)

    cd
    download
    wallpaper->whatsapp

which is equivalent to 

    cd download/wallpaper->whasapp

Please also note that, you do not need to input the full folder or filer. Whenever the result you need appears in the leftmost, you can continue with your next code. In this case, your input might be

    cd do/w->wh

###Back to parent directory

Under directory mode, you can use

    cd

to go back to parent directory. Please note that the plugin that takes you to parent directory is 'cd..'. 

###List all files and folders

Under directory mode, you can use

    ls

to list all files and folders

###Move file

You can move files using connection operator. For instance, use

    cd download/wallpaer->images

to move file /download/wallpaper.png to folder download/images 

###Delete file or folder

You can connect any folders or files to 

    delete

to delete them. For instance, if you'd like to delete file /download/wallpaper.png, use

    download/wallpaper->delete

Moreover, you can use startsWith or endsWith to delete certain files whose names start or end with certains string. For instance, if you'd like to delete all files in /download that end with avi, you can use

    cd download->endswith avi->delete
