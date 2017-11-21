Rate Limits
=============

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
