---
title:  Introduce of Jujuj
date:   2016-03-22 10:24:00
description: Release version comming some
categories: Android

---

<img src="https://cloud.githubusercontent.com/assets/3215337/13972466/f7fdb030-f0d3-11e5-9149-fe37ffc5ea44.png" width = "300"/>

Image you're developing this application, two problems will come into your mind instantly(if not, just read on): 

1. I need to pre-load and display what's cached in the database, before retrieving data from the server and, whatever is loaded from server should be stored in the database. 

2. These posts should only include the identity of the user whom they belong to. Users' information(portrait, name, etc.) is supposed to be managed in a pool, so that whoever wants it can lazy-load it according to the identity, like ImageLoader

This is the very common scenery when developing applications that retrieve data from servers.

That's why `Jujuj` is built, to make these things easier. With `Jujuj`, you do not need to worry about how data is managed, just use it like this:
```
Jujuj.getInstance().inject(this, new LoginRequest(this));
```

`Jujuj` frees you from all the `findViewById`, `setText`, `setAdapter` whatsover by simply declaring which variable is supposed to be bind on which widget, like this:
```
@ViewInj   
public String account;
```

When you have a foreign key, for instance, user's identity in the post object, just put it this way:
```
@DependentInj   
public User user;
```

and `Jujuj` will do all the magic. 

Wanna [try it](http://github.com/shinado/jujuj) yourself? 