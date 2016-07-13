---
title:  Week 1 Monday
date:   2016-06-11 10:24:00
description: 
categories: Blog

---

Been working on using common dependencies with multiple product flavors, failed. Refer to [this](http://stackoverflow.com/questions/28563632/common-code-for-different-android-flavors).

Speed up gradling by replacing 

    compile 'com.google.android.gms:play-services:8.4.0'

with

    compile 'com.google.android.gms:play-services-gcm:8.4.0'

since only GCM is required in my project.

Got a problem:

    Error retrieving parent for item: No resource found that matches the given name after upgrading to AppCompat v23

Change the appcompat dependency to

    compile 'com.android.support:appcompat-v7:22.2.1'

Refer to [this](http://stackoverflow.com/questions/32075498/error-retrieving-parent-for-item-no-resource-found-that-matches-the-given-name)