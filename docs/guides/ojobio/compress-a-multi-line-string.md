---
layout: default
title: Compress a multi-line string
parent: oJobIO
grand_parent: Guides
---

# Compress a multi-line string

When handling a multi-line string it might be usefull to find a simple way to compress it and print it again in OpenAF. This might usually apply to cases where there is no need to change it later (like multi-line ascii banners). Let's see an example on how to accomplish this.

## Step 1

Let's generate a sample banner:

````
$ ojob ojob.io/formats/str2banner str=oJob.io font=georgia11
                              ,,             ,,            
             `7MMF'          *MM             db            
               MM             MM                           
 ,pW"Wq.       MM   ,pW"Wq.   MM,dMMb.     `7MM   ,pW"Wq.  
6W'   `Wb      MM  6W'   `Wb  MM    `Mb      MM  6W'   `Wb 
8M     M8      MM  8M     M8  MM     M8      MM  8M     M8 
YA.   ,A9 (O)  MM  YA.   ,A9  MM.   ,M9 ,,   MM  YA.   ,A9 
 `Ybmd9'   Ymmm9    `Ybmd9'   P^YbmdP'  db .JMML. `Ybmd9'  
                                 
````

## Step 2

Let's generate the code to print this banner:

````
$ ojob ojob.io/formats/str2banner str=oJob.io font=georgia11 | ojob ojob.io/formats/str2code
af.fromBytes2String(io.gunzip(af.fromBase64(af.fromString2Bytes("H4sIAAAAAAAAAKWQMQsCMQyF9/6K4HIqpaNex1scDh/eVm6RUroW9P8v2hYubdGCmCnvfQl5hKhXUnakqJg9A5eB9RGouHffd4ma4UbWJUg+zM48VTnMFiA94NSWqqTiZGJGaxzvFla+a/GRijGnwsi0sNCjYp1iIDlp2t8OmbL1lqmFzi+uqSC7uuB1zLGGEHTKuFnLPbbLkF6sZuCqmLZ//qX+2n0B3DIBrlgCAAA="))))
````

> The generated code captures the multi-line script into a compressed base64 representation that will potentially have a lot less characters than the original string and will only require a single line of code in OpenAF

## Step 3

Let's use it on an OpenAF script (_test.js_):

````javascript
// print banner
print( af.fromBytes2String(io.gunzip(af.fromBase64(af.fromString2Bytes("H4sIAAAAAAAAAKWQMQsCMQyF9/6K4HIqpaNex1scDh/eVm6RUroW9P8v2hYubdGCmCnvfQl5hKhXUnakqJg9A5eB9RGouHffd4ma4UbWJUg+zM48VTnMFiA94NSWqqTiZGJGaxzvFla+a/GRijGnwsi0sNCjYp1iIDlp2t8OmbL1lqmFzi+uqSC7uuB1zLGGEHTKuFnLPbbLkF6sZuCqmLZ//qX+2n0B3DIBrlgCAAA=")))) )
````

Then when you execute this script:

````
$ oaf -f test.js
                              ,,             ,,            
             `7MMF'          *MM             db            
               MM             MM                           
 ,pW"Wq.       MM   ,pW"Wq.   MM,dMMb.     `7MM   ,pW"Wq.  
6W'   `Wb      MM  6W'   `Wb  MM    `Mb      MM  6W'   `Wb 
8M     M8      MM  8M     M8  MM     M8      MM  8M     M8 
YA.   ,A9 (O)  MM  YA.   ,A9  MM.   ,M9 ,,   MM  YA.   ,A9 
 `Ybmd9'   Ymmm9    `Ybmd9'   P^YbmdP'  db .JMML. `Ybmd9'  
                                 

````