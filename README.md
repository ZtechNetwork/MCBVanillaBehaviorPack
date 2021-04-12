# Minecraft: Bedrock Edition Behavior Pack
## Repository Status
![GitHub All Releases](https://img.shields.io/github/downloads/ZtechNetwork/MCBVanillaBehaviorPack/total) ![GitHub release (latest by date)](https://img.shields.io/github/v/release/ZtechNetwork/MCBVanillaBehaviorPack) ![GitHub last commit](https://img.shields.io/github/last-commit/ZtechNetwork/MCBVanillaBehaviorPack/master)

### Update on Changelogs (September 5th, 2020)
From v1.16 and on, changelogs shown here will only go back two major versions to prevent a long list. Along with this, new releases will contain changelogs on the [releases](https://github.com/ZtechNetwork/MCBVanillaBehaviorPack/releases) page.

## Changelogs
### v1.16.220

#### Changes and Fixes
- Renamed all references of `Actor` to `Entity`.
- Renamed `BlockPos` to `BlockLocation`.
- Updated Behavior Packs to require explicit module dependencies when using other native modules.
- Identifiers within `render_controllers` will now be considered content errors if there is no render controller matching that name.
- Entity json before version 1.16.100 will no longer give a content error for the deprecated field `minecraft:foot_size`.
- Modified condition in `trident.animation_controllers.json` to allow mobs to enter  `wield_third_person_raise`.
- Fixed an issue where loading into a world would cause continuous MoLang errors around "unhandled request for unknown variable".
- Items can now have the `transparentattachable` tag applied to make attachable items not render for the player wearing them in the first person perspective.
- Fixed an issue where V2 Villagers were not properly updating their MoLang variables on initialization.

### v1.16.210
- Added Fog documentation.
#### Fixes
- Horses, Donkeys, Mules, Skeleton Horses, and Zombie Horses can now properly be given custom names, and identified using their respective `runtime_identifier`.
- Improved performance for actors using `TemptGoal`.
- Zombie villagers spawned from zombie spawners on Marketplace worlds that were created after version 1.11 now correctly spawn as V2 zombie villagers. When cured, they will now correctly turn into V2 villagers.
- Fixed upgrade path for `format_version` 1.13.0 boats to be properly upgraded to 1.16.100, which resolves a bug where boats templated worlds with a version lower than 1.16.100 had no gravity.
- Structure blocks no longer auto-save data when structure name text box is deselected.
- Entities that use material state "Blending" now render correctly behind transparent parts.
- The scoreboard data of an entity is no longer removed if the entity is being teleported to an unloaded area of the world.
- Custom blocks now can only drop default state when broken, even with Silk Touch.

#### Technical
- Structures can now be deleted from the saved structure list using the new `/structure delete <name>` command.
- Added new slash command options for `/setblock`, `/fill`, and `/clone` commands for passing in a list of block states to set on the block being spawned.
- A boolean parameter called `ignore_game_mode` has been added for the block event response `decrement_stack`, set to false by default. Thus `decrement_stack` no longer decreases the item stack when playing in Creative by default.
- Changing `RideableComponent` property `rotate_rider_by` to function for custom mobs.
- `SetBlock` and `SetBlockAtPos` events now support custom block states.
- Attachable items created in 1.16.2 and before will not render for their player in first person. Attachable items created after 1.16.2 will render for their player in first person unless they are armor.

#### Custom Biomes and Blocks
- Disabled loading of entities in custom biome features.
- Fixed UVs of data-driven blocks to not be slightly shrunk, which caused texel warping.
- Fixed data-driven blocks being pushed by pistons not working correctly.

#### Render Offsets Component
- Simple items, like swords or pickaxes, can have an optional offset applied to them to modify the way they are rendered. Note this component should not be added to an attachable item.
- Component Variables:
    - `main_hand` - An optional object storing optional transform data for `first_person` and `third_person` for the player's right hand.
    - `off_hand` - An optional object storing optional transform data for `first_person` and `third_person` for the player's left hand.
    - `first_person` - An optional object storing 3 vectors `position`, `rotation`, `scale` used to build the first person matrix.
    - `third_person`- An optional object storing 3 vectors `position`, `rotation`, `scale` used to build the third person matrix.

### v1.16.200
#### Fixes
- Turning bandwidth optimizations off to see if it fixes stationary mob problem and entity "lag" issues.
- Custom projectiles once again animate properly.
- Fixed an issue where loot tables with a `set_data` function produced incorrect loot items.
- Fixed face occlusion with data-driven blocks to properly account for unit cube transparent vs unit cube opaque.
- Data-driven blocks no longer have their top faces rotated 180 degrees when carried or in inventory.
- Fixed an issue with a runaway block ticking queue that occurred on a looping data-driven block that changed itself to a different permutation. The bug could cause memory issues, increased load and save times, as well as stalling the game periodically. (No ID)
- Fixed data-driven blocks to shrink UVs the same way as actors to prevent UV bleeding. (No ID)
- Fixed some culling issues with data-driven blocks larger than 1x1x1 when placed on a chunk boundary. Also added content warnings for larger blocks
- Changed `set_block` and `set_block_at_pos` to use `BlockDescriptor` when specifying `block_type`.
- Old command versions now use the previous position instead of current one
Fixed issue where `query.cardinal_block_face_placed_on` no longer worked with `on_player_placing`.
- Changed texture atlas padding size from 0 to 1 when disabling mipmap
- Fixed issue of blocks listed in the "minecraft:block_placer" component not working correctly.
- Fixed player smaller hitbox while swimming and gliding from being reset after an event is sent on the player.
- Fixed custom spawn egg generation in template worlds.
- MoLang geometry, material, and texture variable names can once again contain dots.
- Items with the item lock component no longer cause the recipe book to show invalid recipe results.

#### Blocks
- Added `query.cardinal_facing_2d` to get a ground plane direction that doesn't return up or down.
- Added the ability to put block models into the models/blocks folder.
- Added the ability for item triggers to send events to the block they are interacting with. (when there is one such as `on_use_on`)
- Added the ability to query the interacted face for both interactions with blocks and using `minecraft:on_use_on` in an item. Face can be queried with `query.block_face`.

#### Components
- Fixed using `query.get_equipped_item_name` with an item that was renamed not returning the right result. We now tie this to vanilla versioning so that the old name is returned if the world is tied to a specific vanilla version.
- `add_mob_effect` and `remove_mob_effect` no longer throw content errors when valid effect names are passed in.
- Added documentation for `remove_mob_effect` to make creators aware they can use the value `all` in effect to remove all mob effects from a target.
- Fixed items not being placeable in additional horse equipment slots. Does not fix all equippable behaviors.
- Inventory size on the minecraft:inventory component has to be increased to match the equippable slots in order for the server to accept the item placement.
- The tooltip for item with item lock component will no longer show when game rule `showtags` is disabled.

### v1.16.100
#### Fixes
- Fixed particles when using animation controllers to play particles and switching to a different state that also plays particles.
- Striders now have a separate texture mapping for each leg, and their leg textures are properly mirrored.
- Pitch written in `sound_definitions.json` is now correctly played.
- FMOD music channel now sets its priority to 0 when music is played to prevent FMOD virtual channel from stealing it when a regular sound is played in game. (default priority is 128)
- Villagers/Zombie Villagers once again correctly spawn as a baby when using the summon command to summon them with the event `minecraft:entity_born`.
- Attempting to load a custom material that is not defined no longer causes a crash. A proper content error is now thrown.

#### Commands
- Added `/structure` command that allows saving and loading of structures without having to use Structure Blocks.
- Added the ability to animate the placement of a structure with the `/structure` command.
- Added the `/music` command, allowing creators to play and control custom music.
- Added `/playanimation` command that allows you to run a one-off animation. It assumes all variables have been setup correctly for the animation to run.
- Added `/camerashake` command to enable a camera shaking effect.
- Added `/ride` command that allows you to make entities ride other entities, stop entities from riding, make rides evict their riders, or summon rides and riders.
- Added `/clearspawnpoint` command that allows you to clear a player’s spawn point.
- Added `/event` command that can be used to trigger an event on an entity.
- Using the `/spawnpoint` command will no longer affect Players that are sleeping.
- Older command versions using `/execute` now use the proper position for command selectors when calculating the radius.

#### Data-Driven Blocks
- Added documentation for block event responses and re-organized block documentation.
- Blocks that have ticking components will now clear their pending ticks from the ticking queue upon removal.
    - Added the `on_player_destroyed` trigger component.
- Made data-driven blocks pathable with disabled collisions.
- Added the `BlockDisplayNameComponent` to allow display names to be configured in the localization table.
- Added support for parsing and performing the following event responses:
    - Added the `set_block_at_pos` event response.
    - Spawn Loot
    - Set Block
    - Added support for the `on_interact` trigger component.
- Added support for the `on_player_placing` trigger component.
    - Also added MoLang queries for `cardinal_block_face_placed_on` and `cardinal_player_facing` for getting placement context.

#### Data-Driven Block Models
- Added the first pass of the new data-driven block tessellation pipeline.
- Added the `minecraft:geometry` component to allow using a block model for rendering.
- Added the `minecraft:unit_cube` component to allow using a default unit cube for rendering. Unit cubes get some extra effects like ambient occlusion and face removal.
- Added the `minecraft:material_instances` component to allow mapping faces and material_instances in a geometry file to an actual material.
- Fixed smooth lighting and ambient occlusion with new data-driven blocks.

#### Placement Filter
Added `minecraft:placement_filter` component which allows you to set conditions for where this block can be placed. This component will also kick in whenever neighboring blocks change and pop its loot if it is no longer in a valid location.

- Added serialization to Block Descriptor.
- Added static anyMatch functions to BlockDescriptor to compare a list of BlockDescriptors against: Block*, BlockLegacy, or BlockDescriptor.
- Added a function to compare two BlockDescriptors. This covers: matching blocks, any tag of either descriptor match, block states with matching permutations.
- Changed the BlockDescriptor BlockLegacy member variable to a Block* so we can set the block states during deferred block resolution and get the block with the states set.
- Removed all the existing Block* json parsing.

#### Schema
- Split `allowed_blocks` into `use_on` and `dispense_on`.
- `use_on` specifies what blocks an entity placer item is allowed to be used on, omit to allow all blocks.
- `dispense_on` specifies what blocks an entity placer item is allowed to be dispensed on, omit to allow all blocks.

#### Execute Command
- Added support to item json events for the `execute_command` keyword. It supports both a string and string array format, where the string is the command intended to run. Commands are compiled at load time and executed after add/remove_mob_effect and teleport actions, but before other triggers for events. Commands will be segmented in sequence and randomize nodes as expected.

#### Run Command
- Added support to entity json events for the `run_command` keyword alongside the current add and remove keywords. It supports both a string and string array format, where the string is the command intended to run. Commands will be run after component groups have been added and removed, and will be segmented in sequence and randomize nodes as expected.
- Updated the following components to parse and use BlockDescriptor instead of Block*
    - BlockBreakSensorComponent
    - BlockListEventMap
    - BreathableComponent
    - BreedableComponent
    - BuoyancyComponent
    - EntityPlacerItemComponent
    - PreferredPathComponent
    - SeedItemComponentLegacy
- Updated the following features to parse and use BlockDescriptor instead of Block*
    - NoSurfaceOreFeature
    - OreFeature
    - SingleBlockFeature
- Updated the following goal definitions to parse and use BlockDescriptor instead of Block*
    - GoalDefinition
    - RaidGardenGoal
    - VanillaGoalDefinition
- Updated the following surfaces code to parse and use BlockDescriptor instead of Block*
    - MesaSurfaceAttributes
    - SurfaceMaterialAdjustmentAttributes
    - SurfaceMaterialAttributes
- Updated the following tests to reflect the changes from updating code to use BlockDescriptors
    - BuoyancyComponentServerTests
    - FeatureHelperTests
    - NoSurfaceOreFeatureTests
    - OreFeatureTests
    - SingleBlockFeatureTests
- Updated the following trees to parse and use BlockDescriptor instead of Block*
    - AcaciaTreeCanopy
    - AcaciaTreeTrunk
    - FallenTreeTrunk
    - FancyTreeCanopy
    - FancyTreeTrunk
    - MegaPineTreeCanopy
    - MegaTreeCanopy
    - MegaTreeTrunk
    - PineTreeCanopy
    - RoofedTreeCanopy
    - SimpleTreeCanopy
    - SimpleTreeTrunk
    - SpruceTreeCanopy
    - TreeHelper

#### Actors
- Squid rendering is now data-driven.
- All types of minecarts are now data-driven.
- The `minecraft:behavior.controlled_by_player` goal is now data-driven.
- Physics component's `has_gravity` field is now used to decide whether a mob should apply water gravity, if the mob does not have a navigation component
- Spatial Bandwidth Optimizations are now exposed through a component, `minecraft:conditional_bandwidth_optimization`.
- Spatial Bandwidth Optimizations are now utilized by every actor using `minecraft:conditional_bandwidth_optimization`.
- Added the selector component to raw text, which can be used to print entity names in commands such as `tellraw` and `titleraw`.
- Pathfinding will now account for the `minecraft:scale` component.
- Updated BrewingStand, ButtonBlock, ChestBlock, EnderChestBlock, SlabBlock, and SoulSandBlockblock types to allow path-finding and navigation.
- Updated Actor Properties. Two fields that were invalid and appeared in some vanilla content will now give a content error. The field `value` on `minecraft:can_fly` and the property `minecraft:foot_size` should simply be removed from any entity files.
- The `MoveToLiquidGoal` has been changed to use data for its target block.
- Strider now correctly executes the `move_to_liquid` goal.
- Made boats use the Buoyancy component. Added two new components, the `inside_block_notifier` component, which fires specified events when the actor enters or exits specified blocks, and the `out_of_control` component, which sets a corresponding actor flag, in order to make this possible.
- Exposed new data parameters to control the behavior of Drop Item For Goal. This includes: `seconds_before_pickup`, `cooldown`, `minimum_teleport_distance`, `max_head_look_at_height`, `teleport_offset`, and `entity_types`. Check out the new Actor component documentation!
- Exposed new data parameters to control the behavior of Harvest Farm Block Goal, including `max_seconds_before_search`, `search_cooldown_max_seconds`, and `seconds_until_new_task`. Check out the new Actor component documentation!
- Added error checks to parsing of Minecraft shareables items. Displays content log if item name is invalid or the array is empty.

#### Fog
- Created `/fog` command for managing active fog settings for players; these fog settings override fog driven from the client such as biome location of player camera.
- Updated `biomes_client.json` to link each biome to a fog definition identifier.
- Added child object `volumetric` which contains `density` and `media_coefficients` objects. These hold the data values used for the volumetric fog.

#### Record Item Component
- Items can now be made records to play music in Jukeboxes.
- **Component Variables**
    - `sound_event` - A string value correseponding to a sound event in the game code. This string must be one these for music to play: `13`, `cat`, `blocks`, `chirp`, `far`, `mall`, `mellohi`, `stal`, `strad`, `ward`, `11`, `wait`, `pigstep`.
    - `duration` - A float value that determines how long particles are spawned from the JukeBox Block, should approximately match length of sound event.
    - `comparator_signal` - An integer value that represents the strenght of the analog signal, used by the Comparator Block.
- **Examples**
    - When added to JukeBox Block this will play the sound clip of `record.chirp`
    - Example 1: `"minecraft:record": { "sound_event": "chirp", "duration": 185.0, "comparator_signal": 4 }`

#### Items
- Renamed items to be consistent with the list of Java Edition items.
- Created RepairableItemComponent that data-drives how an item is repaired in game.
- Items can now override their display name with a localized `value`. If a value is not supplied, the component will stay with its default name. If the value supplied is not in the localization file, the display name will be the value string.
- Added a Lock in Inventory component that can be applied to an item via the `/give` and `/replaceitem` commands. This prevents the item from being removed from the player's inventory, dropped, or crafted with. 
    - Example of use: `/give @s apple 1 0 {"item_lock": {"mode": "lock_in_inventory"}}`
- Added a Lock in Slot component that can be applied to an item via the `/give` and `/replaceitem` commands. This prevents the item from being moved or removed from its slot in the player's inventory, dropped, or crafted with.
    - Example of use: `/give @s apple 1 0 {"item_lock": {"mode": "lock_in_slot"}}`
- Added a Keep on Death component which can be applied to an item via the `/give` and `/replaceitem` commands. This component prevents the item from being dropped when the player dies.
    - Example of use: `/give @s apple 1 0 {"keep_on_death": {}}`

#### Item Icon Component
- Items now have an easy way to set the icon for an item for displaying in the user interface.
Component Variables
`texture`: Full path to icon image to use as item's icon. No default.
`frame`: Molang script to be executed at runtime to determine the icon's current frame. Can be a constant, defaults to: `0`.
`legacy_texture_id`: The name of the texture used on legacy items. No default.
`legacy_frame`: Molang script to be executed at runtime to determine the icon's current frame. Can be a constant, defaults to: `0`.

#### Item Parsing
- `any_tag` functionality added to several actor components. In addition to representing items as item names in json they can now be represented as a set of tags.
- Examples:
    - `"item": {"any_tag": "food"}`
    - `"item": {"any_tag": ["food", "wood"]}`
    - `"bribe_items": ["emerald", {"any_tag": "stone"}]`
- Components and fields that can now use `any_tag` functionality:
    - `minecraft:ageable`
    - `minecraft:breedable` breed_items
    - `minecraft:bribeable` bribe_items
    - `minecraft:giveable` items
    - `minecraft:healable` items
    - `minecraft:tamemount` feed_items and auto_reject_items
    - `minecraft:equippable` accepted_items

#### Technical Changes
- Item names of the format `minecraft:item.someitem` no longer need the `item.` portion and it will be ignored.
- Added Entity Movement Prediction.
- Changed LegacyCubemap from opaque to transparent.
- Added `decrement_count` event response for items.
- **'minecraft:behavior.send_event' Changes**
    - `minecraft:behavior.send_event` no longer uses `-1` in `max_activation_range` as a value to indicate unlimited range, the default has been changed to `32`.
    - Added content log warnings for when `min_activation_range` and `max_activation_range` is less than `0`.
    - Added content log warnings for when `min_activation_range` is greater than `max_activation_range`.
- **'minecraft:behavior.summon_entity' Changes**
    - `minecraft:behavior.summon_entity` no longer uses `-1` in `max_activation_range` as a value to indicate unlimited range, the default has been changed to `32`.
    - Added content log warnings for when `min_activation_range` and `max_activation_range` is less than `0`.
    - Added content log warnings for when `min_activation_range` is greater than `max_activation_range`.
- Fixed a difference with the default return type of the script function, which differed from the usual return type. (No ID)
- Added new BlockRaycastComponent that can override the AABB used for outlines and raycasting.
- Added new BlockCollisionComponent that can override the AABB used for entity collision.
- Added new BlockPropertyComponent that can replace the blockProperties : Unwalkable, Infiniburn, PreventsJumping, Immovable, BreakOnPush, OnlyPistonPush and BreaksWhenHitByArrow.
- Added new BlockQueuedTickingComponent that triggers events for a block on a range of time set by the creator.
- Added new BlockRandomTickingComponent that triggers events for a block randomly.
- Added a Rotation Component that allows a block to rotate. The component only allows axis-aligned rotations.
- Adds the base implementation of the CraftingTableComponent.
    - Allows the creation of custom crafting tables.
    - Currently only supports 3x3 grids.

#### Animations
- Added a new `loop_delay` field to skeletal animation files that controls how to wait between each iteration of a looping animation.
- Fixed a bug where `start_delay`fields in skeletal animations were being used for both the initial delay before playing an animation and for inter-loop delays.

#### MoveTowardsRestrictionGoal
- This goal has been removed in favor of the two new child goals that make the behavior clearer. The behavior works the same, but is now separated out properly into the two goals.
#### MoveTowardsDwellingRestrictionGoal
- This goal is for Actors that are part of the Village construct.
- The `DwellerComponent` is necessary for this goal.

#### MoveTowardsHomeRestrictionGoal
- The `HomeComponent` is necessary for this goal
- Exposed a new data parameter for the range at which the Actor will stay within in relation to their home: `restriction_radius`

#### Send Event Goal
- `minecraft:behavior.send_event` no longer uses `-1` in `max_activation_range` as a value to indicate unlimited range, the default has been changed to `32`
- Added content log warnings for when `min_activation_range` and `max_activation_range` is less than `0`.
- Added content log warnings for when `min_activation_range` is greater than `max_activation_range`.
- Added a new json field `look_at_target` which allows and disallows entities to turn and face their target.

#### SetBannerDetailsFunction
- Now supports customizing non-Illager banners.
- Up to 6 patterns and colors can be specified.
- **Accepted Banner Types**
    - `default` `illager_captain`
- **Accepted Color Values**
    - `black` `red` `green` `brown` `blue` `purple` `cyan` `silver` `gray` `pink` `lime` `yellow` `light_blue` `magenta` `orange` `white`
- **Accepted Pattern Values**
`base` `border` `bricks` `circle` `creeper` `cross` `curly_border` `diagonal_left` `diagonal_right` `diagonal_up_left` `diagonal_up_right` `flower` `gradient` `gradient_up` `half_horizontal` `half_horizontal_bottom` `half_vertical` `half_vertical_right` `mojang` `piglin` `rhombus` `skull` `small_stripes` `square_bottom_left` `square_bottom_right` `square_top_left` `square_top_right` `straight_cross` `stripe_bottom` `stripe_center` `stripe_downleft` `stripe_downright` `stripe_left` `stripe_middle` `stripe_right` `stripe_top` `triangle_bottom` `triangle_top` `triangles_bottom` `triangles_top`
- **Possible Input:**
```JSON
"function": "set_banner_details",
"type": "default",
"base_color": "blue",
"patterns": [
    {
        "pattern": "flower",
        "color": "white"
    },
    {
        "pattern": "triangle_bottom",
        "color": "brown"
    }
]
```

#### Format Version Checks
- Updated the `format_version` field in geometry, particles, and animation files to behave as entity behavior files do. That is, you no longer need to specify a specific version for it to be accepted, instead you can just specify the version of the release you are targeting.

### v1.16.20
- Updated Piglin geometry and entity files: Fixed issue with scaling carried item for baby humanoid mobs.
- Accessing a Beacon no longer spams the content log with warnings.
- The `rider_can_interact` field on `minecraft:rideable` is now used again.
- Behavior animation components will no longer try to reload after a suspend resume and a mob/player rides something.
- Drowned geometry is no longer broken in content packs.

### v1.16.0 | Nether Update
#### Data-Driven Features
- Most attack goals are now data-driven.
- Most Slime and swim goals are now data-driven.
- Experience Orbs have been data-driven.
- Fireballs have been data-driven.
- Elytra have been data-driven.
- NPC geometry and animations have been data-driven.
- Tree generation is now data-driven.
- Drowned are now data-driven.
- Wither skull attacks are now data-driven.
- Item sprites are now data-driven.
- Updated documentation for new data-driven features.

#### Admire Item Component
- Mobs can now admire items they pick up or receive during an interaction. For a mob to admire an item they need to have both the `admire_item goal` and the `admire_item component`, and the relevant configuration need to be done in the interact component and/or the shareables component. 

#### Angry Component
- Several new variables have been introduced to the `angry` component.
- Goal Variables
    - `broadcast_anger_on_attack` - If true the mob will send a pulse of brodcast anger whenever it attacks, `broadcast_anger` must also be `true` for this to work.
    - `broadcast_anger_on_being_attacked` - If true the mob will send a pulse of brodcast anger whenever it is attacked, `broadcast_anger` must also be `true` for this to work.
    - `angry_sound` - The sound event to play when the mob is `angrysound_interval` - The range of time in seconds to randomly wait before playing the sound again.

#### Avoid Mob Type Goal
- Several new variables have been introduced to the `avoid_mob_type` goal.
- Goal Variables
    - `avoid_mob_sound` - The sound event to play when the mob is angry.
    - `sound_interval` - The range of time in seconds to randomly wait before playing the sound again.

#### Barter Component
- Mobs can now barter when they pick up items, or when they receive an item during an interaction. For a mob to barter they need to have both the `barter` goal and the `barter` component, and the relevant configuration need to be done in the `interact` component and/or the `shareables` component.
- Component Variables
    - `barter_table` - A path to a loot table, which is used to determine what items the mob gives out during barter.
    - `cooldown_after_being_attacked` - Specifies for how long the goal will be unavailable after the mob is attacked, the default value is `0`.
- Barter Goal
    - Mobs can now barter when they pick up items, or when they receive an item during an interaction. For a mob to barter they need to have both the `barter` goal and the `barter` component, and the relevant configuration need to be done in the `interact` component and/or the `shareables` component.
- Goal Variables
    - `priority` - Specifies how the mob should prioritize this goal.

#### Celebrate Hunt Component
- Specifies that the mob should have the hunt celebration behavior.
- Component Variables
    - `broadcast` - If true, celebration will be broadcasted to other entities in the radius. Default value is `true`.
    - `radius` - If broadcast is enabled, specifies the radius in which it will notify other entities for celebration. Default value is `16`.
    - `duration` - Duration, in seconds, of celebration. Default value is `4`.
    - `celeberation_targets` - The list of conditions that target of hunt must satisfy to initiate celebration.
    - `celebrate_sound` - The sound event to play when the mob is celebrating.
    - `sound_interval` - The range of time in seconds to randomly wait before playing the sound again.

#### Equip Item Component
- Mobs can now equip armor and weapons that they pick up.

#### Equip Item Goal
- Mobs can now equip armor and weapons that they pick up.

#### Interact Component
- Component Variables
    - `barter` - If true the mob will try to activate the barter goal after the interaction, default value is `false`.
    - `admire` - If true the mob will try to activate the admire goal after the interaction, default value is `false`.

#### MoveToLavaGoal
- Added the `MoveToLava` goal, similar to `MoveToWater` goal. Mob tries to find and move to lava.

#### Navigation Component
- Navigation component now has `can_path_over_lava` and `can_walk_in_lava` parameters, allowing mobs (like the strider) to traverse lava.

#### Panic Goal
- Changed the priority from the damage type to the `ignore_mob_damage` flag (if that flag is set and a mob attacks the mob with the Panic Goal, they will not panic even if the damage type matches one in their `damage_sources` list).
- Changed damage types from being hard-coded to being data-driven using the existing "Entity Damage Sources".
- Changed the default from `fire`, `fire_tick`, `magma` (old, hardcoded behavior) to `all`.
- Pre-1.16 mobs will default to `fire`, `fire_tick`, `magma`.

#### Pickup Items Goal
- The `PickupItemsGoal` only considers items that the mob can reach.
    - When determining whether the goal can be used, we now check whether the mob can reach an item it’s interested in, before committing to it as the target of the goal. This is to avoid mobs getting stuck in this goal after deciding to pick up an item they cannot reach.
- PickupBasedOnChance variable
    - This new variable was added to be used for monsters that can pick up items sometimes but also preserve mobs that used this goal in the past like Villagers. If this variable is `true`, the mob will have a calculation done (based on things like time played by the player, game difficulty, and moon brightness) to determine if this is a mob that is allowed to pick up items. That value is only calculated on the mob’s first spawn, which means it is forever saved on that mob and doesn’t change. If the variable is `false` (which it is by default), the mob will always be able to pick up items using the goal.
- CanPickupAnyItem variable
    - The `PickupItemsGoal` is dependent on the `ShareableComponent` and the items that are added to its items list. This new variable overrides that list and tells the component that this mob can pick up any item even if it isn’t in the list. Items picked up because of this variable still honor the priority set to items in the list of items, however. This means that any items with a set priority in the list will still be picked up over any item that may be picked up because of this variable. By default, it is set to `false`.
- CooldownAfterBeingAttacked variable
    - The variable `cooldown_after_being_attacked` has been added to the goal, specifying for how many seconds after being attacked the goal should be unavailable. The default value is `0`.
- CanPickupToHandOrEquipment variable
    - Specifying if the mob can equip items that it picks up or put items in its hand, or if it belongs in the inventory.

#### Shareable Component
- Component Variables
    `item/barter` - If `true` the mob will try to activate the barter goal after picking up the item, default value is `false`.
    - `item/admire` - If `true` the mob will try to activate the admire goal after picking up the item, default value is `false`.
    - `item/consume_item` - Specifies if an item should be consumed, for instance Piglins consume (eat) porkchop. Default value is `false`.
    - `item/stored_in_inventory` - Specifies if the item is desired to be picked up and stored in the mob’s inventory. Default value is `false`.

#### Splash Text
- The Splash Text loading code has been augmented to allow splash text JSON files to be additive, rather than replacing them completely, and to allow some conditional statements to disable splash text entries. Use a field called `canMerge` that sits next to the `splashes` field, it is a bool that defaults to `false`. Also, another sibling of `splashes` is `conditional`, which is an array of objects. Those objects contain a `requires` field and a `splashes` field. The `splashes` field is an array of strings like the original `splashes` field, and the `requires` field contains three fields - `platforms`, `treatments`, and `stores`, each of which is an array of strings that is compared with the relevant data.

- Bug Fixes. For more details, [click here](https://feedback.minecraft.net/hc/en-us/articles/360044928311-Minecraft-Nether-Update-1-16-0-Bedrock-).

### v1.14.60
- No changes made to Addons and Scripts.

### v1.14.30
- No changes made to Addons and Scripts.

### v1.14.1
- No changes made to Addons and Scripts.

### v1.14.0
- No changes made to Addons and Scripts.
- Updated documentation for `v1.14.X`.

```
    All assets belong to Mojang Studios & Microsoft.
```