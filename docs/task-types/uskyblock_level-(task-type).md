---
title: uskyblock_level
parent: Task types
nav_order: 41
---

# uskyblock_level (task type)

Since v1.7.1
{: .label .label-green }

Plugin 'uSkyBlock' required
{: .label }

Reach a certain uSkyBlock level.

## Options

| Key     | Description         | Type    | Required | Default | Notes |
|---------|---------------------|---------|----------|---------|-------|
| `level` | The level to reach. | Integer | Yes      | \-      | \-    |

## Examples

Reach island level 10:

``` yaml
askyblock:
  type: "uskyblock_level"
  level: 10                             # island level needed
```
