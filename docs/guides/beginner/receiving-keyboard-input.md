---
layout: default
title: Receiving keyboard input
parent: Beginner
grand_parent: Guides
---

# Receiving keyboard input

In some scripts you might need to request input from an user or you just want to pause and wait for the user to press any key (the famous "Press any key to continue" sentence). In OpenAF you can do this easily with the Console plugin. Here is a quick example:

````javascript
plugin("Console");

var con = new Console();
var login = con.readLinePrompt("Please enter your login   : ");
var pass  = con.readLinePrompt("Please enter your password: ", "*");

printnl("Press any key to continue... "); 
print("(you pressed char '" + con.readCharB() + "')\n");

print("Login: " + login);
print("Pass : " + pass);
````

So the readLinePrompt function will actually read an entire line, with any "prompt" you want and return you what was written. If you need to hide what the user is writing (e.g. password) you can also provide the character to use for that.

The readCharB will wait for the user to hit any key and then return you the ascii code of the charactered hit on the keyboard. You can cycle between readCharB waiting for a specific char, for example. You can also use readChar that let's you pass, as an argument, the allowed characters set. And if just want to check if any character was hit on the keyboard without waiting for it you can use readCharNB.