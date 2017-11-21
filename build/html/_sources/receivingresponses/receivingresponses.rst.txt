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
* ``meta``: not currently used.

If a document does not contain a top-level data key, the included member will not be present either.

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
    },
    "included": [
      {...},
      ...
    ],
    "meta": {}
  }

.. toctree::
  :maxdepth: 2
