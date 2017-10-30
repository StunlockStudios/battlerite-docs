.. _makingrequests:

Making Requests
===============

Content Negotiation
---------------------------

Content Negotiation
Clients using the api should specify that they accept responses using the ``application/vnd.api+json``format, for convenience we will also accept ``application/json`` since it is the default for many popular client libraries.

The Server will respond with a ``Content-Type`` header that mirrors the format requested by the Client.

Regions
---------------------------

The Vainglory Game Data Service currently supports the following regions:

*General Region Shards*

To find data regarding live servers, where all data is found, please use the following shards.

* **North America:** ``na``
* **Europe:** ``eu:``
* **South America:** ``sa``
* **East Asia:** ``ea``
* **Southeast Asia (SEA):** ``sg``

*Tournament Region Shards*

To find data regarding professional eSport, which take place on the private client only, please use the following shards.

* **North America Tournaments:** ``tournament-na``
* **Europe Tournaments:** ``tournament-eu``
* **South America Tournaments:** ``tournament-sa``
* **East Asia Tournaments:** ``tournament-ea``
* **Southeast Asia Tournaments:** :tournament-sg:

*Choosing a specific region is currently required*

**Javascript**

.. code-block:: javascript

  To specify a region, use this code:

  "...gamelockerapp.com/shards/<region>/..."

GZIP
---------------------------

Clients can specify the header ``Accept-Encoding: gzip`` and the server will compress responses.
Responses will be returns with ``Content-Encoding: gzip``.

Given the size of matches, this can have significant performance benefits.

**Shell**

.. code-block:: javascript

  To specify the header Accept-Encoding, use this code:

  -H "Accept-Encoding: gzip"

**Java**

.. code-block:: java

  To specify the header Accept-Encoding, use this code:

  conn.setRequestProperty("Accept-Encoding","gzip");

**Python**

.. code-block:: python

  To specify the header Accept-Encoding, use this code:

  header = {"Accept-Encoding":"gzip"}

**Go**

.. code-block:: go

  To specify the header Accept-Encoding, use this code:

  req.Header.Set("Accept-Encoding", "gzip")

Pagination
---------------------------

Where applicable, the server allows requests to limit the number of results returned via pagination. To paginate the primary data, supply pagination information to the query portion of the request using the limit and offset parameters. To fetch items 2 through 10 you would specify a limit of 8 and an offset of 2:

If not specified, the server will default for matches to ``limit=5`` and ``offset=0``, and for players/samples to ``limit=50`` and ``offset=0``

 *Important - Currently the server will not allow responses with over 50 primary data objects*

Search Time
---------------------------

* Data retention period: 120 days.
* The max search time span between createdAt-start and createdAt-end: 28 days.

**Defaults:**
* If you don't specify createdAt-start, the default is now - 28 days.
* If you don't specify createdAt-end, the default is now.
* If you search for a time > now, the default is now.
* If you search for a time before the retention period, the default is the retention period (now - 120 days).
* If createdAt-start >= createdAt-end, you will receive an error.

Sorting
---------------------------

The default sort order is always ascending. Ascending corresponds to the standard order of numbers and letters, i.e. A to Z, 0 to 9). For dates and times, ascending means that earlier values precede later ones e.g. 1/1/2000 will sort ahead of 1/1/2001.

All resource collections have a default sort order. In addition, some resources provide the ability to sort according to one or more criteria ("sort fields").

If sort fields are is prefixed with a minus, the order will be changed to descending.

**Javascript**

.. code-block:: javascript

  **The example below will return the oldest articles first:**
  ".../matches?sort=createdAt"

  **The example below will return the newest articles first:**
  ".../matches?sort=-createdAt"

JSON-P Callbacks
---------------------------

You can send a ?callback parameter to any GET call to have the results wrapped in a JSON function. This is typically used when browsers want to embed content in web pages by getting around cross domain issues. The response includes the same data output as the regular API, plus the relevant HTTP Header information.

**Shell**

.. code-block:: shell

  curl -g "https://api.dc01.gamelockerapp.com/status?callback=foo"


Cross Origin Resource Sharing
-----------------------------

This is what the CORS preflight request looks like. The API supports Cross Origin Resource Sharing (CORS) for AJAX requests from any origin. You can read the CORS W3C Recommendation, or this intro from the HTML 5 Security Guide.

Here's a sample request sent from a browser hitting http://example.com:

**Shell**

.. code-block:: shell

  curl -i https://api.dc01.gamelockerapp.com/status -H "Origin: http://example.com"
  HTTP/1.1 200 OK
  ...
  Access-Control-Allow-Origin: *
  Access-Control-Expose-Headers: Content-Length

  This is what the CORS preflight request looks like:

  curl -i https://api.dc01.gamelockerapp.com/status -H "Origin: http://example.com" -X OPTIONS
  HTTP/1.1 200 OK
  ...
  Access-Control-Allow-Headers: Origin,X-Title-Id,Authorization
  Access-Control-Allow-Methods: GET,POST,OPTIONS
  Access-Control-Allow-Origin: *
  Access-Control-Max-Age: 86400




.. toctree::
  :maxdepth: 2
