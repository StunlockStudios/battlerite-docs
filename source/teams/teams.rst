.. _teams:

Teams
======================

This endpoint retrieves team objects.

**HTTP Request**

|  ``GET https://api.developer.battlerite.com/shards/global/teams?filter[season]=foo&filter[playerIds]=p1,p2``


**Required URL Parameters**

===================== ========= =====================================================================
Parameter             Default   Description
===================== ========= =====================================================================
filter[season]           none      Filter by season. Usage: filter[Season]=6
filter[playerIds]        none      Filter by playerIds in a team. Usage: filter[PlayerIds]=45,834,...
filter[gameType]         arena     Filter by gameType. Usage for royale teams: filter[gameType]=royale 
===================== ========= =====================================================================

**Shell:**


.. code-block:: shell

  curl "https://api.developer.battlerite.com/shards/global/teams?filter[playerIds]=934511096860184600&filter[season]=6" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

**The above commands returns JSON structured like this:**

.. code-block:: none

  {
    "type": "team",
    "id": "934514508356001792",
    "attributes": {
      "name": "",
      "shardId": "global",
      "stats": {
        "avatar": 0,
        "champions": [
          {
            "championId": "543520739",
            "matchesPlayed": 5
          },
          {
            "championId": "613085868",
            "matchesPlayed": 5
          },
          {
            "championId": "1134478706",
            "matchesPlayed": 1
          }
        ],
        "division": 5,
        "divisionRating": 0,
        "league": 0,
        "losses": 0,
        "members": [
          934511096860184600
        ],
        "placementGamesLeft": 6,
        "topDivision": 5,
        "topDivisionRating": 0,
        "topLeague": 0,
        "wins": 0
      },
      "titleId": "stunlock-studios-battlerite"
    }
  }

.. code-block:: shell

  curl "https://api.developer.battlerite.com/shards/global/teams?filter[playerIds]=804750644501164032&filter[season]=9&filter[gameType]=royale" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

.. code-block:: none
**The above commands returns JSON for royale teams like this: **

{
  "type": "team",
  "id": "1044982893539151872",
  "attributes": {
    "name": "",
    "shardId": "global",
    "stats": {
      "avatar": 0,
      "champions": [
        {
          "championId": "1955352790",
          "kills": 1,
          "matchesPlayed": 2,
          "placements": [
            {
              "count": 1,
              "placement": 7
            },
            {
              "count": 1,
              "placement": 13
            }
          ]
        },
        ...
      ],
      "division": 5,
      "divisionRating": 73,
      "league": 3,
      "members": [
          "804750644501164032"
      ],
      "placementGamesLeft": 0,
      "topDivision": 4,
      "topDivisionRating": 37,
      "topLeague": 3,
      "wins": 2
    },
    "titleId": "stunlock-studios-royale"
  }
}

.. toctree::
  :maxdepth: 2
