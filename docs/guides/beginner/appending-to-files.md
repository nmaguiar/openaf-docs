# Appending to files

Let's start with a simple question: how to append content to an existing file?

The answer is: check the "help" for the _io.writeFile*_ function you need. Most of them already support an extra parameter to append to existing files.

## io.writeFileString example

To write to a custom log you would do something like:

````javascript
io.writeFileString("mylog.log", new Date() + " | Just did something\n");
````
But using this example the file _mylog.log_ would get overwritten every time you execute it. To get around it simple add an extra flag:

````javascript
io.writeFileString("mylog.log", new Date() + " | Just did something\n", void 0, true);
````

And everytime you run it, it will add a new line to the _mylog.log_ file.

## Appending several files into one

A _one_liner_ that is usually helpfull is:

````javascript
> $from(io.listFilenames("my/path")).ends(".js").select(r => { io.writeFileString("all.js", io.readFileString(r), void 0, true); });
````
This will actually create _all.js_ file with the contents of all files in _my/path_ with suffix _".js"_. Of course you now can change the _$from_ conditions to whatever special conditions you might have.
