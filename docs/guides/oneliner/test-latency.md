---
layout: default
title: "OneLiner: Test latency"
parent: Guides
grand_parent: OpenAF docs
---

# Test latency

The usual latency test most of us use if simply execute the _ping_ operating system command from the source to the target we want to measure. But nowadays, [ICMP](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol) packets (what ping really transmits) might be blocked by a firewall or similar.

With OpenAF's function _ow.format.testLatency_ that isn't a problem since it will try to open a TCP socket to the desired host and port and measure the time taken for the socket connection to be created (and then it closes it). 

It's not perfect but is usually enough to understand the relative latency to another host and port.

First I will present a test function a later show how to use it as an one-liner.

## The test function

Here is a test function that will taken several measures and return you: each measure, the average and a chart representation of the variation between each measure.

````javascript
ow.loadFormat();

var tl = (host, port, times) => { 
    times = _$(times).isNumber().default(3); 
    var tries = [], sum = 0, max = 0; 
    
    for(var ii = 0; ii < times; ii++) {
        tries.push({
            sample: ii+1, 
            latency: ow.format.testPortLatency(host, port)
        });
    }; 
    tries.forEach((v) => {
        sum += v.latency; 
        max = (v.latency > max) ? v.latency : max; 
        v.chart = ow.format.string.progress(v.latency, max, 0, 50, "=", " ");
    }); 
    tries.push({ 
        sample: "avg", 
        latency: Math.floor(sum/times) + "ms"
    });

    return tries;
}
````

## The one-liner

Now convert it to a one-liner and write on an openaf-console, for example:

````javascript
> ow.loadFormat();
> var tl = (host, port, times) => { times = _$(times).isNumber().default(3);var tries = [], sum = 0, max = 0; for(var ii = 0; ii < times; ii++) { tries.push({ sample: ii+1, latency: ow.format.testPortLatency(host, port)});}; tries.forEach((v) => { sum += v.latency; max = (v.latency > max) ? v.latency : max; v.chart = ow.format.string.progress(v.latency, max, 0, 50, "=", " "); }); tries.push({ sample: "avg", latency: Math.floor(sum/times) + "ms" }); return tries; }
````

And test it:

````javascript
> table tl("www.yahoo.com", 443);
sample|latency|                      chart                       
------+-------+--------------------------------------------------
1     |63     |==================================================
2     |60     |================================================  
3     |63     |==================================================
avg   |62ms   
````

Of course, the chart would only help you when there are slight or significant variations in latency between tests:

````javascript
> table tl("dynamodb.ap-southeast-2.amazonaws.com", 443, 15);
sample|latency|                      chart                       
------+-------+--------------------------------------------------
1     |354    |==================================================
2     |364    |==================================================
3     |357    |================================================= 
4     |351    |================================================  
5     |352    |================================================  
6     |357    |================================================= 
7     |406    |==================================================
8     |358    |============================================      
9     |354    |============================================      
10    |348    |===========================================       
11    |361    |============================================      
12    |358    |============================================      
13    |369    |=============================================     
14    |354    |============================================      
15    |366    |=============================================     
avg   |360ms  
````

## From the command-line

If you want to run it from the command-line:

````bash
$ openaf -c 'ow.loadFormat();var tl = (host, port, times) => { times = _$(times).isNumber().default(3);var tries = [], sum = 0, max = 0; for(var ii = 0; ii < times; ii++) { tries.push({ sample: ii+1, latency: ow.format.testPortLatency(host, port)});}; tries.forEach((v) => { sum += v.latency; max = (v.latency > max) ? v.latency : max; v.chart = ow.format.string.progress(v.latency, max, 0, 50, "=", " "); }); tries.push({ sample: "avg", latency: Math.floor(sum/times) + "ms" }); return tries; }; print(printTable(tl(  "www.google.com", 443, 15)));'
sample|latency|                      chart                       
------+-------+--------------------------------------------------
1     |35     |==================================================
2     |30     |===========================================       
3     |30     |===========================================       
4     |26     |=====================================             
5     |30     |===========================================       
6     |29     |=========================================         
7     |29     |=========================================         
8     |28     |========================================          
9     |28     |========================================          
10    |29     |=========================================         
11    |33     |===============================================   
12    |30     |===========================================       
13    |32     |==============================================    
14    |33     |===============================================   
15    |33     |===============================================   
avg   |30ms   
````

And replace the function arguments on the end of the one-liner.