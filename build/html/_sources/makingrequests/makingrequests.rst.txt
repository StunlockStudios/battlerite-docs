.. _makingrequests:

Making Requests
===============

Content Negotiation
---------------------------

Clients using the api should specify that they accept responses using the ``application/vnd.api+json`` format, for convenience we will also accept ``application/json`` since it is the default for many popular client libraries.

The Server will respond with a ``Content-Type`` header that mirrors the format requested by the Client.

Regions
---------------------------

The Battlerite Game Data Service currently supports the following regions:

*General Region Shards:* To find data regarding live servers, where all data is found, please use the following shards.

* **North America:** ``na``
* **Europe:** ``eu``
* **South America:** ``south_america``
* **Asia:** ``asia``
* **oceania:** ``oce``

*Please note: Choosing a specific region is currently required*

To specify a region, use this code:

.. code-block:: none

  "...gamelockerapp.com/shards/<region>/..."



GZIP
---------------------------

Clients can specify the header ``Accept-Encoding: gzip`` and the server will compress responses. Responses will be returned with ``Content-Encoding: gzip``.

Given the size of matches, this can have significant performance benefits.

To specify the header Accept-Encoding, use this code:

**Shell:**

.. code-block:: shell

  -H "Accept-Encoding: gzip"


**Java:**

.. code-block:: java

  conn.setRequestProperty("Accept-Encoding","gzip");


**Python:**

.. code-block:: python

  header = {"Accept-Encoding":"gzip"}


**Go:**

.. code-block:: go

  req.Header.Set("Accept-Encoding", "gzip")



Pagination
---------------------------

Where applicable, the server allows requests to limit the number of results returned via pagination. To paginate the primary data, supply pagination information to the query portion of the request using the limit and offset parameters. To fetch items 3 through 5 you would specify a limit of 5 and an offset of 3:

If not specified, the server will default to ``offset=0``, and the following values for ``limit``:

| Matches: 5
| players/samples: 6

Note that the above values are also the maximum values for ``limit``.

.. code-block:: shell

  curl -g "https://api.dc01.gamelockerapp.com/shards/na/matches?page[limit]=5&page[offset]=3" \
  -H "Authorization: Bearer <api-key>" \
  -H "Accept: application/vnd.api+json"

At the end of the JSON returned by the above command you will find links to the first, next, and current pages:

.. code-block:: none

  "links": {
    "first": "https://api.dc01.gamelockerapp.com/shards/na/matches?page[limit]=5&page[offset]=0",
    "next": "https://api.dc01.gamelockerapp.com/shards/na/matches?page[limit]=5&page[offset]=8",
    "self": "https://api.dc01.gamelockerapp.com/shards/na/matches?page[limit]=5&page[offset]=3"
  },

There will also be a previous page link when appropriate.



Search Time
---------------------------


**Defaults:**

* Data retention period: 120 days.
* The max search time span between createdAt-start and createdAt-end: 28 days.
* If you don't specify createdAt-start, the default is now - 28 days.
* If you don't specify createdAt-end, the default is now.
* If you search for a time > now, the default is now.
* If you search for a time before the retention period, the default is the retention period (now - 120 days).
* If createdAt-start >= createdAt-end, you will receive an error.


Sorting
---------------------------

The default sort order is always ascending. Ascending corresponds to the standard order of numbers and letters, i.e. A to Z, 0 to 9). For dates and times, ascending means that earlier values precede later ones e.g. 1/1/2000 will sort ahead of 1/1/2001.

All resource collections have a default sort order. In addition, some resources provide the ability to sort according to one or more criteria ("sort fields").

If sort fields are prefixed with a minus, the order will be changed to descending.

The example below will return the oldest articles first:

.. code-block:: none

  ".../matches?sort=createdAt"

The example below will return the newest articles first:

.. code-block:: none

  ".../matches?sort=-createdAt"



JSON-P Callbacks
---------------------------

You can send a ``?callback`` parameter to any GET call to have the results wrapped in a JSON function. This is typically used when browsers want to embed content in web pages by getting around cross domain issues. The response includes the same data output as the regular API, plus the relevant HTTP Header information.

**Shell:**

.. code-block:: shell

  curl -g "https://api.dc01.gamelockerapp.com/status?callback=foo"




Cross Origin Resource Sharing
-----------------------------

This is what the CORS preflight request looks like. The API supports Cross Origin Resource Sharing (CORS) for AJAX requests from any origin. You can read the CORS W3C Recommendation, or this intro from the HTML 5 Security Guide.

Here's a sample request sent from a browser hitting http://example.com:

**Shell:**

.. code-block:: shell

  curl -i https://api.dc01.gamelockerapp.com/status -H "Origin: http://example.com"
  HTTP/1.1 200 OK
  ...
  Access-Control-Allow-Origin: *
  Access-Control-Expose-Headers: Content-Length

This is what the CORS preflight request looks like:

.. code-block:: shell

  curl -i https://api.dc01.gamelockerapp.com/status -H "Origin: http://example.com" -X OPTIONS
  HTTP/1.1 200 OK
  ...
  Access-Control-Allow-Headers: Origin,X-Title-Id,Authorization
  Access-Control-Allow-Methods: GET,POST,OPTIONS
  Access-Control-Allow-Origin: *
  Access-Control-Max-Age: 86400


.. toctree::
  :maxdepth: 2
