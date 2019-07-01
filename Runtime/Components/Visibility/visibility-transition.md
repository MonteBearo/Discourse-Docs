---
layout: default
title: VisibilityTransition
parent: Visibility
grand_parent: Components
nav_order: 1
---

# VisibilityTransition


```
[Flags]
public enum Montebearo.Discourse.VisibilityTransition
```

---

The VisbiilityTransition enum is used by an IVisibilityTransitionHandler to describe a type of transition. Transitions can occur over time or immediately (see: 'Instant').

## Flags

| Flag | Description |
|:-----|:------------|
| ToVisible | Transition to a state where the element is visible. |
| ToHidden | Transition to a state where the element is hidden.
| Instant | Indicates whether the transition should occur immediately (i.e. in a single frame). |
||||
| ToVisibleInstant | Combines the ToVisible and Instant flags.  |
| ToHiddenInstant | Combines the ToHidden and Instant flags. |
