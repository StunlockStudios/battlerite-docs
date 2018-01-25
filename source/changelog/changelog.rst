.. _changelog:

Changelog
==========

[API] v1.6.4
--------------
Other:

- /teams endpoint now uses filter[playerIds] and filter[season] as opposed to their tag[] equivalents which are still supported for backwards compatibility

[API] v1.6.3
--------------
Bug Fixes:

- match.stats.type now includes LEAGUE2V2 and LEAGUE3V3

Other:

- Searchable tags re-enabled

[API] v1.6.2
--------------
Bug Fixes:

- Updated mapping files
- createdAt and sorting bug fix

[API] v1.6.1
--------------
Bug Fixes:

- Spectators will now be represented correctly

Other:

- Search stability improvements


[API] v1.6.0
--------------
New Features:

- rankingType and serverType filters for matches

New Data:

- Match: rankingType
- Match: serverType

Bug Fixes:

- Team member's IDs are no longer rounded

[API] v1.5.0
--------------
New Features:

- /teams endpoint now available

[API] v1.4.0
--------------
New Features:

- player name filter for /players endpoint

New Data:

- battleritePickEvent available in telemetry

[API] v1.3.0
--------------
New Features:

- steamId filter for players
- patchVersion filter for matches

New Data:

- More player stats available

New Assets:

- Mapping files for icons, names, tooltips, and tooltip variables on `GitHub <https://github.com/gamelocker/battlerite-assets>`_!

Deprecated:

- schema links
- participant.attributes.stats.userId

[API] v1.2.0
--------------
New Assets:

- Mapping files for player stackables added on `GitHub <https://github.com/gamelocker/battlerite-assets>`_!

[API] v1.1.0
--------------
New Features:

- Player endpoint is now live!

Bug Fixes:

- Participants now consistently include stats data.

.. toctree::
  :maxdepth: 2
