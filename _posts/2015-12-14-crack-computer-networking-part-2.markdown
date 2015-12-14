---
title:  Crack Computer Networking
date:   2015-12-10 10:00:00
description: Start from beginning -- day 2
categories: Basic Computer

---

On my last post I was talking about IP address. So let us go on with it.

Check your ip address and you'll probably find it goes something like "192.168.x.x". That's your inner private IP address. It's like your room number. And the thing is, your number could be 402 or something while mine could be the same, except that we are in different buildings. You can consider that all computers connected to a router rooms in the same building. Then how do two rooms in the same, or different buildings talk? In order to solve this problem, the router is cricial. Consider router a busy deliver man in building A, who everyone knows his room number, that's say 101. When room 123 wants to talk to room 102, it asks the router, in room 101 to deliver it. The address of deliver man is what we call GATEWAY. You can always find your gateway in your computer is "192.168.1.1" or "192.168.0.1". That's more of an International practice.  

Now what if room 102 in this building wants to talk to room 102 in building B? How to do it?

That's say building A and building B are in the same community. Like how it goes in delivering messages within a building, there's another same guy, let's say he lives in building 0, responsible for delivering messages from buildings to buildings. For people living in building A, they only know this deliver man lives in room 101, that's his address. But for the community, it doesn't care where this deliver man in building A lives, it only cares about which building. Therefore, he has two addresses, room 101, as the address to everyone living in this building, and, that's say building 12, the address to the community.   

This stradegy goes all the way to the whole internet. Now, one important thing is, how to determine wether an address is whitin this group(building or community or whatever) or outside of it? Here it goes subnet mask.

Check your subnet mask you're most likely to  find it "255.255.255.0". Like the name suggests, it's actually a mask to determine which part of your IP address points to the host and which is your identity under the ROUTE it connects to. How does it do that? That's because IP address is basically a serial of 0/1 digital. For example, address "192.168.1.123" is:
11000000.10101000.00000001.01111011
while "255.255.255.0" is
11111111.11111111.11111111.00000000 
The "1" part masks the host address, which is "192.168.1", while the o part masks the identity "123", which is the identical address of your machine.

In this case, if my computer(192.168.1.123) wants to visit the device with address of "192.168.1.124", then the router knows that this address is whithin this LAN cause the host(192.168.1) is  same as mine, therefore, it just dispatches the message to this "192.168.1.124". 

Now, what if I want to access to "192.168.1.123" under anther route? Well, basically you can't do this. You'll probabely say, bullshit, I can send my message to anyone connected to the internet. That's another we'll talk about later. That's a good arguement. The only reason you can do a online instant chatting is your application connects to a server first, which records your exact address. When you send message to anther person, the server knows his address therefore messages can reach it. How does it know that? Let's slow down a little bit. Before we get to tackle this problem, let's see another example.   

Consider you have a router A, which a computer A and another router B is connected to, and computer B is connected to router B. It goes something like this:

      routerA
       /    \
computerA  routerB
              |
           computerB

Let's say computerA's ip is "192.168.0.12", gateway "192.168.0.1", while computerB' ip is "192.168.1.13". gateway "192.168.1.1". 


Given a PRIVATE IP address, there's still something more need to do with it. As described on the last post, your computer needs to communicate with a router, which is how it assembles a LAN. Notice that the router itself could be under another LAN, which is to say, the router has its router, that's say a parent router, which, contains a lot of children routers. Every child router has its own LAN which many computers connect to. That's how internet is organized, in a tree structure.  

Now things get little bit tricky. We have known that public address is the ONLY DIRECT way to access to internet. In other word, if you want to connect to internet, you have to connect to something that has a PUBLIC address, directly or indrectly. Keep it in mind that public IP address is more like a gate from which you can access to the internet. 

