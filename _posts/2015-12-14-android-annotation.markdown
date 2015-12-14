---
title:  Pre-process in Android 
date:   2015-12-14 10:00:00
description: Do it right way
categories: Android dev

---


I've been building Jujuj with annotation. I want to make it as effecient as possible therefore I want to replace reflection with pre-process.

I found this ariticle very helpful. However I got a problem. I was trying to add my lib module to the complie module as its dependency but somehow, the code in compile module can not find the class defined in lib module. What an odd. It turned out that this compile module, applying java plugin, can not depend on a module based on Android. Very reasonable and obvious. Then I turned to the source code of ActiveAndroid in Github. The solution is straitforward. Since the AbstractProcessor relies on plugin java, not android, we can simply put android.jar into the libs folder, as a dependency of it. However, doing a reverse way seems not pratical. I tried to apply both java and Android and I got an error.
