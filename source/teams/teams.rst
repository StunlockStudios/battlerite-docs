.. _teams:

Teams
======================

This endpoint retrieves team objects.

**HTTP Request**

|  ``GET https://api.dc01.gamelockerapp.com/shards/global/teams?tag[season]=foo&tag[playerIds]=p1,p2``


**Required URL Parameters**

===================== ========= =====================================================================
Parameter             Default   Description
===================== ========= =====================================================================
tag[season]           none      Filter by season. Usage: tag[Season]=6
tag[playerIds]        none      Filter by playerIds in a team. Usage: tag[PlayerIds]=45,834,...
===================== ========= =====================================================================

**Shell:**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/global/teams?tag[playerIds]=934511096860184600&tag[season]=6" \
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


.. toctree::
  :maxdepth: 2
