---
layout: default
title: Encrypt/Decrypt with public/private keys
parent: Beginner
grand_parent: Guides
---

# Encrypt/Decrypt with public/private keys

There are built-in functions to easily encrypt/decrypt text using a single password key (using functions _af.encrypt_ and _af.decrypt_). But if you need better security you might need to encrypt/decrypt using a public and a private keys.

This can be achieved using the __ow.java.cipher__. It enables the generation or loading of existing public and private keys and use them to encrypt/decrypt text.

To create an object instance:

````javascript
ow.loadJava();
var cipher = new ow.java.cipher();
````

## Generating public/private keys

You can generate a public and a private key with a specific key length (by default 2048 bits). You can generate for 3072, 4096, 7680 and 15360 bits (the bigger, the longer to generate):

````javascript
var keys = cipher.genKeyPair(4096);
````

To save the private and public keys in files:

````javascript
cipher.saveKey2File("key.pub", keys.publicKey, false);
cipher.saveKey2File("key.priv", keys.privateKey, true);
````

To load the keys from the files:

````javascript
var kpPUB  = cipher.readKey4File("key.pub", false);
var kpPRIV = cipher.readKey4File("key.priv", true);
````

## Encrypting/Decrypting text

Now that you have a pair of public and private keys you can easily encrypt/decrypt text:

````javascript
var cipheredText = cipher.encrypt2Text(plainText, kpPUB);
````

````javascript
var plainText = cipher.decrypt4Text(cipheredText, kpPRIV);
````

The functions with the "Text" suffix automatically convert to a Base64 text for easier transport. But there are also functions for encrypting/decrypting to/from arrays of bytes and streams.