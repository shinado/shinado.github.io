---
title:  Week 1 Wednesday
date:   2016-06-13 10:24:00
description: 
categories: Blog

---
Got a werid problem on Android Studio 2.1.2. When I tried to run my application, it throws string out of boundary exception and aborts builidng. Turned out it takes none-translating strings in strings.xml as an error when I use release variant. 

You can either switch to debug variant or put this code in build.gradle:

    lintOptions {
        checkReleaseBuilds false
        abortOnError false
    }

I've been using debug variant ever since but I got a problem as I switched to Android 2.1.4. The problem and the very solution, which turns me into using release variant is [here](http://nanashi07.blogspot.my/2016/04/problem-on-result-of-dexfileentries.html). For more infomation about instant run, check this official post [here](https://developer.android.com/studio/run/index.html#instant-run)

