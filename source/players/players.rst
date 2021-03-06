.. _players:

Players
======================

Player objects contain aggregated lifetime information about each Player. The stats object contains several StackableIDs and their values. The mappings for these IDs can be found at https://github.com/StunlockStudios/battlerite-assets.

There are stats for both Arena and Royale.


Get a Single Player
--------------------

This endpoint retrieves a specific player.

**HTTP Request**

|  ``GET https://api.developer.battlerite.com/shards/global/players/<ID>``


**URL Parameters**

=========== ========= ==================================
Parameter   Default   Description
=========== ========= ==================================
ID          none      The ID of the player to retrieve
=========== ========= ==================================


**Shell:**

.. code-block:: shell

  curl "https://api.developer.battlerite.com/shards/global/players/<ID>" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

**The above commands returns JSON structured like this:**

.. code-block:: none

  {
    "data": {
      "type": "player",
      "id": "931405258914193408",
      "attributes": {
        "name": "",
        "patchVersion": "",
        "shardId": "",
        "stats": {
          ...
        }
        "titleId": ""
      },
      "relationships": {
        "assets": {
          "data": []
        }
      },
      "links": {
        "schema": "https://raw.githubusercontent.com/madglory/gamelocker-/master/schemas/player_index.json",
        "self": "https://api.developer.battlerite.com/shards/global/players/931405258914193408"
      }
    }
  }


Get a Collection of Players
---------------------------

This endpoint retrieves a collection of up to 6 players, filtered by id.

**HTTP Request**

|  ``GET https://api.developer.battlerite.com/shards/global/players``


**Query Parameters**

===================== ========= =====================================================================
Parameter             Default   Description
===================== ========= =====================================================================
filter[playerIds]     none      Filter by player ids. Usage: filter[playerIds]=id1,id2,...
filter[steamIds]      none      Filter by player's steam ids. Usage: filter[steamIds]=id1,id2,...
filter[playerNames]   none      Filter by player names. Usage: filter[playerNames]=name1,name2,...
===================== ========= =====================================================================


**Shell:**

.. code-block:: shell

  curl "https://api.developer.battlerite.com/shards/global/players?filter[playerIds]=player1Id,player2Id" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

.. toctree::
  :maxdepth: 2
