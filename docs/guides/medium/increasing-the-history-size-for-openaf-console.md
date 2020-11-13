---
layout: default
title: "Medium: Increasing the history size for openaf-console"
parent: Guides
grand_parent: OpenAF docs
---

# Increasing the history size for openaf-console

The default history size on the openaf-console is around 500 lines or commands. But there are some users that require a little more for their uses. So can an user increase the history size for openaf-console? Yes, you just set it on the openaf-console_profile file.

To check the current size just open an openaf-console and execute: 

````javascript
> con.getConsoleReader().getHistory().getMaxSize()
500
````

To change this you just need to execute: 

````javascript
con.getConsoleReader().getHistory().setMaxSize(1000);
````

But it order to make this change permanent you need to execute this setMaxSize every time openaf-console starts. An easy way is to use the openaf-console_profile file. This file, in Unix/Mac, is located at ~/.openaf-console_profile and in Windows its located at c:\users\[you user]\.openaf-console_profile. It executes like an openaf script every time the openaf-console is started.

That means that you have to be careful on what you add to this file as you also have to be careful in increase the history size. The default is set to keep the performance at "satisfactory" levels so do lower your maximum if you notice an non satisfactory performance downgrade. 

The same applies to the near by .openaf_profile file. It will get executed every time a openaf script is executed (and keep in mind that the openaf-console is just another openaf script).