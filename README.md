# Minecraft: Bedrock Edition Behavior Pack
## Repository Status
![GitHub All Releases](https://img.shields.io/github/downloads/ZtechNetwork/MCBVanillaBehaviorPack/total) ![GitHub release (latest by date)](https://img.shields.io/github/v/release/ZtechNetwork/MCBVanillaBehaviorPack) ![GitHub last commit](https://img.shields.io/github/last-commit/ZtechNetwork/MCBVanillaBehaviorPack/master)


## Changelogs
### v1.13.2 (iOS Only)
- No changes to Addons and Scripts.

### v1.13.1
- No changes to Addons and Scripts.

### v1.13.0
#### *Changes for Map Makers & Addons:*

- **New Data-Driven Objects for Add-Ons**
    - Brewing stand potion recipes are now data-driven
    - Arrow shake animation
    - Item breaking particles
    - Data-driven environment damage for entities
    - Added 'push' component that determines whether an entity can be pushed
    - Added 'persistent' component that determines whether an entity should be persistent in the game world
    - Turtle Lightning interactions are now data-driven
    - Pufferfish puffed states are now data-driven
    - Guardian/Elder Guardian animation and rendering
        - Fixed unparented geometry on pre-1.8 guardians
        - Elder Guardian spike animation
    - Fishing hook
    - Horse models and animations
    - Snow Golem trail behavior
    - Dragon Breath particles
    - Sparkler particles (Education)
    - Balloons (Education)

- **Script Engine**

    - Actor Definition Events can now be triggered from scripts
    - Scripting logs can now be opened and viewed while the game is running
    - Added new scripting Actor tags
    - Added 'container' scripting component for blocks
    - Added 'projectile_hit' scripting event
    - Added 'entity_hurt' scripting event
    - Added 'entity_sneak' scripting event
    - Added 'entity_attack' scripting event
    - Added 'block_exploded' scripting event

- Added new feature rules data that implements existing biome decoration through JSON

    - Final infrastructure changes required to support fully data-driven features. Rules themselves must be provided in a behavior pack with Experimental Gameplay enabled

- Significantly increased the maximum 'spawnRadius' distance
- Levers now have their own block state
- Changed Breathable, RideTick, and Transformation systems to use ViewedEntityContext
- All pillar blocks now have their own block state instead of using some values of the direction block state. This allows mirror and rotating with structure blocks

- **Changes to Pack Manifests**
    - ***Summary***
        - As of 1.13, we have made some changes to the pack manifest with a new format version of "2". We recommend that any new packs or world templates that you create use format version of 2 from now on. With this new format, there are a few additional changes to be aware of, detailed below
- **All Pack Types**
    - The 'name' field in the header is now required for all pieces of content
- **World Templates**
    - The 'lock_template_options' field is now required. This Boolean field determines whether the world options for your template should be locked to default values when a player creates a world from the template. They can still choose to unlock and modify the options, but will be warned that doing so could affect gameplay
    - The 'base_game_version' field is required (see below for more info)
    - The 'min_engine_version' field should no longer be used as it isn't parsed on world templates and produces a warning on import
- **Resource and Behavior Packs**
    - The 'min_engine_version' field is now required. This affects how the game interprets some of the assets loaded from Resource and Behavior Packs. We recommend using the latest available version of the game for this field (e.g. '[1, 13, 0]') to ensure your pack works correctly
- **Base Game Version Field**
    - For this field, we recommend using the value "*". This will ensure that anyone using your content in their Minecraft worlds will always get the latest base game (Vanilla) content when an update is available.
    - In the case that your content relies on specific base game behavior, you can use this field to specify a base game version, starting with 1.13. If you choose to do this, you should omit the third octet; for example, if the version of the game you are targeting is '[1, 14, 2]', you would specify a version of '[1, 14, 0]'). If you specify a version this way, any worlds using your custom content will not get new base game content when it becomes available in future releases, which could help prevent unwanted changes to behavior in your content caused by updates to the base game. However, we still recommend using the "*" value to ensure players can continue to enjoy your content in their Minecraft worlds long-term while also receiving updates to the base game

### v1.12.1
- No changes to Addons and Scripts.

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