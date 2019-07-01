---
layout: default
title: Scene Reference Handlers
parent: Components
has_children: true
nav_order: 1
---


# SceneReferenceHandler



```
Montebearo.Discourse.SceneReferenceHandler<TLookup, TComponent> : MonteBehaviour, ISceneReferenceHandler<TComponent>
```

---

A concrete implementation of the ISceneReferenceHandler interfaces. This behaviour allows you to retrieve scene references of a Unity-serializable type via a unique string Id at runtime. These components should sit next to the EventBehaviour such that when the 'UpdateReferenceHandlers' method is called via its ContextMenu, the Event can pass itself to all implemnentations of ISceneReferenceHandler so they can sync with the Event's data appropriately. Lists of these Id references should be stored in an ISceneReferenceInfoList.

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
