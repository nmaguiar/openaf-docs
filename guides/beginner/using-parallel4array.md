# Using the function parallel4Array

OpenAF allows you to code in javascript while using Java functionality underneath. But there are obvious differences between the two languages.

## Example

Let's take a simple example for parallel processing. First you create an array with the information of several files:

````javascript
var files = listFilesRecursive("/usr");
````

### Running it sequentially 

Next you want to capture the result of executing a "not so fast" operation of performing an external shell command and capture the result:

````javascript
var res = [];
for(var i = 0; i < files.length; i++) {
    res.push(sh("ls " + files[i]));
}
````

Using this simple for cycle the time elapsed, on a specific environment, was __1 second and 686 ms__.

### Running it in parallel

But this was a rather sequential processing in nature. OpenAF includes a function, _parallel4Array_, that wlil automate much of the work of using Java threads to perform the same exact functionality:

````javascript
var res = parallel4Array(files, (v) => {
    return sh("ls " + v.filename);
})
````

Changing the _for_ cycle by _parallel4Array_, and testing on the same environment, the result was a exactly equal _res_ array in around __842ms__. So what happenend?

Breaking it down:

* The number of cpu cores was detected.
* The _files_ array was split evenly between the number of cpu cores detected.
* Each "splitted array" was executed sequentially on separate executing thread (Java thread).
* OpenAF kept an eye on the operating system reported machine load introducing delays when cpu cores got "overloaded".

This last step is helpful when executing on machines with a large number of cpu cores.

## "Can I tune it?"

Yes, of course. A third optional argument of _parallel4Array_ let's you override the cpu detection and "machine load" control. A fourth argument of _parallel4Array_ gives you direct access to the Java threads objects, unique ids, etc... Check the help information in openaf-console: "help parallel4Array".

For advanced cases you can use the function _parallelArray_ which let's you control how the end result will be built letting you provide a function to "unify" all the threads results.

There is even the function _parallel_ that will launch multiple threads to execute the same provided function without the need to provide an array.