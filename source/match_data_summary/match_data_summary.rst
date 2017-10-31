.. _match_data_summary:

Match Data Summary
==================

Special thanks to Kashz for helping to create this! GitHub: iAm-Kashif

Match Object
---------------------------

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
Type               str             Match
ID                 str             Match ID
createdAt          str (iso8601)   Time of Match Played
duration           int             Time of match in seconds
gameMode           str             Game Mode
patchVersion       str             Version of API
shardID            str             Match Shard
stats              map             See Match.stats
assets             obj             See Match.assets
rosters            obj             See Rosters
=================  ==============  ===========================


**Match.stats (End of game statistics)**

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
endGameReason      str             "Victory" or "Defeat"
queue              str             Game Mode
=================  ==============  ===========================


**Match.assets (Telemetry Data)**

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
Type               string          asset
createdAt          str (iso8601)   Time of Telemtry creation
description        str             " "
filename           str             telemetry.json
id                 str             ID of Asset
contentType        str             application/json
name               map             telemetry
url                obj             Link to Telemetry.json file
=================  ==============  ===========================


.. toctree::
  :maxdepth: 2
