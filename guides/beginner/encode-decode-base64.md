# Encode/Decode base64 in OpenAF

[Base64](https://en.wikipedia.org/wiki/Base64) is a enconding scheme used to represent binary data in ASCII strings (using only 6-bit instead of the full 8-bit). It's used in several cases: LDAP's LDIF files character representation; encoding binary email attachments; embeeding images and fonts in HTML/CSS; avoiding delimiters been interpreted as delimiters inside a sequence of characters on a field: etc&#46;&#46;&#46;

So, how to quickly encode or decode a string or an array of bytes to and from Base 64 in OpenAF:

````javascript
> af.fromBytes2String(af.toBase64Bytes("This is a test"))
"VGhpcyBpcyBhIHRlc3Q="

> af.fromBytes2String(af.fromBase64("VGhpcyBpcyBhIHRlc3Q="))
"This is a test"
````

Keep in mind that the af.toBase64Bytes & af.fromBase64 return always a byte array. So in order to display it you need to use af.fromBytes2String to convert the byte array back to a string.

Of course, to convert a binary content you can just provide the array of bytes:

````javascript
> af.fromBytes2String(af.toBase64Bytes(io.readFileBytes("openaf.ico")))
AAABAAQAgIAAAAEAIAAoCAEARgAAAEBAAAABACAAKEIAAG4IAQAgIAAAAQAgAKgQAACWS...
````