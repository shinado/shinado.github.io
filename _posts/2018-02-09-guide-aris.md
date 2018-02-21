---
layout: post
title:  "Aris Launcher"
date:   2018-02-09 22:01:43 +0530
categories: Aris Guide
---
## What is Aris

To begin with, Aris is an Android Launcher where you do everything by searching, mostly.
  
However, Aris is more than that. In Aris, you can connect various plugins to accomplish complex operations. For instance, if you'd like to share Maya's phone number to Eric, in the normal case, you have to 
  
  * Launch contact book
  * Find Maya
  * Copy
  * Back
  * Find Eric
  * Choose message
  * Paste
  * Send
  
whereas in Aris, just type
  
    maya->eric
    
and hit 'enter' in your keyboard. Please note that you do not need to fully type 'Maya' or 'Eirc', whatever you want appears as the first item in the result area, which means it's the Current Operating Object*, you can either hit 'enter' or use connection operator(->) to connect it with any other items. 
 
## Connection

In Linux, you can share data with pipe. Very much like this idea, you can use connection operator(->) to connect various pipes. 
  
When you type connection operator(->), Aris will take the Primary Result* as input, ready for the next item you are going to connect it with. Via different plugins, you can use your phone like a real hacker. For instance, with APK plugin(available in Store), you can share your app as apk files to your friends in Whatsapp with this:

    facebook->apk->whatsapp
    
        
## Some Basic Plugins
  
  Aris comes with few most basic plugins, which are: restart, clear, help, config, store, uninstall and info.
  
  I may not need to explain what restart does since it is quite obvious. However, I may still need to explain the rest.
  
  clear: To clear the console or, by using {plugin}->clear to clear the pipe configurations if the plugin is able to be cleared. 
  
  config: To configurate Aris.     

  help: To get help obviously. You can also use 

    {plugin}->help
  
  to get help for the certain plugin(if applicantable).
  
## Explained

  **Instruction**：Any input in the input area is considered as an instruction

  **Parameter**：For Instruction
  
    a p
    
  p is a Parameter of a.
  
  **Component**：Refers to any item displayed in the result area.
  
  **Result Set**：All available Components under any Instruction that does not include any operator.
  
  **Primary Result**: The first Component under any Instruction that does not include any operator.
  
  **Plugin**：A Plugin is the executable unit, which contians one or more Components. For instance, the Application Plugin contains all applications in your phone. Any single application is a Component, whereas the Clear Plugin contains only one Component, which is Clear itself. 
  
  **Compatable Plugin**：A Plugin that contains multiple Components
  
  **Action Plugin**: A Plugin that contains only one Component
  
  **Full Plugin**：A Compatable Plugin that requires a certain Component to enable all the other Components it contains. For instance, the Directory Plugin requires user to use Instruction 'cd' to enable directory search. 
  
  **Execute**：Refers to the action when you hit 'enter' or click on one certain Component.  
  
  **Connect**：For any Instruction comes with 
  
    a->b
  
  we call Connect b with a, where the symbol(->) is the connection operator.

   
