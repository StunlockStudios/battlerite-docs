.. _telemetry:

Telemetry
=========

Telemetry provides further insight into a match.


To retrieve Telemetry Data
---------------------------

You start by pulling a list of matches using the matches endpoint.

**HTTP Request**

``GET https://api.dc01.gamelockerapp.com/shards/global/matches``

**Shell:**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/global/matches" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

The above commands returns JSON structured like this:

.. code-block:: none

  {
    "data": [
      {
        "type": "match",
        "id": "D005654E95174996B303A17B979DC016",
        "attributes": {...},
        "relationships": {
          "assets" {
            "data": [
              {
                "type": "asset",
                "id": "b900c179-0aaa-11e7-bb12-0242ac110005"
              }
            ]
          },
          "rosters": {...},
          "rounds": {...},
          "spectators": {...}
        }
        "links": {...}
      }
    ]
    "included": [
      {...}, //Player, Roster, Participant, and Round structures
      ...
    ],
    "links": {...},
    "meta": {}
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

Once you have located this ID, you now have to search for the following JSON segment in the response object. The following response object will provide you a link to the Telemetry data

.. code-block:: none

  {
    "type": "asset",
    "id": "1ad97f85-cf9b-11e7-b84e-0a586460f004",
    "attributes": {
      "URL": "https://cdn.gamelockerapp.com/stunlock-studios-battlerite/global/2017/11/22/15/37/1ad97f85-cf9b-11e7-b84e-0a586460f004-telemetry.json",
      "createdAt": "2017-11-22T15:37:53Z",
      "description": "",
      "name": "telemetry"
    }
  },

You can download the data with following commands. Please note that you do not need API Key to get this data.

.. code-block:: shell

  curl "https://gl-prod-us-east-1.s3.amazonaws.com/assets/stunlock-studios-battlerite/na/2017/03/17/00/43/b900c179-0aaa-11e7-bb12-0242ac110005-telemetry.json" \
 	-H "Accept: application/vnd.api+json"

This request will return you a response with lines strutured as follows:

.. code-block:: none

  {"cursor":499303,"type":"com.stunlock.service.matchmaking.avro.QueueEvent","dataObject":{"time":1509652368501,"userId":"867669421479563264","teamId":"926118591642865664","sessionId":"79DED2DF8F365B2978A57071E9E9028C","season":6,"eventType":"MATCH","timeJoinedQueue":"34506717429220767","timeInQueue":2.0009074,"character":543520739,"characterArchetype":8,"queueTypes":["QUICK2V2"],"limitMatchmakingRange":false,"regionSamples":[{"region":"eu-west","latencyMS":32},{"region":"na-northeast","latencyMS":110}],"preferredRegion":"eu-west","rankingType":"UNRANKED","league":0,"division":2,"divisionRating":0,"teamSize":1,"teamMembers":[],"placementGamesLeft":6,"matchId":"7260797FD85648B295DF0AA16E17A80D","matchRegion":"eu-west","teamSide":1,"autoMatchmaking":true}}
  ...

.. toctree::
  :maxdepth: 2
