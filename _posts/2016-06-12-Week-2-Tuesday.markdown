---
title:  Week 1 Tuesday
date:   2016-06-12 10:24:00
description: 
categories: Blog

---
The differences between compileSDKVersion and targetSDKVersion check [this](http://stackoverflow.com/questions/26694108/what-is-the-difference-between-compilesdkversion-and-targetsdkversion)

In the Android permission system, the official doc says like [this](https://developer.android.com/training/permissions/requesting.html):

> If the device is running Android 5.1 or lower, or your app's target SDK is 22 or lower: If you list a dangerous permission in your manifest, the user has to grant the permission when they install the app; if they do not grant the permission, the system does not install the app at all.
> 
> If the device is running Android 6.0 or higher, and your app's target SDK is 23 or higher: The app has to list the permissions in the manifest, and it must request each dangerous permission it needs while the app is running. The user can grant or deny each permission, and the app can continue to run with limited capabilities even if the user denies a permission request.

How to handle Android touch events has always been a big problem for me. I believe [this site](https://developer.android.com/training/gestures/viewgroup.html) has made it really clear.

The very point of this is that make sure to return true in the child touch event so it means that "I am interested in this event so next time dispatch this to me ok?". On the contrary, when it returns false in the touch event, which means "OK you know what, I'm not interested in the events so DO NOT dispatch those to me any more". Nailed it. 

