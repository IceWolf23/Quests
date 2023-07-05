Play for a certain amount of time after starting the quest.

## Options

| Key          | Description                            | Type    | Required | Default | Notes                |
|--------------|----------------------------------------|---------|----------|---------|----------------------|
| `minutes`    | The number of minutes to play.         | Integer | Yes      | \-      | \-                   |
| `ignore-afk` | Whether AFK players should be ignored. | Boolean | Yes      | \-      | Requires Essentials. |

## Examples

Play for 20 minutes:

``` yaml
playtime:
  type: "playtime"
  minutes: 10                           # amount of minutes played
  ignore-afk: false                     # (OPTIONAL) ignore players marked as AFK by essentials
```
