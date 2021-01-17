---
layout: default
title: console
parent: Reference
grand_parent: OpenAF docs
---


## console

### Console.console

__Console.console()__

````
Creates a new instance of the object Console.
````
### Console.console

__Console.console()__

````
Creates a new instance of the object Console.
````
### Console.getConsoleReader

__Console.getConsoleReader() : ConsoleReader__

````
Returns the internal ConsoleReader java object.
````
### Console.getConsoleReader

__Console.getConsoleReader() : ConsoleReader__

````
Returns the internal ConsoleReader java object.
````
### Console.isAnsiSupported

__Console.isAnsiSupported() : boolean__

````
Determines if the console is able to support ansi (returns true) or not (returns false).
````
### Console.isAnsiSupported

__Console.isAnsiSupported() : boolean__

````
Determines if the console is able to support ansi (returns true) or not (returns false).
````
### Console.readChar

__Console.readChar(allowed) : char__

````
Read a character from the console. If allowed is provided only the characters on the string allowed will be considered.
````
### Console.readChar

__Console.readChar(allowed) : char__

````
Read a character from the console. If allowed is provided only the characters on the string allowed will be considered.
````
### Console.readCharB

__Console.readCharB() : int__

````
Low level character read from console with waiting. Will return -1 - EOF or -2 - No character available or the available character
````
### Console.readCharB

__Console.readCharB() : int__

````
Low level character read from console with waiting. Will return -1 - EOF or -2 - No character available or the available character
````
### Console.readCharNB

__Console.readCharNB() : number__

````
Low level character read from the console with no waiting. Will return -1 for EOF or -2 for No character available or the available character
````
### Console.readCharNB

__Console.readCharNB() : number__

````
Low level character read from the console with no waiting. Will return -1 for EOF or -2 for No character available or the available character
````
### Console.readLine

__Console.readLine(aMaskchar) : String__

````
Read a line from the console. Will provide a mask for introduction of passwords if aMaskchar is provided. Returns the line read. NOTE: Use Console.readLinePrompt if you are using a prompt.
````
### Console.readLine

__Console.readLine(aMaskchar) : String__

````
Read a line from the console. Will provide a mask for introduction of passwords if aMaskchar is provided. Returns the line read. NOTE: Use Console.readLinePrompt if you are using a prompt.
````
### Console.readLinePrompt

__Console.readLinePrompt(aPrompt, aMaskchar) : String__

````
Read a line from the console providing aPrompt. Will provide a mask for introduction of passwords if aMaskchar is provided. Returns the line read. NOTE: Use this method instead of Console.readLine if you are using a prompt
````
### Console.readLinePrompt

__Console.readLinePrompt(aPrompt, aMaskchar) : String__

````
Read a line from the console providing aPrompt. Will provide a mask for introduction of passwords if aMaskchar is provided. Returns the line read. NOTE: Use this method instead of Console.readLine if you are using a prompt
````
