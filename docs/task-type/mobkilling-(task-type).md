Kill a set amount of mobs.

Since Quests v3.13, `mobkillingcertain` and `mobkilling` have been
merged into one. Both names can be used to refer to this task.

## Options

| Key       | Description                                      | Type                             | Required | Default | Notes                                                                                                                                                                                              |
|-----------|--------------------------------------------------|----------------------------------|----------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amount`  | The number of mobs to kill.                      | Integer                          | Yes      | \-      | \-                                                                                                                                                                                                 |
| `mob`     | The specific mob(s) to kill.                     | Entity type, or list of entities | No       | \-      | Not specifying this field will allow all mob types to count towards the task. Please see [this list](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html) for entity types. |
| `name`    | The specific name(s) of mobs to kill.            | String, or list of strings       | No       | \-      | Not specifying this field will allow mobs with any names to count towards the task. Ensure any colour codes in the name of the entity are specified, otherwise the match will not work.            |
| `hostile` | Whether the mob must be hostile.                 | Boolean                          | No       | \-      | If specified and set to false, only non-hostile mobs will count.                                                                                                                                   |
| `item`    | Specific item which should be used to kill mobs. | ItemStack                        | No       | \-      | Accepts standard [item definition](defining_items "wikilink").                                                                                                                                     |
| `worlds`  | Worlds which should count towards the progress.  | List of world names              | No       | \-      | \-                                                                                                                                                                                                 |

## Examples

Kill 10 of any mob:

``` yaml
mobkilling:
  type: "mobkilling"
  amount: 10                            # amount of mobs to be killed
  hostile: true                         # (OPTIONAL) whether or not the mob is hostile - default: both
  worlds:                               # (OPTIONAL) restrict to certain worlds
   - "world"
```

Kill 10 of a blaze named (red) "Inferno":

``` yaml
mobkillingblaze:
  type: "mobkilling"
  amount: 10                            # amount of mobs to be killed
  mob: BLAZE                            # (OPTIONAL) type of mob
  name: &cInferno                       # (OPTIONAL) this only allows blazes called "&cInferno" - default: any name
  worlds:                               # (OPTIONAL) restrict to certain worlds
   - "world"
```

Kill 10 of a blade named either (red) "Inferno" or (orange) "Furnace":

``` yaml
mobkillingblazemultiple:
  type: "mobkilling"
  amount: 10                            # amount of mobs to be killed
  mob: BLAZE                            # (OPTIONAL) type of mob
  names:                                # (OPTIONAL) this only allows blazes called "&cInferno" OR "&6Furnace" - default: any name
   - "&cInferno"
   - "&6Furnace"
  worlds:                               # (OPTIONAL) restrict to certain worlds
   - "world"
```

Kill 10 of a blaze or creeper named either (red) "Inferno" or (orange)
"Furnace":

``` yaml
mobkillingblazemultiple:
  type: "mobkilling"
  amount: 10                            # amount of mobs to be killed
  mob:                                  # (OPTIONAL) types of mobs
   - BLAZE                              
   - CREEPER
  names:                                # (OPTIONAL) this only allows blazes called "&cInferno" OR "&6Furnace" - default: any name
   - "&cInferno"
   - "&6Furnace"
  worlds:                               # (OPTIONAL) restrict to certain worlds
   - "world"
```

Kill 10 of a blaze or creeper named either (red) "Inferno" or (orange)
"Furnace" with [quest item](Defining-items#Quest-items "wikilink")
"super_sword":

``` yaml
mobkillingblazecreepermultiple:
  type: "mobkilling"
  amount: 10                            # amount of mobs to be killed
  mob:                                  # (OPTIONAL) types of mobs
   - BLAZE                              
   - CREEPER
  names:                                # (OPTIONAL) this only allows blazes called "&cInferno" OR "&6Furnace" - default: any name
   - "&cInferno"
   - "&6Furnace"
  item:                                 # (OPTIONAL) specific item to kill with
    quest-item: "super_sword"
  worlds:                               # (OPTIONAL) restrict to certain worlds
   - "world"
```
