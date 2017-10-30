.. _links:

Links
======

Get a Link
---------------------------

This endpoint checks to see if a link object exists for a given code.

**HTTP Request**
``GET https://api.dc01.gamelockerapp.com/link``

**Shell**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/na/link/{id}" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

Post a Link
---------------------------

This endpoint creates a PlayerLink object if the verification code matches the one provided by the game.

**HTTP Request**
``POST https://api.dc01.gamelockerapp.com/link/{player_id}``

**Query Parameters**
=========================== =================================================================================================================== 
Parameter                   Description                                               
=========================== =================================================================================================================== 
code                        The verification code                                           
=========================== =================================================================================================================== 

**Shell**

.. code-block:: shell

  curl -XPOST "https://api.dc01.gamelockerapp.com/shards/na/link/{player_id}" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"


Player Link
---------------------------

**Shell**

.. code-block:: shell

	  {
	  "attributes": {
	      "playerId": "fb374a7b-78be-4fcc-83ed-6a532a8a6f55",
	      "shardId": "na",
	      "titleId": "semc-vainglory"
	  },
	  "id": "2454e5ac-0a69-4468-ad12-8616f066e817",
	  "type": "playerLink"
	}

.. toctree::
  :maxdepth: 2
