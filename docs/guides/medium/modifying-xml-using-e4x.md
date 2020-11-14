---
layout: default
title: Modifying XML using E4X
parent: Medium
grand_parent: Guides
---

# Modifying XML using E4X

OpenAf uses the Java Mozilla Rhino javascript engine and one of the features that, despite being obsolete, has still been kept is E4X.

E4X simply allows for easy interaction and also modification of XML content in Javascript.

Let's start by the XML example used in "Accessing XML using E4X":

````xml
<shopcart>
  <!-- Client id -->
  <client type="personal" id="12345">
    <name>Joe Smith</name>
  </client>

  <!-- Store id -->
  <store>
    <id>12345</id>
    <type>diy</type>
  </store>

  <!-- Items on the shopcart -->
  <items>
    <item id="123">
       <qty>1</qty>
       <name>Item 1</name>
    </item>
    <item id="456">
       <qty>10</qty>
       <name>Item 2</name>
    </item>
  </items>
</shopcart>
````

Then you can load it to a _xml_ javascript variable through various ways:

````javascript
var xml = io.readFileXML("myxml.xml");
var xml = new XMLList(myXMLString);
var xml = <shopcart><!-- Client id --><client type="personal" id="12345">...
````

## Modifying data using the xml variable in javascript

Any element that you can access directly, you can change it:

````javascript
> xml.client.name.toString()
"Joe Smith"
> xml.client.name = "Scott Tiger"
"Scott Tiger"
> xml.client.name.toString()
"Scott Tiger"
````

Changing attributes:

````javascript
> xml.client.@id.toString()
"12345"
> xml.client.@id = "67890"
"67890"
> xml.client.@id.toString()
"67890"
````



And any comments are kept:

````javascript
> xml.toString()
<shopcart>
  <!-- Client id -->
  <client id="12345" type="personal">
    <name>Scott Tiger</name>
  </client>
  <!-- Store id -->
  <store>
    <id>12345</id>
...    
````

### Adding and removing children elements

To add you can simply think like an array:

````javascript
> xml.items.item[2] = <item id="789"><qty>2</qty><name>Item 3</name></item>
> xml.items.item.length()
3
````

And to remove a children element you can use _delete_:

````javascript
> delete xml.items.item[2]
> xml.items.item.length()
2
````

There are more methods, listed on the end of this section, to add or remove elements like _appendChild(child)_, _prependChild(child)_, _insertChildAfter()_, insertChildBefore()_

## XML Object methods

| Method | Description |
|--------|-------------|
| appendChild(_child_) | Adds the child XML object at the end of the corresponding XML element children. |
| prependChild(_child_) | Inserts a child XML object prior to the beginning of the corresponding XML element children. |
| insertChildAfter(_childRef_, _childNew_) | Inserts _childNew_ after _childRef_. |
| insertChildBefore(_childRef_, _childNew_) | Inserts _childNew_ before _childRef_. |
| copy() | Returns a deep copy of a XML object starting on the corresponding XML element children (without the parent). |
| 