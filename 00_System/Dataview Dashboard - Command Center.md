---
type: dashboard
tags:
  - roadmap/dashboard
---

# Dataview Dashboard - Command Center

## Active Main Quest Nodes

```dataview
TABLE domain, tier, status, prerequisite, unlock_condition
FROM "MainQuest"
WHERE type = "quest" AND status != "archived"
SORT domain ASC, order ASC
```

## Active Side Quests

```dataview
TABLE support_role, tier, status, main_quest_link
FROM "SideQuests"
WHERE type = "side_quest" AND status = "active"
SORT priority ASC
```

> If this table shows more than 3 rows, freeze the least useful one.

## Locked Regions

```dataview
TABLE unlock_condition, visible_hint
FROM "Hidden"
WHERE type = "hidden_quest"
SORT order ASC
```

## Recent Daily Logs

```dataview
TABLE main_focus, side_focus, evidence, next_unlock
FROM "DailyLogs"
WHERE type = "daily_log"
SORT file.name DESC
LIMIT 14
```

## Research Ideas

```dataview
TABLE status, related_field, next_action
FROM "ResearchIdeas"
WHERE type = "research_idea"
SORT file.mtime DESC
```
