# Mefy's Extended-Gametypes

Server-Side Extended-Gametypes MOD Version 1.1.4 For Medal of Honor (11-15-04)
by Mark Follett (Mefy)
mef123@geocities.com
www.planetmedalofhonor.com/mefy

## Description

This mod allows you to host seven new gametypes for the stock Medal of Honor
maps: Capture-The-Flag, Freeze-Tag, Freeze-Tag-Objective, Freeze-Tag-CTF,
Freeze-Tag-TOW, Demolition, and Freeze-Tag-Demolition. A brief description
of each gametype:

- Capture-The-Flag* (for all Allied Assault and Spearhead maps)
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

- Freeze-Tag-CTF* (for all Allied Assault and Spearhead maps)
    This is a Capture-The-Flag game with Freeze-Tag type respawning.
    Each team must capture the flag the most times to win the round.
    While both flags are at their own bases, Freeze Tag respawning will
    be active. Once a flag is removed from its base by the opposing
    team, then full respawning will be enabled until it is returned
    back. If a team is killed while in Freeze-Tag respawning mode, then
    the other team will have several free seconds to advance before the
    killed team will respawn.

- Freeze-Tag-TOW* (for all Spearhead and Breakthrough TOW maps)
    This is a Tug-of-War game with Freeze-Tag type respawning. Each
    team must complete its objectives to win the match like a regular
    Tug-of-War game. When an objective is captured, both teams will be
    automatically melted. If a team is killed, then the other team
    will have several free seconds to advance towards their objectives
    before the killed team respawns. Once a team's base has been
    destroyed they will lose the game if all their players are killed. 

- Demolition* (for all Allied Assault maps)
    This is similar to an objective game except both teams have a base
    to defend. The team that finds and destroys the opponent's base while
    also successfully defending their own base wins the round.

- Freeze-Tag-Demolition* (for all Allied Assault maps)
    This is Demolition mode with Freeze-Tag-Respawning. Kill the enemy
    team or destroy their base to win the round.

The rules of each gametype can be customized by setting cvars- see below for
instructions. The mod is also designed to allow modders to easily set up the
gametypes for custom maps.

This mod is a server-side mod, meaning clients do not have to download anything
to play it on your server!

## Installation

There are currently 2 versions available for download. One is for Allied
Assault, and the other is for Spearhead and Breakthrough. Make sure you have
the correct version:

user-mefy-extgametypes-1.1.4-AA.pk3 (for Allied Assault)
user-mefy-extgametypes-1.1.4-SH.pk3 (for Spearhead and Breakthrough)

For Allied Assault, place the pk3 file in your MOHAA/main directory.
For Spearhead, place the pk3 in your MOHAA/mainta directory.
For Breakthrough, place the pk3 in your MOHAA/maintt directory.


## Hosting a Game

If the map is one of the stock dm maps (mohdm#) or Spearhead tow maps, then run
that map in Round-Based-Match mode in order to enable the new gametypes. If the
map is one of the stock objective maps (obj_team#), then run the map in
Objective mode. Running a stock dm map in Free-For-All or Team-Match modes will
make the map function as normal. For Freeze-Tag-TOW, run the map in
Tug-of-War mode.

The default gametype that will be played is Freeze-Tag for the dm maps,
Freeze-Tag-Objective for the obj maps, and Freeze-Tag-TOW for the tow maps. If
you want to activate the other gametypes for a map, you must set the cvar
"g_extgametype" to the gametype that you want to play:

  set g_extgametype ctf   // Capture-The-Flag
  set g_extgametype ft    // Freeze-Tag
  set g_extgametype ftobj // Freeze-Tag-Objective
  set g_extgametype ftctf // Freeze-Tag-CTF
  set g_extgametype fttow // Freeze-Tag-TOW
  set g_extgametype dem   // Demolition
  set g_extgametype ftdem // Freeze-Tag-Demolition

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
  ftctf.cfg          - Freeze-Tag-CTF config
  fttow.cfg          - Freeze-Tag-TOW config
  dem.cfg            - Demolition config
  ftdem.cfg          - Freeze-Tag-Demolition config
  mixed-types-aa.cfg - Mixed Gametypes config for Allied Assault
  mixed-types-sh.cfg - Mixed Gametypes config for Spearhead and Breakthrough
                       only

## Special Notes

For Freeze-Tag-TOW, this mod will automatically turn off the built-in respawning
delay feature of Spearhead and Breakthrough (sv_team_spawn_interval will be set
to 0), since this interferes with Freeze-Tag respawning. Do not turn it back on
while in the middle of a Freeze-Tag-TOW round or players may be able to hold up
the round if they don't spawn into the game. If you are hosting a mixed gametype
rotation where you want respawn delay on other maps in the rotation, use a VSTR
rotation where you set "sv_team_spawn_interval" back to the desired value for
the specific map.

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

## Global CVARS

- "g_mef_disable" Default: 0
    Set this to 1 in order to disable the Extended Gametypes mod completely.

- "g_mef_team_spawn_interval" Default: 0
    This controls respawning delay for a Capture-The-Flag or Demolition
    game and works similar to the Spearhead and Breakthrough wave respawning
    feature. Set this to the number of seconds a player must wait after they
    are killed before they can respawn again. Set this to 0 to disable wave
    respawning.

- "g_mef_observe" Default: "bodies"
    This setting controls how players are allowed to spectate the game while
    they are dead. The format is a list of options separated by spaces:
      "freefloat" -- Allows players to freefloat in the map while they are
                     dead.
      "bodies"    -- Allows players to spectate their own team's frozen
                     bodies while they are dead.
      "builtin"   -- Enables the "built-in" spectating mode. In this mode
                     you will be able to see dead player names as red on the
                     scoreboard and gun turrets will be available in the map.
                     However, you will no longer be able to free-float while
                     spectating or be able to spectate from frozen bodies.
      "none"      -- Set the cvar to "none" to disable both freefloating and
                     spectating of frozen bodies.

- "g_cinematics_off" Default: 0
    Set this cvar to 1 in order to disable the cinematics at the end of a
    Tug-of-War or Freeze-Tag-TOW game.


## Freeze-Tag and Freeze-Tag-Objective CVARS

Use the "g_ft_<setting>" cvars to control the settings for a Freeze-Tag
game. Use the "g_ftobj_<setting>" cvars to control the settings for a
Freeze-Tag-Objective game.

- "g_ft_suddendeath" and "g_ftobj_suddendeath" Default: 1
    Set this to the number of minutes you want for the sudden death round.
    Once sudden death begins, players will no longer be able to respawn.
    In a Freeze-Tag game, if players are still alive after the sudden death
    round completes, the team with more players alive will win the round.
    The sudden death time is included in the round time. For example, if
    roundlimit is set to 10 and sudden death is set to 2, then there will
    be 8 minutes of normal Freeze-Tag, then 2 minutes of sudden death. Set
    this to 0 to disable sudden death.

## Generic CVARS for all Freeze-Tag gametypes

These cvars apply to all gametypes with Freeze-Tag respawning: Freeze-Tag,
Freeze-Tag-Objective, Freeze-Tag-CTF, and Freeze-Tag-TOW. Use the
"g_ft_<setting>" cvars to control the settings for a Freeze-Tag game. Use
the "g_ftobj_<setting>" cvars to control the settings for a
Freeze-Tag-Objective game. For Freeze-Tag-CTF, use the "g_ftctf_<setting>"
cvars. For Freeze-Tag-TOW, use the "g_fttow_<setting>" cvars.

- "g_ft_melttime", "g_ftobj_melttime", "g_ftctf_melttime", and
  "g_fttow_melttime" Default: 20

    This cvar controls the amount of time it takes to melt a player (in
    tenths of a second). This is how much time it would take to melt
    if a player was standing right next to a frozen body. If you are
    using the melting laser to melt a body, then the time will increase
    with the distance you are from the body.


- "g_ft_meltradius", "g_ftobj_meltradius", "g_ftctf_meltradius", and
  "g_fttow_meltradius" Default: 100

    This controls how close you must be standing to a frozen body in order
    to melt it (in map units). 


- "g_ft_meltgun", "g_ftobj_meltgun", "g_ftctf_meltgun", and
  "g_fttow_meltgun" Default: 1

    Set this to 0 to disable the melting laser. Players would then have to
    stand next to a frozen body to melt it.


- "g_ft_ftannounce", "g_ftobj_ftannounce", "g_ftctf_ftannounce", and
  "g_fttow_ftannounce" Default: "hudmessages frozen melted bodycodes"

    This setting controls the announcing of the frozen body locations for
    given events. The format is the list of events in which to announce the
    location. The possible events are:
      "hudmessages" -- Announces when a player is frozen or melted.
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

## Capture-The-Flag and Freeze-Tag-CTF CVARS

Use the "g_ctf_<setting>" cvars to control the settings for a Capture-The-Flag
game. Use the "g_ftctf_<setting>" cvars to control the settings for a
Freeze-Tag-CTF game.

- "g_ctf_respawn" Default: 1
    Set this cvar to 0 in order to enable a non-respawning Capture-The-Flag
    game. While both flags are at their home bases, respawning will be
    disabled. Once a flag is captured from it's home base, then respawning
    will be enabled in order to allow that flag's team to re-capture it
    before the enemy team runs it back to score. If a team is killed while
    in non-respawning mode, the other team will have several free seconds
    in order to advance before the killed team will respawn. This cvar has
    no effect on a Freeze-Tag-CTF game.

- "g_ctf_pointlimit" and "g_ftctf_pointlimit" Default: 4
    This sets the number of points a team must score in order to win a
    round. If time runs out before the point limit is reached, then the
    team with the most points will be the winner. Setting this to 0 will
    allow the round to continue until time runs out, then determine a
    winner. Use the standard 'roundlimit' cvar to control the length of
    the round. The default round time is 12 minutes.

- "g_ctf_suddendeath" and "g_ftctf_suddendeath" Default: 5
    If time runs out and the score is tied, a sudden death round will
    begin. The next team to score will win the round. Set this option to
    the number of minutes the sudden death round should last. If the sudden
    death round ends with the score still tied, then a 'final' sudden death
    round will occur (see below). Setting this to 0 will start a final
    sudden death round immediately.

- "g_ctf_fsuddendeath" and "g_ftctf_fsuddendeath" Default: 3
    If time runs out in sudden death, then a final sudden death round will
    begin. This is the same as sudden death except that respawning will be
    disabled. The next team to score or kill all of the enemy team will win
    the round. Set this option to the number of minutes the final sudden
    death round should last. If the final sudden death round ends with the
    score still tied and players still alive, then a draw will occur.
    Setting this to 0 will force a draw immediately.

- "g_ctf_returnboth" and "g_ftctf_returnboth" Default: 0
    Set this to 1 in order to require a team to bring both flags to their
    own base in order to score a point. When set to 0, they only have to
    bring the enemy team's flag to their own base to score.

- "g_ctf_countdown" and "g_ftctf_countdown" Default: 15
    This sets the number of seconds a team must hold the flags at their
    base in order to score a point. Setting this to 0 will cause them to
    instantly score when the flags are brought home.

    Setting this to a large value will give the opposing team a chance to
    re-capture their flag and prevent a score. The scoring team will have to
    guard their base well in order to hold off the opposing team. Set this
    to a small value to make scoring easy.

- "g_ctf_capturepress" and "g_ftctf_capturepress" Default: 20
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

- "g_ctf_returnpress" and "g_ftctf_returnpress" Default: 15
    This sets the duration of the button press for returning a flag to home
    base (in tenths of a second). Setting this to -1 means a button press
    is not required- simply walk up to the spot where the flag should go
    and it will attach to the base immediately.

    Set this to a large value to make it difficult to return a flag to home
    base, and keep the snipers happy.

- "g_ctf_drophold" and "g_ftctf_drophold" Default: -1
    This sets how long a player must hold the 'use' key in order to drop a
    flag (in tenths of a second). Setting this to -1 will disable intentional
    flag dropping.

    Setting this to a value of 20 would enable flag dropping, and require a
    player to hold the use key for 2 seconds in order to drop it. This would
    allow players to intentionally hide a flag from the opposing team, or
    allow a player to hand off their flag to a teammate.

- "g_ctf_friendlyreturn" and "g_ftctf_friendlyreturn" Default: 7
    This determines how much time (in seconds) after a player captures their
    own team's flag that it will return automatically to their own base.
    Setting this to 0 will cause the flag to immediately return home. Setting
    this to -1 means that the flag will not return home.

    Setting this to a large value means that a player needs to stay alive
    for awhile after they pick up their team's flag in order for it to return
    to home base. Disabling flag return by setting to -1 will allow a team
    to hide their own flag by having a teammate carry the flag and hide
    somewhere.

- "g_ctf_groundreturn" and "g_ftctf_groundreturn" Default: 25
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

- "g_ctf_enemyreturn" and "g_ftctf_enemyreturn" Default: -1
    This determines how much time (in seconds) after a flag is captured by
    the enemy team that it will automatically return to its base. Setting this
    to -1 means that the flag will not return home.

- "g_ctf_dropdelay" and "g_ftctf_dropdelay" Default: 20
    This sets the amount of time (in tenths of a second) after a flag is
    dropped that it cannot be picked up by any player. The flag will be
    semi-transparent while it is disabled.

    Set this to a large value to lengthen the amount of time players will
    fight over a flag once its dropped. Setting to 0 is not recommended
    and may make certain functions not work.

- "g_ctf_announce" and "g_ftctf_announce" Default: "dropped atbase"
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

- "g_ctf_announcefreq" and "g_ftctf_announcefreq" Default: 8
    If announcing the flag position when "captured" is enabled, this
    setting controls the frequency that the flag position is updated.
    Set to the number of seconds between updates of the flag position.
    If set to 0, then only the position at the spot of capture will be
    announced.

    Setting this to a small value will make it impossible for the flag
    carrier to hide or stay alive. Set this to a large value to give
    them a chance but not allow them to completely hide.

## Demolition and Freeze-Tag-Demolition CVARS

Use the "g_dem_<setting>" cvars to control the settings for a Demolition
game. Use the "g_ftdem_<setting>" cvars to control the settings for a
Freeze-Tag-Demolition game.

- "g_dem_respawn" Default: 0 (1 for Stalingrad)
    Set this cvar to 1 in order to enable a full respawning Demolition
    game. This cvar has no effect on a Freeze-Tag-Demolition game.

- "g_dem_settime" and "g_ftdem_settime" Default: 50
    Set the amount of time (in tenths of a second) it takes to plant a bomb.

- "g_dem_defusetime" and "g_ftdem_defusetime" Default: 35
    Set the amount of time (in tenths of a second) it takes to defuse a bomb.

- "g_dem_ticktime" and "g_ftdem_ticktime" Default: 45 (60 for Stalingrad)
    Set the amount of time (in seconds) it takes for a bomb to explode.

- "g_dem_activatedelay" and "g_ftdem_activatedelay" Default: 20
    Set the amount of time (in seconds) before the bombs become activated at
    the start of the round.

- "g_dem_attacker" and "g_ftdem_attacker" Default: "both"
    This determines which team will be the attacking team and which team
    will be the defending team. The possible options are:
      "both"   -- enables a standard double-objective game where both teams
                  must try to blow up the other team's base
      "allies" -- the allies must blow up the axis team's base
      "axis"   -- the axis must blow up the allied base
      "swap"   -- swaps between the axis team and allied team attacking each
                  round

- "g_dem_suddendeath" and "g_ftdem_suddendeath" Default: 1
    Set this to the number of minutes you want for the sudden death round.
    Once sudden death begins, players will no longer be able to respawn.
    If players are still alive after the sudden death round completes,
    the team with more players alive will win the round. Set this to 0 to
    disable sudden death.


## Map-Specific Customization

The game can be further customized by having map-specific rules. In order
to do this, set a cvar named "g_<gametype>_<mapname>_settings" to a list of
settings to be used for the map. For example:

   set g_ctf_mohdm2_settings "returnboth: 1 drophold: 20"

will adjust the Capture-The-Flag rules for Destroyed Village to require players
to return both flags to their base and enable intentional flag dropping.

Another example:

  set g_ft_mohdm1_settings "meltgun: 0 melttime: 30 ftannounce: none"

will adjust the Freeze-Tag settings for Southern France to disable the melting
laser, set the melting time to 3 seconds, and disable all announcing of body
locations.

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
  /global/libmef/dem.scr
  /global/libmef/ft.scr
  /global/libmef/hud.scr
  /global/libmef/mapdesc.scr
  /global/libmef/respawn.scr
  /global/libmef/spawn.scr
  /global/libmef/tow.scr
  /global/libmef/util.scr

You will then need to modify your map script to initialize the new gametypes.
Use one of the stock map script files included in this map pack as a template
for your own map's script file. Also see the mod forums for a tutorial on how
to set up a map script for the new gametypes.

## Other useful cvars

g_ctf_version -- is set to which version of CTF or FTCTF you are running
g_ft_version  -- is set to which version of FT, FTOBJ, and FTTOW you are running
g_dem_version -- is set to which version of DEM or FTDEM you are running
g_ctf_currentsettings   -- lists the current settings for CTF
g_ft_currentsettings    -- lists the current settings for FT
g_ftobj_currentsettings -- lists the current settings for FTOBJ
g_ftctf_currentsettings -- lists the current settings for FTCTF
g_fttow_currentsettings -- lists the current settings for FTTOW
g_dem_currentsettings   -- lists the current settings for DEM
g_ftdem_currentsettings -- lists the current settings for FTDEM
g_mef_devmode -- Set this to 1 to enable the mod developer mode. This will
                 start the round immediately so you can see where the base
                 locations are for CTF or DEM. Useful if you want to tweak
                 settings or change base locations by yourself.

## Changelog

### Extended-Gametypes 1.1.4 (11/15/04):
- Capture-The-Flag: Fixed the bug where vehicle bases would vanish.
- All gametypes: Fixed bug where you could set bombs and press buttons behind walls.
- Demolition: Set up this gametype for all Allied Assault stock maps.
- Capture-The-Flag: Added more base positions for all Allied Assault stock maps.
- Demolition: The game now announces when a team's base is destroyed.
- Freeze-Tag: Added new option to g_ft_ftannounce called "hudmessages". Not including this will disable the "Allied/Axis player frozen/melted" messages.
- Round-Based-Match: Added fix so players on opposite teams no longer spawn next to each other on mohdm1, mohdm4, mohdm6, and mohdm7 at the beginning of a round.
- Misc cvar changes:
    - Removed the g_ctf_alliedbase, g_ftctf_alliedbase, g_ctf_axisbase, and g_ftctf_axisbase cvars.

### Extended-Gametypes 1.1.3 (10/16/04):
- Capture-The-Flag: Fixed the no-bomb-ticking-sound bug.
- Demolition: The game is non-respawning as default now, except for Stalingrad which has full respawning.
- Demolition: Default tick time is 45 seconds, except for Stalingrad which remains at 60 seconds.
- Demolition: Set up this gametype for mohdm2 and mohdm3.
- Capture-The-Flag: Added more base positions for mohdm2 and mohdm3.

### Extended-Gametypes 1.1.2 (09/28/04):
- Renamed Voodoo-Dolls gametype to Demolition. Set g_extgametype to 'dem' to run it.
- Added Freeze-Tag-Demolition gametype for Stalingrad. Set g_extgametype to 'ftdem' to run it.
- Added non-respawning Demolition mode. Set 'g_dem_respawn' to 0 to enable it.
- Capture-The-Flag: Added g_ctf_enemyreturn option to make a flag return to its home base if held by the enemy for too long.
- Demolition: Added non-respawning sudden death to the end of the round. The team with less players alive at the end will be nuked.
- Demolition: After both bombs blow up, sudden death will commence.
- Demolition: Base positions and the player count now appear on the HUD.
- Demolition: Added "swap" option for g_dem_attacker: this will make it swap between axis and allies attacking each round.
- Demolition: Fixed bug that would reset the team scores if a draw occured.
- Misc cvar changes:
    - Removed the g_vd_... suite of cvars and replaced them with g_dem_... for the Demolition gametype.
    - Added g_dem_respawn for controlling respawning in Demolition.
    - Added g_dem_suddendeath for controlling sudden death in Demolition.
    - Added the g_ftdem_... suite of cvars for the Freeze-Tag-Demolition gametype.
    - Added g_ctf_enemyreturn.

### Extended-Gametypes 1.1.1 (08/15/04):
- Added Freeze-Tag-TOW gametype for all Spearhead and Breakthrough tow maps. This is now the default gametype for tow maps.
- Fixed bug in 'built-in' spectating mode where spectators at the end of the round would have to re-select their weapons at the start of the next round.
- In Spearhead and Breakthrough, frozen bodies and flags no longer fall through catwalks. (but they still do in Allied Assault, sorry)
- Wave respawning for the new gametypes is now activated with the "g_mef_team_spawn_interval" cvar instead of "sv_team_spawn_interval".
- When a bomb is set or defused, the team who did it will be announced.
- All gametypes: Extended gametypes now start when g_gametype is 5.
- Misc cvar changes:
    - Added the g_fttow_... suite of cvars for the Freeze-Tag-TOW gametype.
    - Added "g_cinematics_off" for the Spearhead TOW maps. Set this to 1 in order to disable cinematics.

### Extended-Gametypes 1.1.0 (07/22/04):
- Added Freeze-Tag-CTF gametype. Set g_extgametype to "ftctf" to start it.
- Added non-respawning CTF mode, similar to Freeze-Tag-CTF except with no respawning during the 'capture' phase of the game. Set g_ctf_respawn to 0 to enable this mode.
- Added wave respawning for CTF. Set sv_team_spawn_interval to the number of seconds a player has to wait to respawn after being killed.
- Added new 'builtin' spectating mode. In this mode, dead players will be seen as red on the scoreboard, and machine gun turrets will be available in the map. Freefloating and spectating from frozen bodies is not possible in this mode. Set g_mef_observe to "builtin" to enable this new spectating mode.
- Spearhead version now includes CTF on all maps (base selection by Kaotik).
- Capture-The-Flag: Flags now stay attached to a player while they climb ladders.
- Capture-The-Flag: Created new CTF base setup method in map scripts which is much simpler and cleaner. Map scripts using the old base setup method will still work.
- Voodoo-Dolls: Added ability to play a game with one team attacking and the other team defending. Set g_vd_attacker to "allies", "axis", or "both".
- Modern-Warfare: Fixed Freeze-Tag-Objective for obj/mw_nasiriyanight. Respawning now works properly.
- All gametypes: Extended gametypes now start on dm maps when g_gametype is 4.
- All gametypes: The player count display now shows the current respawning mode.
- Misc cvar changes:
    - Removed g_ctf_disable, g_ft_disable, g_ftobj_disable, g_vd_disable.
    - Added g_mef_disable for disabling the mod. Use this instead of the old cvars for each gametype.
    - Renamed g_ft_announce and g_ftobj_announce to g_ft_ftannounce and g_ftobj_ftannounce.
    - Removed g_ft_allowjoin and g_ftobj_allowjoin. Players will now always be able to join a game in the middle of a round.
    - Removed g_ft_observe. Use the new g_mef_observe cvar instead.
    - Added g_mef_observe for handling spectator mode options. Now recognizes the 'builtin' option for enabling the new spectating mode.
    - Added the g_ftctf_... suite of cvars for the Freeze-Tag-CTF gametype.

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