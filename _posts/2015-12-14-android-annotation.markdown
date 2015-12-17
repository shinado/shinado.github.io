---
title:  Pre-process in Android 
date:   2015-12-14 10:00:00
description: Do it right way
categories: Android dev

---

I've started building Jujuj with annotation. I want to make it as effecient as possible therefore I want to replace reflection with pre-process.

However I got a problem. I was trying to add my lib module to the complie module as its dependency but somehow, the code in compile module can not find the class defined in lib module. What an odd. It turned out that this compile module, applying java plugin, can not depend on a module based on Android. Very reasonable and obvious. Then I turned to the source code of ButterKnife in Github. The structure goes something like this:

    lib      ←      app
     ↓                ↓
     
    annotation  ← compiler 
    
Notice that both annotation and compiler apply java while app and lib apply android.