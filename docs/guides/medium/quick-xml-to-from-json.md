---
layout: default
title: Quick XML to/from JSON conversion
parent: Medium
grand_parent: Guides
---

# Quick XML to/from JSON conversion

At a first glance XML and JSON have some similiarities but XML is actually document oriented while JSON is data-oriented. Nevertheless for some cases, specially when processing in Javascript, it's useful to convert XML into JSON and JSON into XML. Let's check some basic examples.

## Simple example XML to JSON

Consider the following example:

````xml
<orders>
    <orderId type="normal">1234</orderId>
    <items>
        <item>
            <id>1234</id>
            <qty>1</qty>
        </item>
        <item>
            <id>5678</id>
            <qty>2</qty>
        </item>
    <items>
</orders>
````

To simply convert it to JSON in OpenAF just execute:

````javascript
> af.fromXML2Obj("<orders>\n\t<orderId type=\"normal\">1234</orderId>\n\t<items>\n\t\t<item>\n\t\t\t<id>1234</id>\n\t\t\t<qty>1</qty>\n\t\t</item>\n\t\t<item>\n\t\t\t<id>5678</id>\n\t\t\t<qty
>2</qty>\n\t\t</item>\n\t</items>\n</orders>")
{
  "orders": {
    "orderId": "1234",
    "items": {
      "item": [
        {
          "id": "1234",
          "qty": "1"
        },
        {
          "id": "5678",
          "qty": "2"
        }
      ]
    }
  }
}
````

The result is pretty much similar to the original XML with just one small detail: the orderId's type attribute. It's missing from the final JSON object because JSON doesn't have "an array of attributes per key".

But there is a workaround:

````javascript
> af.fromXML2Obj("<orders>\n\t<orderId type='normal'>1234</orderId>\n\t<items>\n\t\t<item>\n\t\t\t<id>1234</id>\n\t\t\t<qty>1</qty>\n\t\t</item>\n\t\t<item>\n\t\t\t<id>5678</id>\n\t\t\t<qty>2</qty>\n\t\t</item>\n\t</items>\n</orders>", ["orderId"])
{
  "orders": {
    "orderId": {
      "_type": "normal",
      "_": "1234"
    },
    "items": {
      "item": [
        {
          "id": "1234",
          "qty": "1"
        },
        {
          "id": "5678",
          "qty": "2"
        }
      ]
    }
  }
}
````

The last optional argument of af.fromXML2Obj is actually an array of keys meaning that if the XML tag name is found on the XML OpenAF will make it a map with keys prefixed with "\_".

In this case, "\_" is the XML tag associated value (e.g. 1234) and "\_type" is the tag attribute type with its corresponding value (e.g. "normal").

## Simple example JSON to XML

The reverse of the previous example is also possible:

````javascript
> var obj = af.fromXML2Obj("<orders>\n\t<orderId type='normal'>1234</orderId>\n\t<items>\n\t\t<item>\n\t\t\t<id>1234</id>\n\t\t\t<qty>1</qty>\n\t\t</item>\n\t\t<item>\n\t\t\t<id>5678</id>\n\t\t\t<qty>2</qty>\n\t\t</item>\n\t</items>\n</orders>");
> af.fromObj2XML(obj);
<orders><orderId>1234</orderId><items><item><id>1234</id><qty>1</qty></item><item><id>5678</id><qty>2</qty></item></items></orders>
````

**Note: Keep in mind that af.fromXML2Obj and af.fromObj2XML are just "simplifiers" to handle XML/JSON conversion. For full support of XML you should use OpenAF's XML plugin.**

## RSS example

One pratical use for these functions is the hability to easily convert RSS feeds into JSON and JSON into a RSS feed:

````javascript
> mapArray(af.fromXML2Obj($rest().get("http://feeds.reuters.com/reuters/technologyNews")).rss.channel.item, ["title", "pubDate"])
[
  {
    "title": "Apple says Uighurs targeted in iPhone attack but disputes Google findings",
    "pubDate": "Fri, 06 Sep 2019 20:14:45 -0400"
  },
  {
    "title": "U.S. states launch antitrust probes of tech companies, focus on Facebook, Google",
    "pubDate": "Fri, 06 Sep 2019 18:05:56 -0400"
  },
  {
    "title": "Alphabet says received civil investigative demand from U.S. DoJ",
    "pubDate": "Fri, 06 Sep 2019 17:28:58 -0400"
  },
  {
[...]
````