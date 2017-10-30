.. _teams:

Teams
=====

Team objects contain aggregated lifetime information about each Team.

Get a collection of Teams
---------------------------

This endpoint retrieves a collection of up to 6 teams.

*Important - Team resources are not yet available in the API.*

**HTTP Request**
``GET https://api.dc01.gamelockerapp.com/teams``

**URL Parameters**
=========================== ================ =================================================================================================================== 
Parameter                   Default          Description                                               
=========================== ================ ===================================================================================================================
filter[teamNames]           none             Filters by team name. Usage: filter[teamNames]=team1                                     
filter[teamIds]             none             Filter by team id. Usage: filter[teamIds]=12345             
=========================== ================ ===================================================================================================================

*Remember — a happy team is an authenticated team!*

**Shell**

.. code-block:: shell

  curl "https://api.dc01.gamelockerapp.com/shards/na/teams?filter[teamNames]=team1" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

Get a Single Team
---------------------------

This endpoint retrieves a specific team.

**HTTP Request**
``GET https://api.dc01.gamelockerapp.com/teams/<ID>``

**URL Parameters**
=========================== =================================================================================================================== 
Parameter                   Description                                               
=========================== =================================================================================================================== 
ID                          The ID of the team to retrieve                                            
=========================== =================================================================================================================== 


**Shell**

.. code-block:: shell

	  curl "https://api.dc01.gamelockerapp.com/teams/<ID>" \
	  -H "Authorization: Bearer <api-key>" \
	  -H "Accept: application/vnd.api+json"

	  The above command returns JSON structured like this:
	  
	{
	  "id": 2,
	  "name": "Max",
	  "breed": "unknown",
	  "fluffiness": 5,
	  "cuteness": 10
	}

.. toctree::
  :maxdepth: 2
