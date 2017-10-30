.. _samples:

Samples
=======

The samples endpoint provides an easy way to access hourly batches of random match data to aggregate stats.


Get a Collection of Samples
---------------------------

This endpoint retrieves a collection of randomly selected matches.

**HTTP Request**
``GET https://api.dc01.gamelockerapp.com/shards/na/samples``


=========================== ================ ===================================================================================================================
Parameter                   Default          Description
=========================== ================ ===================================================================================================================
page[offset]                0                Allows paging over results
page[limit ]                50               The default (and current maximum) is 50.Values less than 50 and great than 2 are supported.
sort                        createdAt        By default, Matches are sorted by creation time ascending.
filter[createdAt-start]     none             Must occur before end time. Format is iso8601 Usage: filter[createdAt-start]=2017-01-01T08:25:30Z
filter[createdAt-end]       none             Queries search the last 3 hrs. Format is iso8601 i.e.filter[createdAt-end]=2017-01-01T13:25:30Z
=========================== ================ ===================================================================================================================

**Shell**

.. code-block:: python

  curl "https://api.dc01.gamelockerapp.com/shards/na/samples" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

  *The above command returns JSON structured like this:*

  {
      "type": "sample",
      "id": "sample-na-2017-02-28T07:15:30Z",
      "attributes": {
        "URL": "URL of Sample Matches",
        "createdAt": "2017-02-28T07:15:30Z",
        "shardId": "na",
        "t0": "2017-02-28T07:15:30Z",
        "t1": "2017-02-28T08:15:30Z",
        "titleId": "semc-vainglory"
      },
      "relationships": {
        "assets": {
          "data": []
        }
      }
    }

**Javascript**

.. code-block:: javascript

  //There are a variety of Java HTTP libraries that support query-parameters.

  curl "https://api.dc01.gamelockerapp.com/shards/na/samples" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

  *The above command returns JSON structured like this:*

  {
      "type": "sample",
      "id": "sample-na-2017-02-28T07:15:30Z",
      "attributes": {
        "URL": "URL of Sample Matches",
        "createdAt": "2017-02-28T07:15:30Z",
        "shardId": "na",
        "t0": "2017-02-28T07:15:30Z",
        "t1": "2017-02-28T08:15:30Z",
        "titleId": "semc-vainglory"
      },
      "relationships": {
        "assets": {
          "data": []
        }
      }
    }

.. toctree::
  :maxdepth: 2
