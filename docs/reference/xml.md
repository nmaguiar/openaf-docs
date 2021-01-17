---
layout: default
title: xml
parent: Reference
grand_parent: OpenAF docs
---


## xml

### XML.doc

__XML.doc() : Document__

````
Returns the org.w3c.dom.Document object with the internal representation.
````
### XML.doc

__XML.doc() : Document__

````
Returns the org.w3c.dom.Document object with the internal representation.
````
### XML.find

__XML.find(aXPathQuery) : Node__

````
Returns an org.w3c.dom.Node object from the XPathQuery provided.
````
### XML.find

__XML.find(aXPathQuery) : Node__

````
Returns an org.w3c.dom.Node object from the XPathQuery provided.
````
### XML.findAll

__XML.findAll(aXPathQuery) : NodeList__

````
Returns a org.w3c.dom.NodeList object given the XPathQuery provided.
````
### XML.findAll

__XML.findAll(aXPathQuery) : NodeList__

````
Returns a org.w3c.dom.NodeList object given the XPathQuery provided.
````
### XML.from

__XML.from(aXPathQuery) : Object__

````
Returns an XMLBuilder2 object from the XPathQuery provided.
````
### XML.from

__XML.from(aXPathQuery) : Object__

````
Returns an XMLBuilder2 object from the XPathQuery provided.
````
### XML.get

__XML.get(aXPathQuery) : String__

````
Returns the string value for the given XPathQuery provided.
````
### XML.get

__XML.get(aXPathQuery) : String__

````
Returns the string value for the given XPathQuery provided.
````
### XML.toNativeXML

__XML.toNativeXML() : Object__

````
Returns an E4X representation.
````
### XML.toNativeXML

__XML.toNativeXML() : Object__

````
Returns an E4X representation.
````
### XML.w

__XML.w() : String__

````
Returns the internal representation into a XML string.
````
### XML.w

__XML.w() : String__

````
Returns the internal representation into a XML string.
````
### XML.x

__XML.x(aRoot) : Object__

````
Starts a XMLBuilder2 object given a root element string. This code:

plugin("XML");
plugin("Beautifiers");
var xml = new XML();
xml.x("test")
 .e("test1").a("status", "ok").a("language", "javascript")
  .e("path").a("type", "sharepath")
   .t("\\\\machine\\share\\test1")
  .up()
 .up()
 .e("test2").a("status", "ongoing").a("language", "python")
  .e("path").a("type", "URL")
   .t("http://some.url/test2");
\  print(beautify.xml(xml.w()));
\  var nodes = xml.findAll("/test/*");
for(var i = 0; i < nodes.getLength(); i++) {
  var name = nodes.item(i).getNodeName();
   var status = nodes.item(i).getAttributes().getNamedItem("status").getNodeValue();
   //var value = notes.item(i).getTextContent();
   print("name = " + name + 
	  "; status = " + status + "; " + 
	  "; " + xml.get("//" + name + "/path/@type") + 
       " = " + xml.get("//" + name + "/path"));
}

will generate the following output:

<test>
   <test1 language="javascript" status="ok">
       <path type="sharepath">\\machine\share\test1</path>
   </test1>
   <test2 language="python" status="ongoing">
      <path type="URL">http://some.url/test2</path>
   </test2>
</test>
name = test1; status = ok; ; sharepath = \\machine\share\test1
name = test2; status = ongoing; ; URL = http://some.url/test2

````
### XML.x

__XML.x(aRoot) : Object__

````
Starts a XMLBuilder2 object given a root element string. This code:

plugin("XML");
plugin("Beautifiers");
var xml = new XML();
xml.x("test")
 .e("test1").a("status", "ok").a("language", "javascript")
  .e("path").a("type", "sharepath")
   .t("\\\\machine\\share\\test1")
  .up()
 .up()
 .e("test2").a("status", "ongoing").a("language", "python")
  .e("path").a("type", "URL")
   .t("http://some.url/test2");
\  print(beautify.xml(xml.w()));
\  var nodes = xml.findAll("/test/*");
for(var i = 0; i < nodes.getLength(); i++) {
  var name = nodes.item(i).getNodeName();
   var status = nodes.item(i).getAttributes().getNamedItem("status").getNodeValue();
   //var value = notes.item(i).getTextContent();
   print("name = " + name + 
	  "; status = " + status + "; " + 
	  "; " + xml.get("//" + name + "/path/@type") + 
       " = " + xml.get("//" + name + "/path"));
}

will generate the following output:

<test>
   <test1 language="javascript" status="ok">
       <path type="sharepath">\\machine\share\test1</path>
   </test1>
   <test2 language="python" status="ongoing">
      <path type="URL">http://some.url/test2</path>
   </test2>
</test>
name = test1; status = ok; ; sharepath = \\machine\share\test1
name = test2; status = ongoing; ; URL = http://some.url/test2

````
### XML.XML

__XML.XML(aXML) : XML__

````
Creates a XML object instance. You can provide a string representation of an XML to instantiate the internal representation. NOTE: This plugin uses a DOM parser (all XML will be read into memory).
````
### XML.XML

__XML.XML(aXML) : XML__

````
Creates a XML object instance. You can provide a string representation of an XML to instantiate the internal representation. NOTE: This plugin uses a DOM parser (all XML will be read into memory).
````
