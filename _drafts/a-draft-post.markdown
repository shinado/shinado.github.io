---
title:  Crack Computer Networking
date:   2015-12-17 10:00:00
description: Start from beginning -- day 3
categories: Basic Computer

---

On my last post I metioned the functionality of routers. Now I'm gonna further talk about it. 

# Routing
Router does not just simply deliver messages, it does something more. It maintains a table called routing table which tracks down every intention of the computers connected to it. This table is what makes it possible for all the resources on the internet going back to you. 

Image that you're typing Google's page in browser, when you hit enter, the browser will look up Google's public IP address in DNS, then it sends this IP address to the router. The router got it, marking it as the destination. Where is it supposed to be found? It forwarded to its parent, and its parent forward to its grandparent....until it reaches Google. So basically routers know where to go. Image you are driving in national highway, from, let's say Shanghai, and your destination is Beijing. You need to know your next stop before you finally reach Beijing. What is the best route to Beijing? What about somewhere else, like Hangzhou? 

That is what routers do. They tell you which way is the best to go, taking things like congestion into consideration. There's always more than one way to reach your destination, going all the way west to Tibet, then turning north east to Beijing will do, yet, with more time. When the router receive the message from your computer, it checks the destination of this message, and forward this message to the next hop, which he believes is the best way to go. How to determine which is the best way? Ask [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm).


