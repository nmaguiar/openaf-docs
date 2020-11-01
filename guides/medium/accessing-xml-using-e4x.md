# Accessing XML using E4X

OpenAf uses the Java Mozilla Rhino javascript engine and one of the features that, despite being obsolete, has still been kept is E4X.

E4X simply allows for easy interaction of XML content in Javascript.

Let's start by the following XML example:

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

## Loading XML to OpenAF

You can load this xml from a file:

````javascript
var xml = io.readFileXML("myxml.xml");
````

From a string:

````javascript
var xml = new XMLList(myXMLString);
````

Or directly:

````javascript
var xml = <shopcart><!-- Client id --><client type="personal" id="12345">...
````

All of them will result in a _xml_ javascript variable of type "_xml_".

## Accessing data using the xml variable in javascript

To access any element simply think like you would access it if it was a JSON map:

````javascript
> xml.client.name.toString()
"Joe Smith"
> xml.store.id.toString()
"12345"
````

Each element has several methods from which we are using the _toString_ method. There is a list of methods on the end of this section. 

For attributes it's the same but add the prefix _"@"_:

````javascript
> xml.client.@type.toString()
"personal"
````

For multiple items you can think of it now as an array:

````javascript
> xml.items.item[0].@id.toString()
123
> xml.items.item[1].qty.toString()
10
````

But this, is also valid (think of it as the first "store" tag element):

````javascript
> xml.store[0].id.toString()
"12345"
````

### Accessing all children nodes

````javascript
> xml.children()[1].name.toString()
"Joe Smith"
````

Why is the children element on position 1 and not in 0? Because comments are also nodes:

````javascript
> xml.children()[0].toString()
"<!-- Client id -->"
````

### Using for cycles

Don't forget that you are in javascript, so you can do _for_ cycles:

````javascript
var totalQty = 0;
for(var i in xml.items.item) {
    totalQty += Number(xml.items.item[i].qty);
}
// 11
````

You can also search all descendants in a _for_ cycle:

````javascript
for(var i in xml..name) {
    print(xml..name[i].toString());
}
// Joe Smith
// Item 1
// Item 2
````

### Using namespaces

You can also use namespaces:

````javascript
var xml = <links><a xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="http://www.google.com">Test link</a></links>;

var ns = new Namespace("http://www.w3.org/1999/xlink");
var url = xml..a;
var link = url.@ns::href;
// http://www.google.com
````

## XML Object methods

| Method | Description |
|--------|-------------|
| attribute(_attributeName_) | Returns the attribute _attributeName_ from the corresponding XML element node. |
| attributes() | Returns a list of the attributes associated with the corresponding XML element node. |
| child(_propertyName_) | Returns the children elements named _propertyName_ associated with the corresponding XML element node. |
| children() | Returns all children elements associated with the corresponding XML element node. |
| descendants(_name_) | Equivalent to "xml.._name_". |
| elements(_name_) | Equivalent to _children()_ if no _name_ is provided or equivalent to _child_ if a _name_ is provided. |
| parent() | Returns the parent element associated with the corresponding XML element node. |
| comments() | Returns the children elements of type 'comment' associated with the corresponding XML element node. |
| text() | Returns the text component of the corresponding XML element node. |
| name() | Returns a map with the name and local name associated with the corresponding XML element node. |
| localName() | Returns the local name associated with the corresponding XML element node. |
| namespace(_prefix_) | Returns the namespace for the provided _prefix_ of the namespace associated with the corresponding XML element node. |
| namespaceDeclarations() | Returns an array of namespaces associated with the corresponding XML element node. |
| childIndex() | Returns the index number on the childrens list of the corresponding XML element node. |
| length() | Returns the size of the children elements of the corresponding XML element node. |
| nodeKind() | Returns if the corresponding XML element node is a _element_ of a _comment_. |
| toString() | Returns the string of the current XML element node. |
| toXMLString() | Returns the XML encoded string of the current XML element node. |