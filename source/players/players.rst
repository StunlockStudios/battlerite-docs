.. _players:

Players (Coming Soon!)
======================

Player objects contain aggregated lifetime information about each Player.


Get a Single Player
--------------------

This endpoint retrieves a specific player.

**HTTP Request**

|  ``GET https://api.dc01.gamelockerapp.com/shards/na/players/<ID>``


**URL Parameters**

=========== ========= ==================================
Parameter   Default   Description
=========== ========= ==================================
ID          none      The ID of the player to retrieve
=========== ========= ==================================


**Shell:**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/global/players/<ID>" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

**The above commands returns JSON structured like this:**

.. code-block:: none

  {
    "data": {
      "type": "player",
      "id": "931405258914193408"
      "attributes": {
        "name": ""
        "patchVersion": ""
        "shardId": "",
        "stats": null,
        "titleId": ""
      },
      "relationships" {
        "assets": {
          "data": []
        }
      },
      "links": {
        "schema": "https://raw.githubusercontent.com/madglory/gamelocker-/master/schemas//player_index.json",
        "self": "https://api.dc01.gamelockerapp.com/shards//players/931405258914193408"
      }
    }
  }


Get a Collection of Players
---------------------------

This endpoint retrieves a collection of up to 6 players, filtered by name or id. Player names are specific to each region.

**HTTP Request**

|  ``GET https://api.dc01.gamelockerapp.com/shards/global/players``


**Query Parameters**

===================== ========= =====================================================================
Parameter             Default   Description
===================== ========= =====================================================================
filter[playerNames]   none      Filters by player names. Usage: filter[playerNames]=player1,player2
filter[playerIds]     none      Filter by player ids. Usage: filter[playerIds]=id1,id2,...
===================== ========= =====================================================================


**Shell:**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/global/players?filter[playerNames]=player1,player2" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

.. toctree::
  :maxdepth: 2
