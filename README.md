# Minecraft: Bedrock Edition Behavior Pack
## Repository Status
![GitHub All Releases](https://img.shields.io/github/downloads/ZtechNetwork/MCBVanillaBehaviorPack/total) ![GitHub release (latest by date)](https://img.shields.io/github/v/release/ZtechNetwork/MCBVanillaBehaviorPack?include_prereleases) ![GitHub last commit](https://img.shields.io/github/last-commit/ZtechNetwork/MCBVanillaBehaviorPack)

## Changelogs
### v1.13.0.9 [Beta]
#### *New Features:*
- Added Wither Rose
- Added Suspicious Stew
- Item Frames can now be placed on the floor and ceiling! 
- Added the Brown Mooshroom
    - Forged by lightning bolts!
- Added abandoned Villages
- Added the Light Block for mapmakers
    - This supports auxiliary data from 0 to 15 for light level
    - The invisible end rod (variant 6) is now auto-upgraded to the new light block
    - Light blocks are supported via /give, /fill, and /setblock.
- Added successful Village Raid celebration 
- Added game credits
    - These can be viewed after defeating the Ender Dragon, and also through a new button found in the Settings menu
- New note block sounds!
    - Added note block functionality for glowstone, haybale, block of emerald, pumpkin, soul sand, block of Iron, bone block, wool, packed ice, clay, and block of gold 
#### *Changes:*
- Squid can now spawn in rivers!
- Added Dead Coral Plants
- Updated and added new Note Block sounds
- Players are now 1.8 blocks tall
- Villagers can now heal if they have bread in their inventory
- Added a "How to Play" section for Structure Blocks 

### v1.13.0.6 [Beta]
- Bug Fixes.
- See the full [changelog](https://feedback.minecraft.net/hc/en-us/articles/360031985392-Minecraft-Beta-1-13-0-6-Xbox-One-Windows-10-Android-) for more info.

### v1.13.0.5 [Beta]
- Bug Fixes.
- See the full [changelog](https://feedback.minecraft.net/hc/en-us/articles/360031774332-Minecraft-Beta-1-13-0-5-Xbox-One-Windows-10-Android-) for more info.

### v1.13.0.4 [Beta]
- Bug Fixes.
- See the full [changelog](https://feedback.minecraft.net/hc/en-us/articles/360031240811-Minecraft-Beta-1-13-0-4-Xbox-One-Windows-10-Android-) for more info.

### v1.13.0.2 [Beta]
- Bug Fixes. 
- See the full [changelog](https://feedback.minecraft.net/hc/en-us/articles/360030455372-Minecraft-Beta-1-13-0-2-Xbox-One-Windows-10-Android-) for more info.

### v1.13.0.1 [Beta]


### v1.12.0
#### *Addon Changes:*
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