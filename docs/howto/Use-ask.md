---
layout: default
title: How To - Use ask functions
parent: How To
grand_parent: OpenAF docs
---
# How to - Use ask functions

_applies to version >= 20201111_

When running OpenAF scripts it's possible to "ask" for user input. This can be achieve using one of four functions:

| Function | Description |
|----------|-------------|
| ask | Asks for an entire input line optionally masking with a char (e.g. masking with '*' all characters). |
| ask1 | Asks for just a single key of input from a list of possible key values. | 
| askEncrypt | Asks for user input to produce an encrypted string. |
| askN | Asks for multi-line input providing a function to decide each lien prompt and a stop function to decide when the input is finished. |  

## Using 'ask'

Asking a question to the user:

````javascript
> var result = ask("What's your name? ");
What's your name? Scott Tiger
> print(result)
Scott Tiger
````

Asking for a question with a secret answer:

````javascript
> var result = ask("What's your password? ", "*");
What's your password? **********
> print(result)
MyPassword
````

## Using 'ask1'

Asking for a confirmation from the user:

````javascript
> var result = ask1("Do you want to continue (y/n)?", "ynYN"); print(result);
Do you want to continue? (y/n)> n
> result = String(result).toLowerCase();
> if (result.toLowerCase() == "n") { 
|    print("stopping....)    
| }
````

## Using 'askEncrypt'

This is the same as the function 'ask' but avoiding to echo any input and returning the encrypted format.

````javascript
> var result = askEncrypt("Password: ");
Password:
> print(result);
74D685B4A77E691819C3194BC55B0AA240EF2C918D386027EE1CB645D67AF9B8
````

## Using 'askN'

Asking for a multi-line input:

````javascript
> var result = askN(() => "| ", v => v.endsWith("\n\n"));
| first line
| second line
|
> print(result)
first line
second line


>
````