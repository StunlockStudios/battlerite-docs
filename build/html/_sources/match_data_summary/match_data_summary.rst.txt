.. _match_data_summary:

Match Data Summary
==================

Match Object
---------------------------

=================  ==============  ==================================
Variable    	   Type            Description
=================  ==============  ==================================
type               str             Match
id                 str             Match ID
createdAt          str (iso8601)   Time of Match Played
duration           int             Duration of match in seconds
gameMode           str             Game Mode
patchVersion       str             Version of the game
shardID            str             Region Shard
stats              map             Stats particular to the match
tags               map             Searchable tags. See Match.tags
assets             obj             See Match.assets
rosters            obj             See Rosters
rounds             obj             See Rounds
spectators         obj             Participants that are spectating
titleId            string          Identifies the studio and game
=================  ==============  ==================================


**Match.assets (Telemetry Data)**

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
type               str             Asset
createdAt          str (iso8601)   Time of Telemtry creation
description        str             NA
filename           str             telemetry.json
id                 str             ID of Asset
contentType        str             application/json
name               map             Telemetry
URL                str             Link to Telemetry.json file
shardId            str             Region Shard
=================  ==============  ===========================

**Match.tags**

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
serverType         string          Match server type
rankingType        string          Match ranking type
=================  ==============  ===========================

Rounds Object
---------------------------

=================  ==============  ===============================
Variable    	   Type            Description
=================  ==============  ===============================
id                 str             Round ID
ordinal            int64           Round Index
participants       obj             List of participants
stats              map             Stats particular to the round
duration           int64           Length of the Match
=================  ==============  ===============================

Rosters Object
---------------------------

=================  ==============  =================================
Variable    	   Type            Description
=================  ==============  =================================
id                 str             ID of Roster
type               str             Roster
participants       obj             See Participants
stats              obj             Stats particular to rosters
team               obj             See Rosters.team
won                str             Indicates if a roster won
shardId            str             Region Shard
=================  ==============  =================================

**Rosters.team**

=================  ==============  ================================
Variable    	   Type            Description
=================  ==============  ================================
id                 str             ID of Team or None
name               str             Name of Team or None
type               str             Team
titleId            str             Identifies the studio and game
shardId            str             Region Shard
assets             obj             NA
=================  ==============  ================================

Participants Object
---------------------------

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
actor              str             Hero
id                 str             Same as ID of Roster
player             obj             See Participants.player
stats              map             See Paticipants.stats
type               str             participants
=================  ==============  ===========================

**Participants.player**

=================  ==============  ================================
Variable    	   Type            Description
=================  ==============  ================================
id                 str             UID of player
type               str             Player
=================  ==============  ================================

.. toctree::
  :maxdepth: 2
