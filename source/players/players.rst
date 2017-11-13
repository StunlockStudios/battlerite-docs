.. _players:

Players
=======

Player objects contain aggregated lifetime information about each Player. At this time Players are fairly sparse, but there are plans to add much richer data as it becomes available.


Get a Single Player
--------------------

This endpoint retrieves a specific player.

* If a player has changed names, it is possible that there are multiple ID's for a single player name.
* Player renames do not trigger a change on this endpoint. A minimum of 1 match after the rename is required to view the change.

*Please Note: Changes Coming! - Player resources are not fully defined at this point, but are included so that consumers can get basic info (name, etc.) This object will have additional data added over the next few months, and may change slightly as data moves from the `attributes.stats` object to the main `attributes` object.*

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

  curl "https://api.dc01.gamelockerapp.com/shards/na/players/<ID>" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

**The above commands returns JSON structured like this:**

.. code-block:: none

  {
    "data": {
      "type": "player",
      "id": "6abb30de-7cb8-11e4-8bd3-06eb725f8a76"
      "attributes": {
        "name": "..."
        "stats": {
          ...
        },
        "titleId": "stunlock-battlerite",
        "shardId": "na",
        "createdAt": "2017-11-02T19:52:48.623Z",
        "patchVersion": "0.14"
      },
    }
  }


Get a Collection of Players
---------------------------

This endpoint retrieves a collection of up to 6 players, filtered by name. Player names are specific to each region.

**HTTP Request**

|  ``GET https://api.dc01.gamelockerapp.com/shards/na/players``


**Query Parameters**

===================== ========= =====================================================================
Parameter             Default   Description
===================== ========= =====================================================================
filter[playerNames]   none      Filters by player names. Usage: filter[playerNames]=player1,player2
===================== ========= =====================================================================


**Shell:**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/na/players?filter[playerNames]=player1,player2" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

.. toctree::
  :maxdepth: 2
