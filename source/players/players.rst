.. _players:

Players
=======

Player objects contain aggregated lifetime information about each Player. At this time Players are fairly sparse, but there are plans to add much richer data as it becomes available.



Get a Single Player
---------------------------

This endpoint retrieves a specific player.

*Please Note: Changes Coming! - Player resources are not fully defined at this point, but are included so that consumers can get basic info (name, etc.) This object will have additional data added over the next few months, and may change slightly as data moves from the `attributes.stats` object to the main `attributes` object.*

**HTTP Request**
``GET https://api.dc01.gamelockerapp.com/shards/na/players/<ID>``

**URL Parameters**

Parameter: ID
Description: The ID of the player to retrieve

**Shell**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/na/players/<ID>" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

    **The above command returns JSON structured like this:**

	  {{
	"data": {
	  "attributes": {
	      "stats": {
	          "lossStreak": 1,
	          "winStreak": 0,
	          "lifetimeGold": 10536.0
	      },
	      "name": "boombastic04"
	  },
	  "type": "player",
	  "id": "6abb30de-7cb8-11e4-8bd3-06eb725f8a76"
	}
	}

**Javascript**

.. code-block:: shell

  //There are a variety of Java HTTP libraries that support query-parameters.

    **The above command returns JSON structured like this:**

	  {{
	"data": {
	  "attributes": {
	      "stats": {
	          "lossStreak": 1,
	          "winStreak": 0,
	          "lifetimeGold": 10536.0
	      },
	      "name": "boombastic04"
	  },
	  "type": "player",
	  "id": "6abb30de-7cb8-11e4-8bd3-06eb725f8a76"
	}
	}


Get a Collection of Players
---------------------------


.. toctree::
  :maxdepth: 2
