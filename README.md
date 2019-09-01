# Minecraft: Bedrock Edition Behavior Pack
## Repository Status
![GitHub All Releases](https://img.shields.io/github/downloads/ZtechNetwork/MCBVanillaBehaviorPack/total) ![GitHub release (latest by date)](https://img.shields.io/github/v/release/ZtechNetwork/MCBVanillaBehaviorPack?include_prereleases) ![GitHub last commit](https://img.shields.io/github/last-commit/ZtechNetwork/MCBVanillaBehaviorPack)

## Changelogs
### v1.13.0.9 [Beta]
#### *Changes for Map Makers & Addons:*
- **New Data Driven Items:**
    - Turtle Lightning interactions are now data driven
    - Pufferfish puffed states are now data driven 
    - Brewing Stand potion recipes are now data driven 
- Changed Breathable, RideTick, and Transformation systems to use ViewedEntityContext
- Added precompiled header targeting for ScriptAPI 
- Significantly increased the maximum “spawnRadius” distance
#### *Bug Fixes:*
- Fixed the death override event firing twice when leaving world from the death screen
- Fixed `minecraft:scale` component failing to scale certain Actor models
- Running the "tick_world" component now removes ticking areas correctly and consistently 
- Fixed double damage events being sent when mobs are hurt by non-magic
- Behaviour Pack animations now run correctly when set
- Timer component now works on projectiles
- "minecraft:spell_effects" no longer trigger a second time incorrectly
- Fixed player entity components that were not getting added
- Added stone slab aliases to allow backwards compatibility on Marketplace maps 

### v1.13.0.6 [Beta]
- No changes to Addons and Scripts

### v1.13.0.5 [Beta]
#### *Bug Fixes:*
- Fixed player entity components (eg. minecraft:damage_sensor) that were not getting added
- Fixed dog fetching mechanic on Dogs Marketplace content. Was caused by a ride attacking it's - rider so prevented the melee attack goal from doing that
- Custom player armor now renders correctly in some Marketplace content worlds

### v1.13.0.4 [Beta]
#### *Bug Fixes:*
- Ducks can once again be hit by the player in the MINECON 2018 Pack (not that you would, of course!)
- Fixed the positioning of particles that were only showing correctly when centered on screen
- Adding back-compatibility for old player animation flags
- Experimental UI is registered as trusted pack (MCPE-47818)
- Fixed horse rein positioning and rotation in certain packs
- Fixed an issue with nested behaviour pack definitions not running correctly
- Fixed an issue with minimum compatible versions of certain packs not working correctly 
- Timer component now works on vanilla projectiles
- ‘minecraft:spell_effects’ no longer trigger a second timer 
- Fixed an issue with the ‘must_see_forget_duration’ component not working 
- Fixed an entity collision issue that was affecting some marketplace maps
- Invisible end rods (variant 6) used in various marketplace maps are now invisible again

### v1.13.0.2 [Beta]
#### *Bug Fixes:*
- Blocks no longer stutter while falling when a script uses getBlocks 
- Scripting: Ticking areas now have a property showing whether they are fully loaded or not 
- Custom rideable entities now show the correct action hint when added

### v1.13.0.1 [Beta]
#### *Changes for Map Makers & Addons:*
- **New Data Driven Items:**
    - Added shake animation to data-driven arrow
    - Data driven actor push logic and behaviour 
    - Breaking item particles are now data driven 
    - Implemented data driven environment damage 
    - Data driven sparkler particles 
    - Data driven Guardian/Elder Guardian animation and rendering
        - Fixed unparented geometry on pre 1.8 guardians
        - Elder Guardian Spike animation 
    - Added new feature rules data that implements existing biome decoration through json 
        - Final infrastructure changes required to support fully data driven features. Rules themselves must be provided in a behaviour pack with experimental turned on
    - Converted the Fishing Hook actor to be Data-Driven 
    - Converted the Balloon actor to be Data-Driven 
    - Data Driven Player Rendering
    - Snow Golem trail behaviour is now data driven 
    - Horse models/animations are now data driven 
    - User Story Dragon Breath Particles are now data driven
    - Ores are now data driven (OreFeature)
- Added Scripting Documentation for ActorDamageSource 
- Added additional Scripting information to death events 
- Added block container Scripting component 
- Added 'Projectile Hit' Scripting event 
- Added 'Actor Hurt' Scripting event 
- Added new Actor tags to the Scripting API
- Added Block Destruction Scripting event for Explosions 
- Actor Definition Events can now be triggered from scripts
- Added 'actor_sneak' Scripting event 
- Added 'actor attacked' Scripting event
- Levers now have their own block state 
- Fixed a scripting error that would show when shooting arrows from a dispenser 
- Added 'build document' code for data-driven recipes
- Players can now open and view scripting logs while the game is running 
- All pillar blocks now have their own block state instead of using some values of the direction block state. This allows mirror and rotating with structure blocks
#### *Bug Fixes:*
- Fixed MoLang scripting errors that were being logged for older content
- Endermen with modified behaviour can now be shot and damaged with projectiles 
- Entities crossing chunk boundaries can no longer get corrupted due to the move 
- Fixed humanoid eating animation
- Fix issue of the mini bows rendering on all mobs other than players in scripting packs 
- The "has_equipment" filter work correctly with damageable items
- Loading packs with lots of custom items now works correctly 
- Creating new End Gateway portal in the "Abstraction Cubes" marketplace map now works correctly
- Particle UVs no longer include lines of textures next to the selected UV
- Custom entities using the "nearest_attackable_target" now re-evaluate current target validity

### v1.12.0
#### *Changes for Map Makers & Addons:*
- Created a screen to view content log errors for Behavior and Resource Packs
    - The log screen can be opened using Ctrl + H after enabling in Profile Settings
- Enabled content logging for creators on Bedrock Dedicated Server to debug pack errors
- Mob events can now be toggled using the new '/mobevent' command
- Particle emitters can now trigger slash commands, actor events, and MoLang expressions
- Added the ability to play single animations at any time, overriding an entity's current state-based animation
- Animations and particles can be spawned without being linked to entities using animation timelines
- Sound effects can now be triggered by animation events
- Added auto-complete to the Command Input field for command blocks
- Delay in Ticks for Command Blocks
    - A delay can be added to the command block using the new field, measured in Redstone ticks
##### *Data-Driven Crafting Recipes (Experimental):*
- Allows custom crafting recipes for shaped crafting, shapeless crafting, and furnaces using Behavior Packs
- Recipe JSON files have been added to the Behavior Pack template
##### *Add New Simple Item (Experimental):*
- New "simple" items can be added to the game using Behavior Packs
- Currently, only a subset of components has been exposed, with more being added in future updates to allow more complex behaviors
- Some items, such as food, are now data-driven and their JSON files have been added to the Behavior Pack template
##### *Add New Simple Block (Experimental):*
- New "simple" blocks can be added to the game using Behavior Packs
- Currently, only a subset of components has been exposed, with more being added in future updates to allow more complex behaviors
##### *New Data-Driven Particles:*
- Llama Spit
- Large Explosions
- Colored Flames
- Redstone Dust
- Falling Dust
- Lava
- Enchanting Table
- Conduit
- New Data-Driven Animations:
- Wolf
- Fang Attack
- Arrow
- Shulker Bullet
- Bow
- Water Movement
#### *Script Engine Changes:*
- **Block API V0:**
    - New block events and two new APIs have been included to query for blocks:
    - ***APIs:***
        - getBlock(Ticking Area, x, y, z)
        - getBlock(Ticking Area, PositionObject)
        - getBlocks(Ticking Area, x min, y min, z min, x max, y max, z max)
        - getBlocks(Ticking Area, Minimum PositionObject, Maximum PositionObject)
    - **Events:**
        - block_destruction_started
        - block_destruction_stopped
        - piston_moved_block
        - player_destroyed_block
        - player_placed_block
- **Item API V0:**
    - Basic item related events have been exposed to the Script Engine. This includes:
        - actor_acquired_item
        - actor_carried_item_changed
        - actor_dropped_item
        - actor_use_item
        - actor_equipped_armor
- **Inventory API V0:**
    - Basic inventory events have been exposed to the Script Engine. This includes:
        - inventory_container
        - armor_container
        - hand_container (note that the hand container will get you both the main hand and offhand)
        - hotbar_container
- **executeCommand API:**
    - Allows executing commands with a callback when the command is executed without using events
    - Only usable on Server Scripts
- **Event Data API:**
    - Data is contained in objects passed to callbacks under the data field
    - Custom events need to be registered (registerEvent) before being triggered

```
    All assets belong to Mojang & Microsoft.
```