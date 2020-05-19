---
layout: default
title: Scene Reference Handlers
parent: Scene Reference Handlers
grand_parent: Components
has_children: true
nav_order: 1
---

# ISceneReferenceHandler


```
public interface Montebearo.Discourse.ISceneReferenceHandler : IEventComponent
```

---

## Methods

| Methods | Returns | Description |
| SyncWithEvent(DiscourseEvent discourseEvent) | void | Forces the handler to retrieve relevant information from an Event and update its information / lookup of objects appropriately. This is called via the ContextMenu on DiscourseEventBehaviour. |


---

# ISceneReferenceHandler\<T\>



```
public interface Montebearo.Discourse.ISceneReferenceHandler<out T> : ISceneReferenceHandler where T : Object
```

---

## Properties

| Property | Returns | Description |
|:--|:--|:--|
| Lookup | ISceneReferenceLookup<T> | The Lookup storing references of type T against their string Id. |
