---
title:  Week 4 Thursday
date:   2016-07-04 10:24:00
description: 
categories: Blog

---
I'm so ashamed of myself that I wrote code like this and couldn't figure out what went wrong. 

    /**
    * 2016-07 -> 201607
    * 2016-11 -> 201611
    **/
    public int getKey(){
        int year = getCal().get(Calendar.YEAR);
        int month = getCal().get(Calendar.MONTH);
        year *= month >= 10 ? 1 : 10;
        return year + month;
    }
    
    