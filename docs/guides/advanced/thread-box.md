---
layout: default
title: Using OpenAF thread &quot;boxes&quot;
parent: Advanced
grand_parent: Guides
---

# Using OpenAF thread "boxes"

What is an OpenAF thread-box? It's basically being able to run a block of OpenAF code (a function) on a separate Java thread that will be interrupted either due to a timeout or the specific result of a control function.

It's specially useful for controlling the execution of custom code that might run for longer than expected (for example: executing a block of code that should run in seconds taking more than 5 minutes) or until a specific condition happens (for example: executing a block of code while no Ctrl-C is hit on the keyboard by the user).

## Example with timeout

Let's examine an example:

````javascript
> var res = $tb(() => {
    print("Start...");
    sleep(5000, true);
    print("End.");
})
.timeout(2500)
.exec();

Start...
> res
timeout
````

So what happened? The code should print Start wait 5 seconds and then print End. But since the thread-box should timeout after 2.5 seconds it just printed Start and then finished returning the string _timeout_.

If you remove the timeout:

````javascript
> var res = $tb(() => {
    print("Start...");
    sleep(5000, true);
    print("End.");
})
.exec();

Start...
End.
> res
true
````

Now, without a timeout, it prints Start and End and return res.

## Example with stopWhen

If you need to control the execution with a custom function you can use the stopWhen function:

````javascript
> var c = 0;
> var res = $tb(() => {
    for(var ii = 0; ii < 10; ii++) {
        print(c);
        c++;
        sleep(100);
    }
})
.stopWhen(() => {
    return c > 5;
})
.exec();
0
1
2
3
4
5
> res
stop
````

Whenever the function returns true, the execution of the thread-box block of code will be interruped. To increase the interval between calls to the stopWhen function, 25ms, you can add extra time with a _sleep_ call on body of the function.

Of course you can mix _stopWhen_ and _timeout_ if necessary.

**Note**: you can use _threadBoxCtrlC_ function as a stopWhen function to exit whenever a Ctrl-C is hit on the keyboard by a user.