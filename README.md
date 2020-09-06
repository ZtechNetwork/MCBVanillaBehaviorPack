# Minecraft: Bedrock Edition Behavior Pack
## Repository Status
![GitHub All Releases](https://img.shields.io/github/downloads/ZtechNetwork/MCBVanillaBehaviorPack/total) ![GitHub release (latest by date)](https://img.shields.io/github/v/release/ZtechNetwork/MCBVanillaBehaviorPack) ![GitHub last commit](https://img.shields.io/github/last-commit/ZtechNetwork/MCBVanillaBehaviorPack/master)

### Update on Changelogs (September 5th, 2020)
From v1.16 and on, changelogs shown here will only go back two major versions to prevent a long list. Along with this, new releases will contain changelogs on the [releases](https://github.com/ZtechNetwork/MCBVanillaBehaviorPack/releases) page.

## Changelogs
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
    All assets belong to Mojang & Microsoft.
```