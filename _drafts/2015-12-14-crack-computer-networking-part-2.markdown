---
title:  Crack Computer Networking
date:   2015-12-10 10:00:00
description: Start from beginning -- day 2
categories: Basic Computer

---

> On my last post I was talking about IP address. So let us go on with it.

# IP Address
Check your ip address and you'll probably find it goes something like "192.168.x.x". That's your inner private IP address. It's like your room number. And the thing is, your number could be 402 or something while mine could be the same, except that we are in different buildings. You can consider that all computers connected to a router rooms in the same building. Then how do two rooms in the same, or different buildings talk? In order to solve this problem, the router is cricial. Consider router a busy deliver man in building A, who everyone knows his room number, that's say 101. When room 123 wants to talk to room 102, it asks the router, in room 101 to deliver it. The address of deliver man is what we call GATEWAY. You can always find your gateway in your computer is "192.168.1.1" or "192.168.0.1". That's more of an International practice.  

Now what if room 102 in this building wants to talk to room 102 in building B? How to do it?

That's say building A and building B are in the same community. Like how it goes in delivering messages within a building, there's another same guy, let's say he lives in building 0, responsible for delivering messages from buildings to buildings. For people living in building A, they only know this deliver man lives in room 101, that's his address. But for the community, it doesn't care where this deliver man in building A lives, it only cares about which building. Therefore, he has two addresses, room 101, as the address to everyone living in this building, which in the internet world, is known as LAN IP, and, that's say building 12, the address to the community, known as WAN IP.   

This stradegy goes all the way to the whole internet. Now, one important thing is, how to determine wether an address is whitin this group(building or community or whatever) or outside of it? Here it goes subnet mask.

# Subnet
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

Let's say routerA allocates IP address with netmask "255.255.255.0", which means the computer connected to it has IP address let's say "192.168.0.2" while the gate way is "192.168.0.1". Notice here, routerB is considered a normal device, with IP address assigned to, let's say,  "192.168.0.3". So now, what is computerB's gateway supposed to be? "192.168.0.3"? If so, there would be a problem. The IP address of computerB therefore is limited to "192.168.0.x", which is supposed to be the subnet of routerA while in fact it is the subnet of routerB. Think about it, when computerB wants to talk to computerA with its IP "192.168.0.2", routerB would only look up devices within it. In fact, the router forbits any attemptation of setting its LAN IP address in the same subnet as its WAN IP address. Therefore, we set routerB's LAN IP as "192.168.1.1". 

So if computerB wants to talk to computerA, with its LAN IP address, "192.168.0.2", it talks routerB first. RouterB maps this ip with netmask, knowing this ip is not its subnet, then it throws this message to its router, A.  When routerA looks up this address, it knows it's its subnet, then sends it to computerA. 

But if computerA, knowing computerB's IP address, wants to talk to computerB. Will that work? The answer is no. Routers only do two things, either deliver this message to someone in its subnet, or handle it over to its parent router. You can consider LAN IP address a total privacy. It only works for devices inside of it. 

# How Does It Come To You
When you visit google.com, you're actually refering to its public IP. The mechanism is quite simple. Check your internet setting you'll find something like DNS address. It's a server that transforms a readable website address into IP address that internet recognizes. Therefore, when you visit www.google.com, it actually looks up in DNS and return its PUBLIC IP address to you. If you know Google's public IP address, it does not make any differences to directly type in it. 

Website, no matter how complicated it is, is bassically a set of resources in another computer. Therefore, by visiting a website, what you are actually doing is visiting some files in another computer. But how do all those files come back to you? You know the website's public IP address which enables you to have a direct access to, but, all it knows is merly your private IP, it doesn't know where you are?

That's half of the truth. It does not need to know where you really are, cause someone else will do all the work to find you -- Routers. All our communications are via routers. We throw our messages to our direct routers, they throws them to their routers, until they reach the exit of this private world, into the internet. Routers know all your trace on the internet. 
(...to be continued)
