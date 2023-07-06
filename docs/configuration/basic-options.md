---
title: Basic options
parent: Configuration
nav_order: 1
---
# Basic options
{: .no_toc }

Quests allows you to configure **basic options** for the
plugin. These can all be located in the `config.yml`.

{: .how-to-read }
> Each option is laid out with its path underneath the title.
> A dot in the path means an extra level of indentation, for example
> `options.categories-enabled` represents:
> 
> ```yaml
> options:
>   categories-enabled: [value]
> ```
> 
> You should have a working knowledge of how to format YAML files
> before configuring this plugin.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Categories enabled

  
*`options.categories-enabled`*

Choose whether or not quests will be sorted into categories. If this is
disabled, quests will be put into one big GUI instead, with categories
only helping determine the order they are sorted.

``` yaml
options:
  # ...
  categories-enabled: true
```

## Trim gui size

  
*`options.trim-gui-size`*

Choose whether or not the quests GUI will scale down (reduce the number
of rows) so that there are not any empty rows.

``` yaml
options:
  # ...
  trim-gui-size: true
```

## Titles enabled

  
*`options.titles-enabled`*

Choose whether or not titles will appear when starting / finishing
quests.

``` yaml
options:
  # ...
  titles-enabled: true
```

## Quest started limit

*`options.quest-started-limit`*

{: .warning }
**This option has been removed in version 3.8 and this wiki entry is
subject to removal.** Please see [quest limit](#quest-limit)
instead.

Choose the number of quests players can start at one time. This will
include quests which have [quest-specific
autostart](creating-a-quest#autostart) enabled, however this
value will be ignored if [global
`quest-autostart`](#quest-autostart) is enabled.

``` yaml
options:
  # ...
  quest-started-limit: 2
```

## Quest limit

  
*`options.quest-limit`*

Choose the number of quests players can start at one time. This will
include quests which have [quest-specific
autostart](creating-a-quest#autostart) enabled, however this
value will be ignored if [global
`quest-autostart`](#quest-autostart) is enabled.

Each key is called a **limit group** (sometimes referred to as a quest
rank), and players can start the set number of quests depending on their
limit group. The group named `default` must be defined and is available
to everybody, however the rest can be granted through the permission
`quests.limit.<limit group>`.

``` yaml
options:
  # ...
  quest-limit: 
    default: 2
    group1: 5
    group2: 10
    # ...
```

Group permissions are also documented in [Commands and permissions §
Permissions](../commands-and-permissions#permissions).

## Allow quest cancel

  
*`options.allow-quest-cancel`*

Choose whether or not players can cancel quests themselves via command
or by right-clicking in the GUI. If this is set to false, consider
removing the right-click cancel instruction from the [global quest
display
configuration](global-configurations#global-quest-display-configuration).

``` yaml
options:
  # ...
  allow-quest-cancel: true
```

## Allow quest track

  
*`options.allow-quest-track`*

Choose whether or not players can track quests themselves via command or
by middle-clicking in the GUI. If this is set to false, consider
removing the middle-click track instruction from the [global quest
display
configuration](global-configurations#global-quest-display-configuration).

``` yaml
options:
  # ...
  allow-quest-track: true
```

## Task type exclusions

  
*`options.task-type-exclusions`*

Prevent Quests from allowing specific task type registrations from those
bearing a specific name. This can be used if you have an incompatible
plugin which causes a dependent task type to activate, thus potentially
leading to errors.

``` yaml
options:
  # ...
  task-type-exclusions: []
```

**Example**

``` yaml
options:
  # ...
  task-type-exclusions:
   - "blockbreak"
   - "blockbreakcertain"
```

## Guinames

  
*`options.guinames`*

Change and define specific GUI names for localization.

``` yaml
options:
  # ...
  guinames:
    quests-category: "Quests Categories"
    quests-menu: "Quests"
    quests-started-menu: "Started Quests"
    daily-quests: "Daily Quests"
    quest-cancel: "Cancel Quest"
```

## Sounds

  
*`options.sounds`*

Choose which sounds play at certain events.

``` yaml
options:
  # ...
  sounds:
    quest-start: "ENTITY_PLAYER_LEVELUP:2:3"
    quest-cancel: "UI_TOAST_OUT:2:3"
    quest-complete: "UI_TOAST_CHALLENGE_COMPLETE:1.25:3"
    gui:
      open: "ITEM_BOOK_PAGE_TURN:1:3"
      interact: "ITEM_BOOK_PAGE_TURN1:3"
```

To define a sound, choose one from [this
list](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Sound.html)
(1.9+) or [this
list](https://helpch.at/docs/1.8.8/index.html?org/bukkit/Sound.html)
(1.8).

To not have a sound play, you can leave the string blank (i.e. `""`),
for example:

``` yaml
options:
  # ...
  sounds:
    quest-start: ""
```

You can choose a specific pitch and volume by including them in the
following format `SOUND:PITCH:VOLUME`. Note that the pitch is any float
between 0.5 and 2 (inclusively), and the volume must be greater than 0.
The volume only changes how far out the sound can be heard by the
player, not the actual volume played back on the client.

**Example (1.9+):** `ENTITY_PLAYER_LEVELUP:2:3` -\> sound
`ENTITY_PLAYER_LEVELUP` at pitch `2` with a volume of `3`.

## GUI hide locked

  
*`options.gui-hide-locked`*

Choose whether quests which cannot be started is visible to the player
or not.

``` yaml
options:
  # ...
  gui-hide-locked: false
```

## GUI confirm cancel

  
*`options.gui-confirm-cancel`*

Choose whether or not there is a confirmation screen when right clicking
to cancel a quest. Cancelling by command does not prompt a confirmation
screen.

``` yaml
options:
  # ...
  gui-confirm-cancel: true
```

## GUI hide quests if no permission

  
*`options.gui-hide-quests-nopermission`*

Choose whether or not quests are hidden to the player if they do not
have permission for the quest.

``` yaml
options:
  # ...
  gui-hide-quests-nopermission: false
```

## GUI hide categories if no permission

  
*`options.gui-hide-categories-nopermission`*

Choose whether or not categories are hidden to the player if they do not
have permission for the category.

``` yaml
options:
  # ...
  gui-hide-categories-nopermission: false
```

## GUI use PlaceholderAPI

  
*`options.gui-use-placeholderapi`*

Choose whether or not the quest GUI is parsed with PlaceholderAPI. This
is disabled by default for performance reasons.

``` yaml
options:
  # ...
  gui-use-placeholderapi: false
```

## GUI truncate requirements

  
*`options.gui-truncate-requirements`*

Choose whether or not the displayed quest requirements for specific
quests should be cut short. The plugin will show "Quest 1 +X more" as
the requirement, rather than listing each quest "Quest 1, Quest 2, Quest
3, ..." to stop lores overflowing off the screen.

``` yaml
options:
  # ...
  gui-truncate-requirements: true
```

## GUI actions

  
*`options.gui-actions`*

Set the click actions for the UI. For a list of click types, check the
[ClickType javadoc
page](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/ClickType.html).

``` yaml
options:
  # ...
  gui-actions:
    start-quest: "LEFT"
    track-quest: "MIDDLE"
    cancel-quest: "RIGHT"
```

## Quest autostart

  
*`options.quest-autostart`*

Choose whether or not players need to start quests themselves. This will
ignore the configured [quest started
limit](#quest-started-limit), and is different from the
[autostart](#quest-autostart) option.

``` yaml
options:
  # ...
  quest-autostart: false
```

## Quest autotrack

  
*`options.quest-autotrack`*

Choose whether or not players need to track quests themselves. This will
automatically track quests when they are started, and will attempt to
track the next available started quests when the player finishes a
quest.

``` yaml
options:
  # ...
  quest-autotrack: true
```

## Verbose logging level

  
*`options.verbose-logging-level`*

Choose how much quests will log to the console. This will filter the
output based on the following options: 0 = errors only, 1 = warnings, 2
= info, 3 = debug

``` yaml
options:
  # ...
  verbose-logging-level: 2
```

## Quests use PlaceholderAPI

  
*`options.quests-use-placeholderapi`*

Choose whether or not start strings, reward strings, reward commands and
start commands are parsed with PlaceholderAPI. This is disabled by
default for performance reasons.

``` yaml
options:
  # ...
  quests-use-placeholderapi: false
```

## Verify quest exists on load

  
*`options.verify-quest-exists-on-load`*

Verify quests exist when a player's data is loaded - inconsistencies may
arise when players progress on specific quests and those quests are
later removed. Their progress is still retained in the quest progress
file, which may lead to issues such as players reaching a quest started
limit when the quests they had active no longer exist - having this
option enabled prevents non-existent quests from loading as quest
progress.

``` yaml
options:
  # ...
  verify-quest-exists-on-load: true
```

## Performance tweaking

  
*`options.performance-tweaking`*

Set some specific options within the internals of Quests.

The `queue executor interval` relates to how frequently players are
checked for completed quests. Not every player is checked at once for
performance purposes, and players are only submitted to the queue upon
completion of a task. The interval defines how frequently players are
polled from the queue.

The `autosave interval` refers to how frequently all online players data
is saved. Data is saved at autosave intervals to prevent data loss
should the server crash.

These options are measured in ticks, 1 second = 20 ticks.

``` yaml
options:
  # ...
  performance-tweaking: 
    quest-queue-executor-interval: 1
    quest-autosave-interval: 12000
```

## Tab completion

  
*`options.tab-completion`*

Choose whether or not commands can be tab completed. Quests will never
offer tab completions which players cannot run, regardless of this
setting. (In other words, players who are not admins will not see tab
completions for `/quests admin` if they do not have the admin
permission.)

``` yaml
options:
  # ...
  tab-completion:
    enabled: true
```

## Error checking

  
*`options.error-checking`*

Configure how Quests handles errors in your configuration. By default,
Quests will not allow quests to be loaded if they contain an
[error](configuration-problems#types-of-problem), since this
could lead to undefined behaviour. The option `override-errors` will
ignore this behaviour and forcibly allow the quest to be registered.

``` yaml
options:
  # ...
  error-checking:
    override-errors: false
```

## Placeholder cache time

  
*`options.placeholder-cache-time`*

Set how long Quests will retain parsed PlaceholderAPI strings in the
cache, in seconds. See [PlaceholderAPI § Caching
placeholders](../tools/placeholderapi#caching-placeholders) for more
information.

``` yaml
options:
  # ...
  placeholder-cache-time: 10
```

## Global task configuration override

  
*`options.global-task-configuration-override`*

Choose whether or not options set in the [global task
configuration](global-configurations#global-task-configuration)
will override per-quest specific options.

``` yaml
options:
  # ...
  global-task-configuration-override: false
```

## Global quest display configuration override

  
*`options.global-quest-display-configuration-override`*

Choose whether or not the [global quest display
configuration](global-configurations#global-quest-display-configuration)
will override per-quest specific options.

``` yaml
options:
  # ...
  global-quest-display-configuration-override: false
```

## Storage

  
*`options.storage`*

Configure how Quests will store playerdata. See [storage
providers](storage-providers) for more info.

``` yaml
options:
  # ...
  storage:
    provider: "yaml"
    synchronisation:
      delay-loading: 0
    database-settings:
      network:
        database: "minecraft"
        username: "root"
        password: ""
        address: "localhost:3306"
      connection-pool-settings:
        maximum-pool-size: 8
        minimum-idle: 8
        maximum-lifetime: 1800000
        connection-timeout: 5000
      table-prefix: "quests_"
```
