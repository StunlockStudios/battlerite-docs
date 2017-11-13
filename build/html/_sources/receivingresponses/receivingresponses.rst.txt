.. _receivingresponses:

Receiving Responses
====================


Payload
---------------------------

All Server responses contain a root JSON object.

Each response will contain at least one of the following top-level members:

* ``data`` : the response's “primary data”
* ``errors`` : an array of error objects

A response may contain any of these top-level members:

* ``links``: a links object related to the primary data.
* ``included``: an array of resource objects that are related to the primary data and/or each other (“included resources”).

If a document does not contain a top-level data key, the included member will not be present either.

The following primary data is a single resource object:

.. code-block:: none

  {
    "data": {
      "type": "match",
      "id": "skarn",
      "attributes": {
        // ... this matches attributes
      },
      "relationships": {
        // ... this matches relationships
      }
    }
  }
  {
    "data": {
      "type": "match",
      "id": "1"
    }
  }


Rate Limits
---------------------------

Be nice. If you're sending too many requests too quickly, we'll send back a ``429`` error code (server unavailable).

**Please note: The default rate limit is 10 requests per minute for testing/development purposes! To increase your rate limit, log into your admin dashboard, find the app you would like a higher rate limit for, and click "request a higher rate limit"**

The rate limit headers are defined as follows:

.. code-block:: none

  X-RateLimit-Limit - Request limit per day / per minute
  X-RateLimit-Remaining - The number of requests left for the time window
  X-RateLimit-Reset - The remaining window before the rate limit is refilled in UTC epoch nanoseconds.
  
  * Limit tokens are incrementally filled by 60(sec)/ rate limit. ex: 60(sec)/10(rate) gets rate token every 6 seconds up to max rate limit.


.. toctree::
  :maxdepth: 2
