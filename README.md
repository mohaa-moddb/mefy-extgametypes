# Mefy's Extended-Gametypes

Server-Side Extended-Gametypes MOD Version 1.0.0 For Medal of Honor (06-02-04)
by Mark Follett (Mefy)
mef123@geocities.com
www.planetmedalofhonor.com/mefy

## Description

This mod allows you to host four new gametypes for the stock Medal of Honor
maps: Capture-The-Flag, Freeze-Tag, Freeze-Tag-Objective, and Voodoo-Dolls.
A brief description of each gametype:

- Capture-The-Flag* (for all Allied Assault maps)
    To score a point your team must capture and bring the enemy team's
    flag to your own team's base and hold it there for 15 seconds. The
    first team to score 4 points, or the team with the most points at
    the end of the round, wins the round. The default round time is 12
    minutes.

- Freeze-Tag* (for all Allied Assault and Spearhead maps)
    Each team must freeze all the players from the opposing team to win
    the round. To freeze a player, simply kill them. Once frozen, a
    player can't respawn until one of their teammates melts their
    frozen body by either standing next to it for a couple seconds, or
    firing their 'melting laser' at it. This gametype was inspired by
    Darrell Bircsak's Quake 3 Freeze-Tag MOD.
    (http://www.planetquake.com/freeze/)

- Freeze-Tag-Objective* (for all Allied Assault Objective maps)
    This is a combination of Freeze-Tag and a standard Objective-Match
    game. The attacking team must either freeze the entire defending
    team or complete their objectives. The defending team must either
    freeze the entire attacking team or successfully defend their
    objectives for the entire duration of the round.

- Voodoo-Dolls* (for Stalingrad only)
    Each team has a doll with a bomb attached to its chest that they
    must defend from the other team. The team that finds and destroys
    the opponent's voodoo doll while also successfully defending their
    own voodoo doll wins the round. If time runs out, the team with
    most kills wins the round. The dolls appear in random locations each
    round.

The rules of each gametype can be customized by setting cvars- see below for
instructions. The mod is also designed to allow modders to easily set up the
gametypes for custom maps.

This mod is a server-side mod, meaning clients do not have to download anything
to play it on your server!


## Installation

There are currently 2 versions available for download. One is for Allied
Assault, and the other is for Spearhead and Breakthrough. Make sure you have
the correct version:

user-mefy-extgametypes-1.0.0-AA.pk3 (for Allied Assault)
user-mefy-extgametypes-1.0.0-SH.pk3 (for Spearhead and Breakthrough)

For Allied Assault, place the pk3 file in your MOHAA/main directory.
For Spearhead, place the pk3 in your MOHAA/mainta directory.
For Breakthrough, place the pk3 in your MOHAA/maintt directory.


## Hosting a Game

If the map is one of the stock dm maps (mohdm#) or Spearhead tow maps, then run
that map in Round-Based-Match mode in order to enable the new gametypes. If the
map is one of the stock objective maps (obj_team#), then run the map in
Objective mode. Running a stock dm map in Free-For-All or Team-Match modes will
make the map function as normal.

The default gametype that will be played is Freeze-Tag for the dm maps, and
Freeze-Tag-Objective for the obj maps. If you want to activate the other
gametypes for a map, you must set the cvar "g_extgametype" to the gametype that
you want to play:

  set g_extgametype ctf   // Capture-The-Flag
  set g_extgametype ft    // Freeze-Tag
  set g_extgametype ftobj // Freeze-Tag-Objective
  set g_extgametype vd    // Voodoo-Dolls

If you want to play Round-Based-Match instead of one of the new gametypes:

  set g_extgametype rbm   // Round-Based-Match

Or if you want to play Objective-Match:

  set g_extgametype obj   // Objective-Match

You can also set "g_extgametype" to the other standard gametypes:

  set g_extgametype ffa   // Free-For-All
  set g_extgametype tdm   // Team-Match
  set g_extgametype tow   // Tug-of-War
  set g_extgametype lib   // Liberation

When "g_extgametype" is set, it will override whatever you set "g_gametype" as.
For example, if "g_extgametype" is set to "ctf" and "g_gametype" is "1", it will
run Capture-The-Flag, not Free-For-All. You can unset "g_extgametype" by setting
it to "".

You can also set a map-specific cvar for setting the gametype for a particular
map. For example,

  set g_extgametype_mohdm1 ctf

will activate Capture-The-Flag for Southern France. This is used in a mixed
gametype rotation.

See the included sample server config files for examples on how to set up a
server for hosting each of the gametypes, and also for setting up a map rotation
with multiple gametypes:

  ctf.cfg            - Capture-The-Flag config
  ft.cfg             - Freeze-Tag config
  ftobj.cfg          - Freeze-Tag-Objective config
  vd.cfg             - Voodoo-Dolls config
  mixed-types-aa.cfg - Mixed Gametypes config for Allied Assault
  mixed-types-sh.cfg - Mixed Gametypes config for Spearhead and Breakthrough
                       only


## Troubleshooting

If you are having trouble getting the mod to run, please read the Hosting FAQ
(www.planetmedalofhonor.com/mefy/hosting-faq.html) which addresses the common
problems. If you are running other mods (like map fix mods), they may be
conflicting with this mod. If you're still having trouble try posting a question
in the mod forums which you can find at www.planetmedalofhonor.com/mefy.

## Uninstall

Just remove the user-mefy-extgametypes... pk3 file from your server's directory.

## General Customization

The game can be customized by adjusting the following cvars. After setting
a cvar, you must restart the game for the changes to take effect. Below
is a list of cvars that can be set for each gametype. NOTE that you do not
need to set any of these cvars to get the game to run-- they are only
meant for changing the rules from the default settings.

## Freeze-Tag and Freeze-Tag-Objective CVARS

Use the "g_ft_<setting>" cvars to control the settings for a Freeze-Tag
game. Use the "g_ftobj_<setting>" cvars to control the settings for a
Freeze-Tag-Objective game.

- "g_ft_disable" and "g_ftobj_disable" Default: 0
    Set this to 1 in order to disable Freeze-Tag or Freeze-Tag-Objective
    mode. If the map running is a dm map, then it will run in
    Round-Based-Match mode. If the map running is an obj map,  then it will
    begin a standard objective game.

- "g_ft_suddendeath" and "g_ftobj_suddendeath" Default: 1
    Set this to the number of minutes you want for the sudden death round.
    Once sudden death begins, players will no longer be able to respawn.
    In a Freeze-Tag game, if players are still alive after the sudden death
    round completes, the team with more players alive will win the round.
    The sudden death time is included in the round time. For example, if
    roundlimit is set to 10 and sudden death is set to 2, then there will
    be 8 minutes of normal Freeze-Tag, then 2 minutes of sudden death. Set
    this to 0 to disable sudden death.

- "g_ft_melttime" and "g_ftobj_melttime" Default: 20
    This cvar controls the amount of time it takes to melt a player (in
    tenths of a second). This is how much time it would take to melt
    if a player was standing right next to a frozen body. If you are
    using the melting laser to melt a body, then the time will increase
    with the distance you are from the body.

- "g_ft_meltradius" and "g_ftobj_meltradius" Default: 100
    This controls how close you must be standing to a frozen body in order
    to melt it (in map units). 

- "g_ft_meltgun" and "g_ftobj_meltgun" Default: 1
    Set this to 0 to disable the melting laser. Players would then have to
    stand next to a frozen body to melt it.

- "g_ft_allowjoin" and "g_ftobj_allowjoin" Default: 1
    When set to 1, players will be able to join the game in the middle of the
    round. When they join they will start out as a frozen body. If set to 0,
    players will only be able to join the game if they enter within the
    join time set by the server (controlled by the cvar 'g_allowjointime'),
    similar to a Round-Based-Match or Objective-Match game. Note that this
    mod will give players a minimum of 30 seconds to join the game after a
    new map loads regardless of what 'g_allowjointime' is set to.

- "g_ft_announce" and "g_ftobj_announce" Default: "frozen melted bodycodes"
    This setting controls the announcing of the frozen body locations for
    given events. The format is the list of events in which to announce the
    location. The possible events are:
      "frozen"    -- Announce the body's location when a player is frozen.
      "melted"    -- Announce the body's location when a player is melted.
      "bodycodes" -- Display all of the frozen body locations in abbreviated
                     format on the HUD in the lower left corner of the screen.
      "none"      -- Set the cvar to "none" to disable all location
                     announcements.
    Note that body locations will only be announced for maps that have a map
    description set up (currently all Allied Assault dm maps, obj_team1, and
    obj_team4). If a map doesn't have a description available then you will
    only get generic announcements without locations.

- "g_ft_observe" and "g_ftobj_observe" Default: "bodies"
    This setting controls how players are allowed to spectate the game while
    they are frozen. The format is a list of options separated by spaces:
      "freefloat" -- Allows players to freefloat in the map while they are
                     frozen.
      "bodies"    -- Allows players to spectate their own team's frozen
                     bodies while they are frozen.
      "none"      -- Set the cvar to "none" to disable both freefloating and
                     spectating of frozen bodies.

## Capture-The-Flag CVARS

- "g_ctf_disable" Default: 0
    Set this to 1 in order to disable Capture-The-Flag mode. If the map
    running is a dm map, then it will run in Round-Based-Match mode. If
    the map running is an obj map,  then it will begin a standard objective
    game.

- "g_ctf_pointlimit" Default: 4
    This sets the number of points a team must score in order to win a
    round. If time runs out before the point limit is reached, then the
    team with the most points will be the winner. Setting this to 0 will
    allow the round to continue until time runs out, then determine a
    winner. Use the standard 'roundlimit' cvar to control the length of
    the round. The default round time is 12 minutes.

- "g_ctf_suddendeath" Default: 5
    If time runs out and the score is tied, a sudden death round will
    begin. The next team to score will win the round. Set this option to
    the number of minutes the sudden death round should last. If the sudden
    death round ends with the score still tied, then a 'final' sudden death
    round will occur (see below). Setting this to 0 will start a final
    sudden death round immediately.

- "g_ctf_fsuddendeath" Default: 3
    If time runs out in sudden death, then a final sudden death round will
    begin. This is the same as sudden death except that respawning will be
    disabled. The next team to score or kill all of the enemy team will win
    the round. Set this option to the number of minutes the final sudden
    death round should last. If the final sudden death round ends with the
    score still tied and players still alive, then a draw will occur.
    Setting this to 0 will force a draw immediately.

- "g_ctf_alliedbase" Default: map-specific
    Set this in order to change the location of the allied base. The format
    is as follows: "<x-coord> <y-coord> <z-coord> <angle>". For example, a
    value of "297 -2115 -22.62 180" will place the allied base at
    ( 297 -2115 -22.62 ) and it will be facing at an angle of 180.
    You will most likely want to set this for a specific map. See the
    section on "Map-Specific Customization" for instructions on how to
    do this.

- "g_ctf_axisbase" Default: map-specific
    Set this in order to change the location of the axis base. The format
    is the same as 'alliedbase'.

- "g_ctf_returnboth" Default: 0
    Set this to 1 in order to require a team to bring both flags to their
    own base in order to score a point. When set to 0, they only have to
    bring the enemy team's flag to their own base to score.

- "g_ctf_countdown" Default: 15
    This sets the number of seconds a team must hold the flags at their
    base in order to score a point. Setting this to 0 will cause them to
    instantly score when the flags are brought home.

    Setting this to a large value will give the opposing team a chance to
    re-capture their flag and prevent a score. The scoring team will have to
    guard their base well in order to hold off the opposing team. Set this
    to a small value to make scoring easy.

- "g_ctf_capturepress" Default: 20
    This sets the duration of the button press for capturing a flag from
    the enemy's base (in tenths of a second). Setting this to -1 means that
    a button press is not required- you can walk up to the flag and capture
    it immediately.

    Set this to a large value to make it difficult to capture a flag from
    an enemy team's base. A player will have to stand in front of the base
    while pressing the button and be vulnerable to attack. This allows
    snipers to guard a base. Setting to zero is not recommended-- it will
    be too easy for the opposing team to re-capture their flag and prevent
    a score.

- "g_ctf_returnpress" Default: 15
    This sets the duration of the button press for returning a flag to home
    base (in tenths of a second). Setting this to -1 means a button press
    is not required- simply walk up to the spot where the flag should go
    and it will attach to the base immediately.

    Set this to a large value to make it difficult to return a flag to home
    base, and keep the snipers happy.

- "g_ctf_drophold" Default: -1
    This sets how long a player must hold the 'use' key in order to drop a
    flag (in tenths of a second). Setting this to -1 will disable intentional
    flag dropping.

    Setting this to a value of 20 would enable flag dropping, and require a
    player to hold the use key for 2 seconds in order to drop it. This would
    allow players to intentionally hide a flag from the opposing team, or
    allow a player to hand off their flag to a teammate.

- "g_ctf_friendlyreturn" Default: 7
    This determines how much time (in seconds) after a player captures their
    own team's flag that it will return automatically to their own base.
    Setting this to 0 will cause the flag to immediately return home. Setting
    this to -1 means that the flag will not return home.

    Setting this to a large value means that a player needs to stay alive
    for awhile after they pick up their team's flag in order for it to return
    to home base. Disabling flag return by setting to -1 will allow a team
    to hide their own flag by having a teammate carry the flag and hide
    somewhere.

- "g_ctf_groundreturn" Default: 25
    This determines how much time (in seconds) after a flag sits on the ground
    that it will automatically return to its base. Setting this to 0 will
    cause the flag to immediately return home. Setting this to -1 means that
    the flag will not return home.

    Setting this to a large value will give a team the chance to recapture a
    flag and continue their progress if their flag carrier drops the flag by
    being killed. Setting this to 0 would mean that the flag carrier must stay
    alive during the entire journey back to home base. Setting to -1 is not
    recommended-- the flag could potentially be lost somewhere for the
    remainder of the round.

- "g_ctf_dropdelay" Default: 20
    This sets the amount of time (in tenths of a second) after a flag is
    dropped that it cannot be picked up by any player. The flag will be
    semi-transparent while it is disabled.

    Set this to a large value to lengthen the amount of time players will
    fight over a flag once its dropped. Setting to 0 is not recommended
    and may make certain functions not work.

- "g_ctf_announce" Default: "dropped atbase"
    This setting controls the announcing of the flag positions for given
    events. The format is the list of events in which to announce the flag
    position. The possible events are:
      "captured" -- Announce the flag position when a player picks up
                    a flag. When not set, the position will be a generic
                    'Axis/Allied Player'
      "dropped"  -- Announce the flag position when the flag is on the
                    ground. When not set, the position will be 'Ground'
      "atbase"   -- Announce the flag position when the flag is at a
                    team's base. When not set, the position will be
                    'Axis/Allied Base'
      "abbr"     -- Include this option to announce the flag positions in
                    abbreviated format.
      "none"     -- Set the cvar to "none" to disable all flag position
                    announcements.
    Note that flag positions will only be announced for maps that have a
    map description set up (currently all Allied Assault dm maps, obj_team1,
    and obj_team4). If a map doesn't have a description available then you
    will only get the generic announcements.

    Setting these options will keep the game moving forward by showing
    players where the flags are.

- "g_ctf_announcefreq" Default: 8
    If announcing the flag position when "captured" is enabled, this
    setting controls the frequency that the flag position is updated.
    Set to the number of seconds between updates of the flag position.
    If set to 0, then only the position at the spot of capture will be
    announced.

    Setting this to a small value will make it impossible for the flag
    carrier to hide or stay alive. Set this to a large value to give
    them a chance but not allow them to completely hide.

## Voodoo-Dolls CVARS

- "g_vd_disable" Default: 0
    Set this to 1 in order to disable Voodoo-Dolls mode. If the map
    running is a dm map, then it will run in Round-Based-Match mode. If
    the map running is an obj map,  then it will begin a standard objective
    game.

- "g_vd_settime" Default: 50
    Set the amount of time (in tenths of a second) it takes to plant a bomb.

- "g_vd_defusetime" Default: 35
    Set the amount of time (in tenths of a second) it takes to defuse a bomb.

- "g_vd_ticktime" Default: 60
    Set the amount of time (in seconds) it takes for a bomb to explode.

- "g_vd_activatedelay" Default: 20
    Set the amount of time (in seconds) before the bombs become activated at
    the start of the round.


## Map-Specific Customization

The game can be further customized by having map-specific rules. In order
to do this, set a cvar named "g_<gametype>_<mapname>_settings" to a list of
settings to be used for the map. For example:

   set g_ctf_mohdm2_settings "returnboth: 1 alliedbase: 297 -2115 -22.62 180 axisbase: -3237 270 24.97 0 drophold: 20"

will adjust the Capture-The-Flag rules for Destroyed Village to place the
bases in new locations, require players to return both flags to their base,
and enable intentional flag dropping.

Another example:

  set g_ft_mohdm1_settings "meltgun: 0 melttime: 30 announce: none observe: none"

will adjust the Freeze-Tag settings for Southern France to disable the melting
laser, set the melting time to 3 seconds, disable all announcing of body locations,
and prevent spectators from freefloating or viewing from frozen bodies.

If a map-specific setting is set, it will override the general setting
cvar. You can review the current settings during any game by reading
the cvar "g_<gametype>_currentsettings", which will give a list of all settings.


## Extended-Gametypes for Custom Maps

Setting up these new gametypes for a custom map is easy. Most of the code
is placed in library files that you simply need to distribute with your
custom map. The library files are as follows:
  /global/libmef/bases.scr
  /global/libmef/bomb.scr
  /global/libmef/ctf.scr
  /global/libmef/ft.scr
  /global/libmef/mapdesc.scr
  /global/libmef/spawn.scr
  /global/libmef/util.scr
  /global/libmef/vd.scr

You will then need to modify your map script to initialize the new gametypes.
Use one of the stock map script files included in this map pack as a template
for your own map's script file. The map script file for mohdm3 (Remagen) is the
simplest one to use as a template-- the axis and allied bases for CTF are in
the same position every round. Check out some of the others for more complex
examples that show you how to place the CTF bases in random locations each
round. Also see the mod forums for a tutorial on how to set up a map script
for the new gametypes.


## Other useful cvars

g_ctf_version -- is set to which version of CTF you are running
g_ft_version  -- is set to which version of FT you are running
g_vd_version  -- is set to which version of VD you are running
g_ctf_currentsettings   -- lists the current settings for CTF
g_ft_currentsettings    -- lists the current settings for FT
g_ftobj_currentsettings -- lists the current settings for FTOBJ
g_vd_currentsettings    -- lists the current settings for VD
g_mef_devmode -- Set this to 1 to enable the mod developer mode. This will
                 start the round immediately so you can see where the base
                 locations are for CTF or VD. Useful if you want to tweak
                 settings or change base locations by yourself.

## Changelog

### Extended-Gametypes 1.0.0 (06/02/04):
- Freeze-Tag: Frozen bodies now change to purple when an enemy player is nearby.
- Added readme file and sample server configs.

### Freeze-Tag 1.1 Alpha #11 (05/12/04):
- Added map description for obj_team1.
- Freeze-Tag: Added object 'broadcasting' code which should reduce lag.
- HUD now clears properly when changing to a standard gametype and restarting.
- Freeze-Tag-Objective: Round end condition now works properly for Allied Assault Demo.
- Voodoo-Dolls: Changed to allow setup of base pairs.

### Freeze-Tag 1.1 Alpha #10 (04/27/04):
- Added map descriptions for mohdm1, mohdm3, mohdm5, and mohdm7.
- Freeze-Tag: Fixed bug in code that's supposed to keep ghosts from being thrown to spec. Players would sometimes not be able to jump the next round.
- Freeze-Tag: Frozen bodies no longer spin. Should reduce lag.
- Freeze-Tag: Tweaked the new HUD animation code to reduce lag.
- Freeze-Tag: Tweaked the laser beam to reduce lag.
- Capture-The-Flag: Added capability to define base descriptions for custom maps without a full blown map description file.
- Voodoo-Dolls: Added a team symbol above the voodoo doll's head.
- Voodoo-Dolls: Changed code to allow easier setup for other maps.

### Freeze-Tag 1.1 Alpha #9 (03/20/04):
- Freeze-Tag: Players can now join the game in the middle of a round. They will start out as frozen. To disable this feature, set g_ft_allowjoin or g_ftobj_allowjoin to 0.
- Freeze-Tag-Objective: Set up this gametype for obj/obj_team3. (Omaha Beach)
- Freeze-Tag: Players who are ghosts will no longer be thrown to spectator mode due to inactivity.
- Freeze-Tag: You can now free-look around a frozen body instead of spinning with it. (no more dizzies!)
- Freeze-Tag: Slight improvement to the HUD. The team icons will pop and the text will temporarily change color when someone is frozen or melted.
- Freeze-Tag: Tweaked laser beam to prevent it from colliding with yourself during certain player animations.

### Freeze-Tag 1.1 Alpha #8 (02/28/04):
- Freeze-Tag: Fixed bug in Spearhead and Breakthrough point awarding code that would screw up the player count and end the round prematurely.

### Freeze-Tag 1.1 Alpha #7 (02/22/04):
- Freeze-Tag: More bugfixes in multi-melt code.

### Freeze-Tag 1.1 Alpha #6 (02/21/04):
- Freeze-Tag: Fixed bug in multi-melt code that prevents a player from being melted.

### Freeze-Tag 1.1 Alpha #5 (02/17/04):
- All gametypes w/bombs: Server no longer crashes (for REAL this time!) if someone is defusing a bomb while it explodes.
- Freeze-Tag-Objective: The last minute of the round is now sudden death (no respawning). Set g_ftobj_suddendeath to change the number of minutes.
- Freeze-Tag: Round time now includes the sudden death round. (Setting roundlimit to 10 and g_ft_suddendeath to 2 will give 8 minutes of freeze tag and 2 minutes of sudden death)
- Freeze-Tag: The game will now announce when sudden death is approaching and when the team with less players will be nuked at the very end of the round.
- Freeze-Tag: Multiple players melting a body will make the melt go faster. On SH and BT versions, the point that is awarded will be divided equally between each melter.
- Freeze-Tag: Unspawned players can't use the melting gun.
- Util: Fixed version detection of Allied Assault Demo.

### Freeze-Tag 1.1 Alpha #4.1 (02/22/04):
- All gametypes w/bombs: Server no longer crashes (for REAL this time!) if someone is defusing a bomb while it explodes.

### Freeze-Tag 1.1 Alpha #4 (02/08/04):
- Added fix so players on opposite teams no longer spawn next to each other on mohdm1, mohdm4, mohdm6, and mohdm7 at the beginning of a round.
- Fixed the bug where unspawned spectators would hold up the game.
- On the first round after a new map loads, players now have a minimum of 30 seconds to join a team, regardless of what g_allowjointime is set to.
- Default round time is now 6 minutes instead of 7.
- Sudden death time is now 1 minute instead of 2.
- Put laser sounds for Spearhead back to Alpha #2 config.
- Freeze-Tag-Objective: Melting gun now doesn't fire after you set a bomb.
- Freeze-Tag-Objective: Fixed the 'mysterious death' bug after a bomb would blow up.
- Freeze-Tag-Objective: Altered the behavior to be similar to standard objective when the planting team is killed and bombs are still set.
- All gametypes w/bombs: Server no longer crashes if someone is defusing a bomb while it explodes.
- Capture-The-Flag: Teams will now spawn on the same side of the map as their bases on mohdm1, mohdm4, and mohdm7 at the beginning of a round.

### Freeze-Tag 1.1 Alpha #3 (01/15/04):
- The mod now contains all gametypes- Freeze-Tag, Capture-The-Flag, and Voodoo-Dolls, selectable with the cvar "g_extgametype".
- Set up Freeze-Tag for the Spearhead maps.
- Added new gametype, Freeze-Tag-Objective, for obj_team1, obj_team2, and obj_team4. This is an objective game with Freeze-Tag respawning.
- Freeze-Tag: Free-floating is now disabled by default.
- Freeze-Tag: Uses new set of laser beam sounds for Spearhead.
- Freeze-Tag: Fixed bug with body beam colors not changing properly.
- Freeze-Tag: Changed spectator viewpoint to make it similar to the built-in spectator mode. Also made the spectator movement smoother.
- Freeze-Tag: HUD now shows the total number of players on each team.
- Freeze-Tag: Players now are awarded a point for melting in Spearhead and Breakthrough.

### Freeze-Tag 1.1 Alpha #2 (01/02/04):
- Major structural changes- most of the gametype code is now in library files.
- Set up the gametype for all of the Allied Assault maps.
- Added the melting laser for melting frozen bodies from long distance.
- Added sudden death round. In this round respawning is disabled. If time runs out with people still alive on both teams, then the team with more players alive will win the round, or it will end in a draw if both teams have the same number of players alive.
- Removed all types of turrets from maps in order to prevent the exploit.
- Reworked the spectating code to fix the 'telefragging' bug.

### Capture-The-Flag 1.2 (11/30/03):
- Fixed bug where the flag would get stuck to a player for the rest of the round if they capture the flag at the same time as they are killed.
- Set the game to run in gametype 4 (objective) for the obj maps. This allows you to cycle through the obj maps easier and should stop players from getting thrown to spec when the round restarts in these maps.
- Added a final sudden death round that follows the standard sudden death round if the score is still tied. During this round respawning is disabled. If this round ends with no winner or players are still alive, then the game will end in a draw. Use the "g_ctf_fsuddendeath" cvar to control the length of the round.
- Added a "g_ctf_version" cvar that returns the version of ctf that is running. Intended for viewing from server browsers like Gamespy and All-Seeing-Eye.
- Added code to hide the center message at the end of the round if it's still up ('Allies/Axis score!')
- Changed Defaults:
    - Roundtime is now 12 minutes instead of 15.
    - Pointlimit is now 4 instead of 5.
    - Capturepress is now 2 seconds instead of 2.5 seconds.
    - Dropdelay is now 2 seconds instead of 3 seconds.
    - Base Locations:
        - mohdm2: moved east bldg ruins spot from the upper level to the ground in front, moved east sector spot away from the spawn point
        - mohdm4: moved the spots to the same as obj_team4: under the bridge and next to the 'chartreux' sign
        - obj_team1: moved the axis bases farther back near their spawn

### Freeze-Tag 1.1 Alpha #1 (11/17/03):
- Observers can't melt bodies.
- Removed free-floating mode to keep people from firing a mg42 or using other stuff.

### Capture-The-Flag 1.1 (11/15/03):
- Major structural changes- most of the gametype code is now in library files.
- Set up the gametype for all Allied Assault stock maps.
- You now have to press a button on the flag base to release a flag.

### Capture-The-Flag 1.0 (10/18/03):
- Initial release, for Stalingrad only

### Freeze-Tag 1.0 (10/05/03):
- Initial release, for Stalingrad only

### Voodoo-Dolls 1.1 (09/08/03):
- New rule: If, after the first bomb blows, the other bomb is still set, then the match continues until that bomb explodes or is defused. If it is defused, then the defusing team will win the round. If it explodes, then the round will end with a draw. The team that blew the first bomb will also have 7 seconds added to their own bomb's time.
- The round will continue when time runs out if any bombs are still set.
- At the start of a round, the bombs will not be settable for 20 seconds.
- When a team's bomb explodes, all players on that team explode with it, no matter where they are on the map.
- Added bomb meters on the player's hud to show how much time is left for each team's bomb.

### Voodoo-Dolls 1.0 (08/16/03):
- Initial release, for Stalingrad only