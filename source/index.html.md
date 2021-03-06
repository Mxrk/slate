---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
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
 ```shell
    curl https://api.poe.watch/get?category=armour&league=Heist
 ```

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

 ```shell
    curl https://api.poe.watch/get?category=waepon&league=Heist
 ```


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

## Get all x
It's exactly like the endpoints above, just use a valid category from the categories endpoint.

## Filters
You can use specific filters to get filtered results on all get categories.
Currently the following filters are available:
"gemLevel", "gemCorrupted", "lowConfidence", "itemLevel", "linkCount"


 ```shell
    curl https://api.poe.watch/get?categories=weapon&league=Heist&lowConfidence=true
 ```



# Categories
This endpoint is used to get all valid categories you can use for the other endpoints.

 ```shell
    curl https://api.poe.watch/categories
 ```

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



# Leagues
This endpoint is used to get all valid leagues you can use for the other endpoints.

 ```shell
    curl https://api.poe.watch/leagues
 ```

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



# History
This endpoint is used to get history data for items in a certain league. 

<aside class="notice">
Remember — you can also check data from old leagues. If you want to see which leagues are supported, check the ... endpoint.
</aside>

 ```shell
    curl https://api.poe.watch/history?id=48&league=Heist
 ```


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

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | int | wanted item id
league | string | set the wanted league


# Enchant
This endpoint is used to get enchat data for a specific item in a certain league. 

```shell
    curl https://api.poe.watch/enchants?id=79&league=Heist
 ```

> The above command returns JSON structured like this:

```json
[
  {
    "name": "Penance Brand has 24% increased Area of Effect",
    "value": 34.38,
    "lowConfidence": true
  },
  {
    "name": "Sunder has 40% increased Damage",
    "value": 2.29,
    "lowConfidence": true
  }
]
```


### HTTP Request

`GET https://api.poe.watch/enchants?id=79&league=Heist`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | int | wanted item id
league | string | set the wanted league


# Corruptions
You can query for a list of corruption prices for a specific ID.


### HTTP Request

`GET https://api.poe.watch/corruptions?id=155&league=Ritual`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | int | wanted item id
league | string | set the wanted league

```shell
    curl https://api.poe.watch/corruptions?id=155&league=Ritual
 ```

> The above command returns JSON structured like this:

```json
[

    {
        "name": "#% increased Area of Effect",
        "mean": 8511.44
    },
    {
        "name": "#% increased Attack Speed during any Flask Effect",
        "mean": 9892.36
    },
  ...
]
```

# Compact
Returns a compact data from all "get?" endpoints combined.

```shell
    curl https://api.poe.watch/compact?league=Heist
 ```

> The above command returns JSON structured like this:

```json
{
  "items": [
    {
      "id": 48,
      "name": "Devouring Totem",
      "category": "",
      "group": "",
      "frame": 4,
      "influences": null,
      "icon": "https://web.poecdn.com/image/Art/2DItems/Gems/DevouringTotem.png?v=f056a6f62ebac73b19eb9baa93ffef16&w=1&h=1&scale=1",
      "mean": 10.14,
      "mode": 0,
      "min": 10.14,
      "max": 10.14,
      "exalted": 0.14,
      "total": 0,
      "daily": 156,
      "current": 0,
      "accepted": 0,
      "change": 119,
      "history": [
        4.14,
        3.45,
        3.66,
        3.97,
        3.98,
        3.62,
        2.7
      ],
      "lowConfidence": false,
      "implicits": null,
      "explicits": null,
      "gemLevel": 21,
      "gemQuality": 23,
      "gemIsCorrupted": true,
      "essenceTier": 0,
      "watchstonesUses": 0,
      "linkCount": 0,
      "mapSeries": 0,
      "mapTier": 0
    }
  ]
}
```


### HTTP Request

`GET https://api.poe.watch/compact?league=Heist`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
league | string | set the wanted league

# Stash
This endpoint returns the latest stash ID and the computed stashes in the current iteration (not really useful for other people.)

```shell
    curl https://api.poe.watch/status
 ```

> The above command returns JSON structured like this:

```json
{
  "changeID": "863692164-876193549-838143009-945188005-904612949",
  "requestedStashes": 31739,
  "computedStashes": 31736
}
```


### HTTP Request

`GET https://api.poe.watch/status`
