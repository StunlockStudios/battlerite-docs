.. _matches:

Matches
=======

Match records are created every time players complete a game session. Each Match contains high level information about the game session, i.e. duration, gameMode, etc. Each Match has two Rosters.


Rosters
----------------------

Rosters track the scores of each opposing group of Participants. If players entered matchmaking as a team, the Roster will have a related Team. Rosters have many Participants objects, one for each member of the Roster. Roster objects are only meaningful within the context of a Match and are not exposed as a standalone resource.

.. code-block:: none

  {
    "type": "roster",
    "id": "eca49808-d510-11e6-bf26-cec0c932ce01",
    "attributes": {
      "shardId": "global"
      "stats": {
        "score": 3
        "side": 1,
      },
      "won": "true",
    },
    "relationships": {
      "participants": {
        "data": [
          {
            "type": "participant",
            "id": "eca49a7e-d510-11e6-bf26-cec0c932ce01"
          },
          "etc..."
        ]
      }
      "team": {
        "data": {...}
      },
    }
  }



Participants
---------------------------

Participant objects track each member in a Roster. Participants may be anonymous Players, registered Players, or bots. In the case where the Participant is a registered Player, the Participant will have a single Player relationship. Participant objects are only meaningful within the context of a Match and are not exposed as a standalone resource.

.. code-block:: none

  {
    "type": "participant",
    "id": "ea77c3a7-d44e-11e6-8f77-0242ac130004",
    "attributes": {
      "actor": "65687534",
      "shardId": "global"
      "stats": {
        "attachment": 578166028,
        "emote": 1505065066,
        "mount": 1302058678,
        "outfit": 1890030881
      },
    }
    "relationships": {
      "player": {
        "data": {
          "type": "player",
          "id": "932723402744184832"
        }
      }
    }
  }


Rounds
---------------------------

Round objects contain an overview of a round played, including information such as the round's duration, order in a match, participants, and the winning team. Round objects are only meaningful within the context of a Match and are not exposed as a standalone resource.

.. code-block:: none

  {
    "type": "round",
    "id": "b93e40bf-f488-4e16-a277-f53deda4e3fb",
    "attributes": {
      "duration": 95,
      "ordinal": 2,
      "stats": {
        "winningTeam": 2
      }
    },
    "relationships": {
      "participants": {
        "data": []
      }
    }
  },


Get a Collection of Matches
---------------------------

This endpoint retrieves data from matches.

*Please keep in mind that bulk scraping matches is prohibited.*

**HTTP Request**

``GET https://api.dc01.gamelockerapp.com/shards/global/matches``

**Query Parameters**

========================= =========== =================================================================================================================
Parameter                 Default     Description
========================= =========== =================================================================================================================
page[offset]              0           Allows paging over results
page[limit]               5           The default (and current maximum) is 5. Values less than 5 and greater than 1 are supported.
sort                      createdAt   By default, Matches are sorted by creation time ascending.
filter[createdAt-start]   Now-28days  Must occur before end time. Format is iso8601 Usage: filter[createdAt-start]=2017-01-01T08:25:30Z
filter[createdAt-end]     Now         Queries search the last 3 hrs. Format is iso8601 i.e.filter[createdAt-end]=2017-01-01T13:25:30Z
filter[playerNames]       none        Filters by player name. Usage: filter[playerNames]=player1,player2,...
filter[playerIds]         none        Filters by player Id. Usage:filter[playerIds]=playerId,playerId,...
filter[teamNames]         none        Filters by team names. Team names are the same as the in game team tags. Usage: filter[teamNames]=TSM,team2,...
filter[gameMode]          none        Filter by gameMode Usage: filter[gameMode]=casual,ranked,...
========================= =========== =================================================================================================================

*Remember — a happy match is an authenticated match!*

**Shell:**

.. code-block:: shell

  curl -g "https://api.dc01.gamelockerapp.com/shards/global/matches?sort=createdAt&page[limit]=3&filter[createdAt-start]=2017-11-10T13:25:30Z&filter[playerNames]=<playerName>" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

**Python:**

.. code-block:: python

  import requests

  url = "https://api.dc01.gamelockerapp.com/shards/global/matches"

  header = {
    "Authorization": "<api-key>",
    "Accept": "application/vnd.api+json"
  }

  query = {
    "sort": "createdAt",
    "filter[playerNames]": "<playerName>",
    "filter[createdAt-start]": "2017-11-10T13:25:30Z",
    "page[limit]": "3"
  }

  r = requests.get(url, headers=header, params=query)

**Go:**

.. code-block:: go

  q := req.URL.Query()
  q.Add("sort", "createdAt")
  q.Add("filter[playerNames]", "<playerName>")
  q.Add("filter[createdAt-start]", "2017-11-10T13:25:30Z")
  q.Add("page[limit]", "3")
  req.URL.RawQuery = q.Encode()
  res, _ := client.Do(req)

The above commands returns JSON structured like this:

.. code-block:: none

  {
    "data": [
      {
        "type": "match",
        "id": "D005654E95174996B303A17B979DC016",
        "attributes": {
          "createdAt": "2017-11-10T20:30:08Z",
          "duration": 492,
          "gameMode": "1733162751",
          "patchVersion": "1.0",
          "shardId": "global",
          "stats": {
            "mapID": "417DE573937D74E39BF40EB6CF82670B",
            "type": "QUICK2V2 ",
          },
          "titleId": "stunlock-studios-battlerite"
        },
        "relationships": {
          "assets" {
            "data": [
              {
                "type": "asset",
                "id": "1ad97f85-cf9b-11e7-b84e-0a586460f004"
              }
            ]
          },
          "rosters": {
            "data": [
              {
                "type": "roster",
                "id": "ea77c2eb-d44e-11e6-8f77-0242ac130004"
              },
              ...
            ]
          },
          "rounds": {
            "data": [
              {
                "type": "round",
                "id": "b7326b70-1473-48b4-a30b-3eb9bb319541"
              }
              ...
            ]
          },
          "spectators": {
            "data": []
          }
        }
        "links": {
          "schema": "schema": "https://raw.githubusercontent.com/madglory/gamelocker-stunlock-studios-battlerite/master/schemas/1.0/match_index.json",
          "self": "https://api.dc01.gamelockerapp.com/shards/global/matches/D005654E95174996B303A17B979DC016"
        }
      }
    ]
    "included": [
      {...}, //Player, Roster, Participant, asset, and Round structures
      ...
    ],
    "links": {
      ...
    },
    "meta": {}
  }

Get a Single Match
---------------------------

This endpoint retrieves a specific match.

**HTTP Request**

``GET https://api.dc01.gamelockerapp.com/shards/global/matches/<ID>``

**URL Parameters**

=========== ========= =================================
Parameter   Default   Description
=========== ========= =================================
ID          none      The ID of the match to retrieve
=========== ========= =================================

**Shell:**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/global/matches/<matchID>" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

The above commands returns JSON structured like this:

.. code-block:: none

  {
    "data": [
      {...}, //Match structures
      ...
    ]
    "included": [
      {...}, //Player, Roster, Participant, asset, and Round structures
      ...
    ],
    "links": {
      ...
    },
    "meta": {}
  }

.. toctree::
  :maxdepth: 2
