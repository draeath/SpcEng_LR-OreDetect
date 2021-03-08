Visit my workshop page:
http://steamcommunity.com/id/KK4DUY/myworkshopfiles/?appid=244850

UPDATED 2021-03-07: Deprecated 8x detector in favor of a 6x detector. Rewrite files based on current "stock" files. Implemented progression and block groups.

Longer range Ore Detectors for both Large and Small grids are added, at 2x, 4x and 6x powers. The 8x detector still exists so it won't break existing saves/blueprints, but I strongly recommend against it's use.

The only changed items are the range and build component counts, all artwork etc is unchanged.

Ore detectors have stupidly short range. This is annoying. This mod adds some higher power alternatives. Costs are "linear" in that, for 2x the detection range, 2x the detector components are required. Power consumption can't be modded (at least not without code mods) - at least from what I found [url=https://github.com/KeenSoftwareHouse/SpaceEngineers/blob/master/Sources/Sandbox.Game/Definitions/MyOreDetectorDefinition.cs]in the source.[/url]

Code is on [url=https://github.com/draeath/SpcEng_LR-OreDetect]github.[/url] While I haven't tagged a license, you're free to do whatever you like with this. You don't need to ask, you don't need to tell me.

CAUTION: CPU load goes up by the cube of the multiplier. The in-terminal maximum range has no effect on this. The 8x detector causes 512 times more "ore detector queries" than the 1x detector, because every voxel in the maximum allowable range is checked. The in-game terminal range setting is consulted after this scan. Planets make this even more obvious.

If you run into performance problems, turn the block off (or shut the grid down) and wait. It can take a long time for the backlog to clear, so watch your sim speed. Alternatively, save and exit to the menu (this clears the detector queries queue). Since the block is unpowered when you come back, it shouldn't scan again. I recommend removing the detector and replacing it with a smaller multiplier in this case.

The more space CPU cycles you have the further you can push things before it becomes a problem. The trouble is it isn't a linear change like, say, increasing shadow details. You're fine until you cross a threshold (where the detector query processing can't keep up with the incoming queries) and which point it tanks hard.

I don't believe there's anything I can do about this, but you're welcome to have a look. I believe [url=https://github.com/KeenSoftwareHouse/SpaceEngineers/blob/a109106fc0ded66bdd5da70e099646203c56550f/Sources/Sandbox.Game/Game/Entities/Blocks/MyOreDetectorComponent.cs#L148-L171]this is the location of interest.
