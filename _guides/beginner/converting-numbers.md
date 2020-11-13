# Converting numbers

Is there a way, in OpenAF, to convert a decimal number to hex? Or to binary? Or to octal? Yes, there is on the ow.format library.

Start by loading the library:
````javascript
> ow.loadFormat();
````

Converting from hexadecimal to decimal:

````javascript
> ow.format.fromHex("1F78")
8056
````

Converting from decimal to hexadecimal:

````javascript
> ow.format.toHex(8056)
"1f78"
````

Converting from decimal to octal:

````javascript
> ow.format.toOctal(8056)
"17570"
````

Converting from octal to decimal:

````javascript
> ow.format.fromOctal(17570)
8056
````

Converting from decimal to binary:

````javascript
> ow.format.toBinary(12345)
"11000000111001"
````

Converting from binary to decimal:

````javascript
> ow.format.fromBinary("11000000111001")
12345
````

And that's it. For conversions between arrays of bytes and the corresponding hexadecimal representation there are also functions like _ow.format.string.toHex_ and _ow.format.string.toHexArray_.