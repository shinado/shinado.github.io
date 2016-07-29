---
title:  Week 1 Friday
date:   2016-06-15 10:24:00
description: 
categories: Blog

---
Got a problem using Gson: 
   
    Cannot make field constructor accessible
    
Solved by adding this:

    new GsonBuilder()
            .excludeFieldsWithModifiers(Modifier.FINAL, Modifier.TRANSIENT, Modifier.STATIC)
            
Refer to [this](https://github.com/google/gson/issues/648)

Got another weird bug, 