---
title: Quest progress in scoreboard
parent: Guides
---

# Quest progress in scoreboard

This guide will show you how to show quest progress in a scoreboard. The
plugin
[<https://www.spigotmc.org/resources/animatedscoreboard.20848/>](AnimatedScoreboard "wikilink")
will provide this scoreboard, however this will work for any plugin
accepting PlaceholderAPI.

**This utilises three features from Quests:**

- tracking quests
- PlaceholderAPI integration
- local quest placeholders

The final result will look like this:

<img src="https://i.imgur.com/NkcZTB2.png"> <img src="https://i.imgur.com/EIWAwb2.png">

## Adding local quest placeholders

Local quest placeholders are used here to provide the progress of the
quest and to provide a breif description of the quest. We will use a
simple blockbreak quest as our base here, where we must break 30 blocks
to complete the quest.

    /Quests/quests/example1.yml

``` yaml
...

placeholders:
  description: "&7Break &f30 blocks &7of any type."
  progress: " &8- &f{mining:progress}&7/30 broken"

...
```

These placeholders will be called using PlaceholderAPI using the
AnimatedScoreboard plugin. For example, using the placeholder
`%quests_q:example1_p:description%` with PlaceholderAPI will return
`&7Break &f30 blocks &7of any type.`. These are known as [local quest
placeholders](../tools/placeholderapi.md#Quest_details "wikilink").

Our `description` placeholder provides a description of the quest. The
\`progress\` placeholder will show the players progression with the
quest.

**You can create any placeholders here, and decide the names for
yourself.** These are designed for you to be able to access information
about a quest with PlaceholderAPI. Avoid using underscores and spaces,
this may cause issues when referencing them using placeholders.

To see the full quest (with comments), click
[here](https://github.com/LMBishop/Quests/blob/master/src/main/resources/resources/bukkit/quests/example1.yml "wikilink").

## Configuring AnimatedScoreboard

{: .note }
This guide assumes you have a basic understanding of the plugin
[<https://www.spigotmc.org/resources/animatedscoreboard.20848/>](AnimatedScoreboard "wikilink").

For our config with AnimatedScoreboard, we will create two seperate
scoreboards: one with tracked quest information and one informing the
user that they are not tracking a quest.

    /AnimatedScoreboard/scoreboards/questtrack.yml

``` yaml
display:
    title:
      text: 
       - "&6&lAmazing Server"
    line-1:
      text:
      - "&7"
      score: 5 
    line-2:
      text:
      - "&e&lTracked Quest:"
      score: 4
    line-3:
      text:
      - "&e%quests_tracked%"
      score: 3
    line-4:
      text:
      - "&7%quests_tracked_p:description%"
      score: 2
    line-5:
      text:
      - "&7%quests_tracked_p:progress%"
      score: 1
    line-6:
      text:
      - "&7"
      score: 0      
```

The placeholder `%quests_tracked<...>%` will access the players tracked
quest. In order to track a quest you must middle-click in-game on the
quest within the GUI. By default, when you start a quest it is
automatically tracked.

Simply put, we are accessing the placeholders called `description` and
`progress` which we made earlier in the player's tracked quest.

Now, we are going to create a default scoreboard for when there is no
tracked quest.

    /AnimatedScoreboard/scoreboards/defaultscoreboard.yml

``` yaml
display:
    title:
      text: 
       - "&6&lAmazing Server"
    line-1:
      text:
      - "&7"
      score: 3 
    line-2:
      text:
      - "&e&lTracked Quest:"
      score: 2
    line-3:
      text:
      - "&7You are not tracking a quest."
      score: 1
    line-4:
      text:
      - "&7"
      score: 0      
```

This is a simple static scoreboard. Finally, we must add a trigger to
switch between the two scoreboards.

Triggers must first be enabled within AnimatedScoreboard:

    /AnimatedScoreboard/config.yml

``` yaml
...
enable-triggers: true
...
```

Then, the server must be restarted. There should be a new folder called
`triggers`.

Now, we must create two files `ontrack.yml` and `ontrackend.yml`. This
will switch between the two scoreboard whenever the player tracks /
stops tracking a quest.

    /AnimatedScoreboard/triggers/ontrack.yml

``` yaml
event: com.leonardobishop.quests.bukkit.api.event.PlayerStartTrackQuestEvent
target-player: getPlayer
trigger-scoreboard: questtrack
```

This will switch to the \`questtrack\` scoreboard when a quest is
tracked.

    /AnimatedScoreboard/triggers/ontrackend.yml

``` yaml
event: com.leonardobishop.quests.bukkit.api.event.PlayerStopTrackQuestEvent
target-player: getPlayer
trigger-scoreboard: defaultscoreboard
```

This will switch to the \`defaultscoreboard\` scoreboard when a quest is
no longer tracked.

That's it! Restart the server and you should be able to see the progress
update in the scoreboard. Please note, you will have to include local
quest placeholders for every quest.

## Further reading

- [Creating a quest](Creating_a_quest "wikilink")
