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

Welcome to the poe.watch API! You can use our API to access poe.watch API endpoints.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Get

## Get all armours

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[{"id":6,"name":"Wreath of Phrecia","category":"armour","group":"helmets","frame":3,"influences":null,"linkCount":0,"icon":"https://web.poecdn.com/image/Art/2DItems/Armours/Helmets/Wreath_of_Phrecia.png?v=0557bfae422aebfaa3ac32bee72fe98e\u0026w=2\u0026h=2\u0026scale=1","mean":13.2,"mode":0,"min":1.6,"max":13.2,"exalted":0.16,"total":0,"daily":169,"current":0,"accepted":0,"change":214,"history":[2.78,1.95,3.75,3.5,4.85,4.42,8.2],"lowConfidence":false,"perfectPrice":10.28,"perfectAmount":0,"implicits":null,"explicits":["Has no Attribute Requirements","Increases and Reductions to Light Radius also apply to Area of Effect at 50% of their value","Increases and Reductions to Light Radius also apply to Damage","(15-25)% increased Light Radius","Deal no Chaos Damage"]},{"id":9,"name":"Rainbowstride","category":"armour","group":"boots","frame":3,"influences":null,"linkCount":0,"icon":"https://web.poecdn.com/image/Art/2DItems/Armours/Boots/rainbowstride.png?v=d24bcacbebe0317035b25ecea7a21776\u0026w=2\u0026h=2\u0026scale=1","mean":2.24,"mode":0,"min":2.21,"max":2.29,"exalted":0.03,"total":0,"daily":5634,"current":0,"accepted":0,"change":-36,"history":[3.85,3.32,3.23,3.6,3.58,3.56,3.36],"lowConfidence":false,"perfectPrice":17.08,"perfectAmount":0,"implicits":null,"explicits":["(4-6)% Chance to Block Spell Damage","(140-180)% increased Energy Shield","+(40-60) to maximum Mana","+20% to all Elemental Resistances","25% increased Movement Speed"]}]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://api.poe.watch/get?category=armour&league=Heist`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
category | false | set to the wanted category
league | true | set the wanted league

<aside class="success">
Remember — on this endpoint only current leagues are working. For older ones use the history endpoint.
</aside>


