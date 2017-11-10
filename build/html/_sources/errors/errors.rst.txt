.. _errors:

Errors
=======

The server will stop processing if a problem is encountered and return an appropriate HTTP error status code. Errors may additionally include error objects, which are returned as an array keyed by errors in the top level of a JSON API document.

An error objects have the following members:

* ``title:`` (Required) the HTTP status code applicable to this problem, expressed as a string value.
* ``description:`` (Optional) a short summary of the problem

.. toctree::
  :maxdepth: 2
