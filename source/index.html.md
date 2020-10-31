---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - python
  - javascript
  - go

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the poe.watch API! You can use my API to access poe.watch API endpoints.

I have language bindings for Python and Go! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Get

The get endpoint always needs a valid category. More about valid categories in the category section.

## Get all armours

```go
import poe "github.com/mxrk/poewatch"

items := poe.GetItems("Heist", "armour")
fmt.Println(items)
```

> The above command returns JSON structured like this:

```json
[
   {
      "id":6,
      "name":"Wreath of Phrecia",
      "category":"armour",
      "group":"helmets",
      "frame":3,
      "influences":null,
      "linkCount":0,
      "icon":"https://web.poecdn.com/image/Art/2DItems/Armours/Helmets/Wreath_of_Phrecia.png?v=0557bfae422aebfaa3ac32bee72fe98e\u0026w=2\u0026h=2\u0026scale=1",
      "mean":13.2,
      "mode":0,
      "min":1.6,
      "max":13.2,
      "exalted":0.16,
      "total":0,
      "daily":169,
      "current":0,
      "accepted":0,
      "change":214,
      "history":[
         2.78,
         1.95,
         3.75,
         3.5,
         4.85,
         4.42,
         8.2
      ],
      "lowConfidence":false,
      "perfectPrice":10.28,
      "perfectAmount":0,
      "implicits":null,
      "explicits":[
         "Has no Attribute Requirements",
         "Increases and Reductions to Light Radius also apply to Area of Effect at 50% of their value",
         "Increases and Reductions to Light Radius also apply to Damage",
         "(15-25)% increased Light Radius",
         "Deal no Chaos Damage"
      ]
   }
]
```


### HTTP Request

`GET https://api.poe.watch/get?category=armour&league=Heist`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
category | string | set to the wanted category
league | string | set the wanted league

<aside class="success">
Remember — on this endpoint only current leagues are working. For older ones use the history endpoint.
</aside>

## Get all weapons

```go
import poe "github.com/mxrk/poewatch"

items := poe.GetItems("Heist", "weapons")
fmt.Println(items)
```

> The above command returns JSON structured like this:

```json
[
   {
      "id":3,
      "name":"Uul-Netol's Kiss",
      "category":"weapons",
      "group":"twohandaxes",
      "frame":3,
      "influences":null,
      "linkCount":0,
      "icon":"https://web.poecdn.com/image/Art/2DItems/Weapons/TwoHandWeapons/TwoHandAxes/UulNetolsKiss.png?v=6f20a967d688173e5ec5d56008332bdb\u0026w=2\u0026h=4\u0026scale=1",
      "mean":2.18,
      "mode":0,
      "min":1.82,
      "max":2.77,
      "exalted":0.03,
      "total":0,
      "daily":367,
      "current":0,
      "accepted":0,
      "change":-41,
      "history":[
         3.11,
         4.83,
         4.35,
         3.01,
         4.08,
         3.38,
         3.21
      ],
      "lowConfidence":false,
      "perfectPrice":0,
      "perfectAmount":0,
      "implicits":null,
      "explicits":[
         "(140-170)% increased Physical Damage",
         "15% reduced Attack Speed",
         "25% chance to Curse Enemies with Level 10 Vulnerability on Hit",
         "Attacks have 25% chance to inflict Bleeding when Hitting Cursed Enemies"
      ]
   }
]
```


### HTTP Request

`GET https://api.poe.watch/get?category=weapon&league=Heist`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
category | string | set to the wanted category
league | string | set the wanted league

<aside class="success">
Remember — on this endpoint only current leagues are working. For older ones use the history endpoint.
</aside>

## Categories
This endpoint is used to get all valid categories you can use for the other endpoints.

```go
import poe "github.com/mxrk/poewatch"

categories := poe.GetCategories()
fmt.Println(categories)
```

> The above command returns JSON structured like this:

```json
[{"id":1,"name":"accessory","display":"Accessories","groups":[]},{"id":2,"name":"armour","display":"Armour","groups":[]}]
```


### HTTP Request

`GET https://api.poe.watch/categories`



## Leagues
This endpoint is used to get all valid leagues you can use for the other endpoints.

```go
import poe "github.com/mxrk/poewatch"

leagues := poe.GetLeagues()
fmt.Println(leagues)
```

> The above command returns JSON structured like this:

```json
[{"name":"Standard","start_date":"2013-01-23T21:00:00+01:00","end_date":"0001-01-01T00:00:00Z"},{"name":"Hardcore","start_date":"2013-01-23T22:00:00+01:00","end_date":"0001-01-01T00:00:00Z"}]
```


### HTTP Request

`GET https://api.poe.watch/leagues`



## History
This endpoint is used to get history data for items in a certain league. 

<aside class="notice">
Remember — you can also check data from old leagues. If you want to see which leagues are supported, check the ... endpoint.
</aside>

```go
import poe "github.com/mxrk/poewatch"

history := poe.GetItemHistory(48, "Heist")
fmt.Println(history)
```

> The above command returns JSON structured like this:

```json
[{"mean":8.87,"date":"2020-09-18T22:01:23.89+02:00","id":0},{"mean":2.31,"date":"2020-09-19T22:59:09.749+02:00","id":0},{"mean":2.22,"date":"2020-09-20T23:09:27.687+02:00","id":0},{"mean":2.17,"date":"2020-09-21T23:59:33.591+02:00","id":0}]
```


### HTTP Request

`GET https://api.poe.watch/history?id=48&league=Heist`

