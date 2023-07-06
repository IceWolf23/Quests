---
title: bentobox_level
parent: Task types
nav_order: 28
---

# bentobox_level (task type)

Since v2.12
{: .label .label-green }

Plugin 'BentoBox' required
{: .label }

Reach a certain BentoBox level.

## Options

| Key     | Description         | Type    | Required | Default | Notes |
|---------|---------------------|---------|----------|---------|-------|
| `level` | The level to reach. | Integer | Yes      | \-      | \-    |

## Examples

Reach island level 10:

``` yaml
bentobox:
  type: "bentobox_level"
  level: 10                             # island level needed
```
