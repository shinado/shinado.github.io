---
layout: post
title:  "Use SLock to lock Aris"
date:   2018-02-09 22:01:43 +0530
categories: Aris Promotion
---

Aris Launcher not only gives you a both efficient and cool way to use you Android, but also gives you freedom to customize it. If you've explored the 'theme' session of Aris Store. You'd probably wonder how you can fully customize your Aris. Good news for you, here's the guide on making your Aris even cooler than it is. 

###Wallpaer/Apperance
This is the most basic and easy ways you can do to customize Aris. In case you haven't found out how to do these settings, follow me on it.

Long press the empty space on the console, you will see two buttons popping up from the bottom. 

![popup](/assets/screenshot_popup.jpg)

Tap on the "wallpaper" button, you can either set a background color for Aris, or select wallpaper and set it as background. 

When you click the "Appearance" button, you'll see this widget displayed on the console.

![popup](/assets/screenshot_appearance.jpg)

When you tap on the first one, text size, you will see an instruction asking you to set a text size. You can do this by entering the number of the text size then hit "enter" key on the keyboard. 

The next two, console font and result font refers to the text in the display area(as we call console), and the results displayed when you search anything, respectively, which follows up text color, where you can set the color for the text on the console. Please also note that if you're using Aris Keyboard, this color will aslo be applied for the keyboard. 

As for the last three, they refer to the results showed up when you search for the items. 

*Tips: If you can not find any empty space, use 'clear' to clear the console. 

###Initiating message
By default, this message will show up when you launch Aris. 

![popup](/assets/screenshot_initext_default.jpg)

You can change this message in the config page, with your personal information, some other cool hacky message, even display current weather or system information if you've got the plugins. To enter config page, you can either find it by typing 'config' or in the sliding folder. 

Now find initiating text and edit. If you want to display a plugin in the initiating text, you can use '${plugin}'. For instance, if you've got the weather plugin, simply put '${weather}' in the initiating text. Once you restart Aris, you'll get something like this:

![popup](/assets/screenshot_initext_weather.jpg)

###Text on Executing
This text will be displyed whenever you execute any item. By default, this text is set to "<font color='#8B76AA'>$s</font>", which represents the output of the item itself. You can also use html tag to format this text. 

For instance, by default, when you launch Google Maps, you'll see this message being displayed. 

![popup](/assets/screenshot_initext_google_map.jpg)

The purple text is the output of this Google Maps app. This message actually is a contaction of its package name and activity name, which allows Aris to launch this app accordingly. 

###Console Output
As shown in the previous screenshot, when you launch Google Maps, you'll see the text in this format:

    [time] console.execute -> [text on executing]

This can be changed in the Console Ouput column in the config. You can use '$t' to display current time. 