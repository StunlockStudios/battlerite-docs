.. _match_data_summary:

Match Data Summary
==================

Special thanks to Kashz for helping to create this! GitHub: iAm-Kashif

Match Object
---------------------------

=================  ==============  ==================================
Variable    	   Type            Description
=================  ==============  ==================================
Type               str             Match
ID                 str             Match ID
createdAt          str (iso8601)   Time of Match Played
duration           int             Time of match in seconds
gameMode           str             Game Mode
patchVersion       str             Version of the game
shardID            str             Match Shard
stats              map             See Match.stats
assets             obj             See Match.assets
rosters            obj             See Rosters
rounds             obj             See Rounds
spectators         obj             Participants that are spectating
titleId            string          Identifies the studio and game
=================  ==============  ==================================


**Match.stats (End of game statistics)**

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
mapID              str             Map ID
type               str             Type of Match Played
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
shardId            str             Region Shard
=================  ==============  ===========================

Rounds Object
---------------------------

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
id                 str             Round ID
ordinal            int64           Round Index
stats              map             See Rounds.stats
duration           int64           Length of the Match
=================  ==============  ===========================

**Rounds.stats**

=================  ==============  ===========================
Variable    	   Type            Description
=================  ==============  ===========================
winningTeam        int             Winning Team
=================  ==============  ===========================

Rosters Object
---------------------------

=================  ==============  =================================
Variable    	   Type            Description
=================  ==============  =================================
id                 str             ID of Roster
type               str             Roster
participants       obj             See Participants
stats              obj             See Rosters.stats (coming soon)
team               obj             See Rosters.team
won                str             Indiciates if a roster won
shardId            str             Region Shard
=================  ==============  =================================

**Rosters.team**

=================  ==============  ================================
Variable    	   Type            Description
=================  ==============  ================================
id                 str             ID of Team or None
name               str             Name of Team or None
type               str             team
titleId            str             Identifies the studio and game
shardId            str             Region Shard
createdAt          str (iso8601)   Team creation time
assets             obj             Same structure as Match.assets
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
name               str             IGN of player
stats              map             Player Stats
type               str             Player
titleId            str             The studio and game title
shardId            str             Region Shard
createdAt          str (iso8601)   Player signup date
assets             obj             Same structure as Match.assets
patchVersion       str             Version of the game
=================  ==============  ================================

**Participants.stats**

=================  ======================  
Variable    	   Type            
=================  ======================
kills              int
deaths             int
score              int
damageDone         int
damageReceived     int
healingDone        int
healingReceived    int
disablesDone       int
disablesReceived   int
energyGained       int
energyUsed         int
timeAlive          int
abilityUses        int
=================  ======================

.. toctree::
  :maxdepth: 2
