---
layout: default
title: Event Advancers
parent: Components
has_children: true
nav_order: 1
---

# Event Advancers

Event Advancers are components that should instruct the EventBehaviour to "advance" the graph; e.g. complete / skip dialogue text, or await a particular input.

---

# IEventAdvancer


```
public interface Montebearo.Discourse.IEventAdvancer : IEventComponent
```

---

## EventHandlers

| EventHandler | Description |
|:--|:---|
| Advance | Subscribe to get notifications when this IEventAdvancer has received an input or otherwise determined the EventBehaviour should advance the graph's state. |
