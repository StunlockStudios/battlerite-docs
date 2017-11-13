.. _telemetry:

Telemetry
=========

The telemtry data provides us with insights into a match. It gives us details of various events that happened in the match, along with the time when they happened. Some of the events also have a location which can be plotted on a Battlerite Game map. Telemetry is very useful to generate a timeline visualtions of how the match went for replays, or create heatmaps of where a certin hero or ability is most useful. These are just some of the exmaples of where Telemtry can be used.


To get Telemetry Data
---------------------------

You start by pulling a list of matches using the matches endopoint.

**HTTP Request**

``GET https://api.dc01.gamelockerapp.com/shards/na/matches``

**Shell:**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/na/matches" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

The above commands returns JSON structured like this:

.. code-block:: none

  {
    "data": [
      {
        "type": "match",
        "id": "02b90214-c64d-11e6-9f6b-062445d3d668",
        "attributes": {
          "createdAt": "2017-11-10T20:30:08Z",
          "duration": 1482195372,
          "gameMode": "...",
          "patchVersion": "0.14",
          "shardId": "na",
          "stats": {
            "mapID": "417DE573937D74E39BF40EB6CF82670B",
            "type": "VSAI"
          }
        },
        "relationships": {
          "data": [
            "rounds": [
              {...},
              ...
            ]
          ],
          "rosters": {
            "data": [
              {...},
              ...
            ]
          },
          "assets": {
            "data" [
              {
                "type": "asset",
                "id": "b900c179-0aaa-11e7-bb12-0242ac110005"
              }
            ]
          }
        }
      }
    ]
  }

You need to look for an ``Assets`` JSON node which points to telemetry. Check for the following in the response:

.. code-block:: none

  "relationships": {
    "assets": {
      "data": [
        {
          "type": "asset",
          "id": "b900c179-0aaa-11e7-bb12-0242ac110005"
        }
      ]
    }
  }

Once you have located this ID, you now have to search for the following JSON segment in the response object. The following response object will provide you a link to the Telemtry data

.. code-block:: none

  {
    "type": "asset",
    "id": "b900c179-0aaa-11e7-bb12-0242ac110005",
    "titleId": "stunlock-battlerite",
    "shardId": "na",
    "attributes": {
      "URL": "https://gl-prod-us-east-1.s3.amazonaws.com/assets/stunlock-battlerite/na/2017/11/10/00/43/b900c179-0aaa-11e7-bb12-0242ac110005-telemetry.json",
      "contentType": "application/json",
      "createdAt": "2017-03-17T00:43:22Z",
      "description": "",
      "filename": "telemetry.json",
      "name": "telemetry"
    }
  },

You can download the data with following commands. Please note that you do not need API Key to get this data.

.. code-block:: shell

  curl "https://gl-prod-us-east-1.s3.amazonaws.com/assets/stunlock-battlerite/na/2017/03/17/00/43/b900c179-0aaa-11e7-bb12-0242ac110005-telemetry.json" \
 	-H "Accept: application/vnd.api+json"

This request will return you a response as follows:

.. code-block:: none

  {
    "time": "2017-02-18T06:37:15+0000",
    "type": "DealDamage",
    "payload": {
      ...
    }
  }



.. toctree::
  :maxdepth: 2
