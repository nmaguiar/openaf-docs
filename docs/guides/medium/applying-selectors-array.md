---
layout: default
title: Applying selectors to an array
parent: Medium
grand_parent: Guides
---

# Applying selectors to an array

Whenever using an array of maps, and specially when analyzing them on OpenAF-console, you probably want to focus just on some map entries and not have all the other map keys on the screen. To make it easier there is a function _mapArray_ in OpenAF for this case and others.

Let's say you have an array of maps and submaps like this:

````javascript
> $rest().get("https://jsonplaceholder.typicode.com/users");
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Gwenborough",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
      "name": "Romaguera-Crona",
      "catchPhrase": "Multi-layered client-server neural-net",
      "bs": "harness real-time e-markets"
    }
  },
  {
    "id": 2,
    "name": "Ervin Howell",
    "username": "Antonette",
    "email": "Shanna@melissa.tv",
    "address": {
[...]
````

Let's say that you want to compare just the name, the city on the address and the company name. With _mapArray_ that's easy:

````javascript
> mapArray( $rest().get("https://jsonplaceholder.typicode.com/users"), [ "name", "address.city", "company.name" ] )
[
  {
    "name": "Leanne Graham",
    "address.city": "Gwenborough",
    "company.name": "Romaguera-Crona"
  },
  {
    "name": "Ervin Howell",
    "address.city": "Wisokyburgh",
    "company.name": "Deckow-Crist"
  },
  {
    "name": "Clementine Bauch",
    "address.city": "McKenziehaven",
[...]
````

Since now you just have the fields you want you can also use _table_ on openaf-console:

````javascript
> table mapArray( $rest().get("https://jsonplaceholder.typicode.com/users"), [ "name", "address.city", "company.name" ] )
          name          | address.city |   company.name
------------------------+--------------+------------------
Leanne Graham           |Gwenborough   |Romaguera-Crona
Ervin Howell            |Wisokyburgh   |Deckow-Crist
Clementine Bauch        |McKenziehaven |Romaguera-Jacobson
Patricia Lebsack        |South Elvis   |Robel-Corkery
[...]
````

If you have an array on a map element you can just reference it directly:

````javascript
> mapArray( someMap, ["id", "items[0].subId"])
[
  {
    "id": 1,
    "items[0].subId": 1
  },
  {
    "id": 2,
    "items[0].subId": 4
  },
  {
    "id": 3,
    "items[0].subId": 43
  }
]
````

_Note: mapArray uses ow.obj.getPath and ow.obj.setPath internally that you can use in other situations directly._