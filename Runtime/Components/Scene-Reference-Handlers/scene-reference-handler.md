---
layout: default
title: SceneReferenceHandler
parent: Scene Reference Handlers
grand_parent: Components
has_children: true
nav_order: 1
---

# SceneReferenceHandler

```
Montebearo.Discourse.SceneReferenceHandler<TLookup, TComponent> : MonteBehaviour, ISceneReferenceHandler<TComponent>
```

---

A concrete implementation of the [ISceneReferenceHandler](iscene-reference-handler.md) interfaces. This behaviour allows you to retrieve scene references of Unity Objects via a unique string Id at runtime. These components should be attached to the [EventBehaviour](../event-behaviour.md). 

When the 'UpdateReferenceHandlers' method is called via the EventBehaviour's context menu, it retrieves all ISceneReferenceHandler components on the object and syncs them with the reference lists of the Entry node of the current Event. Lists of these Id references should be stored in an ISceneReferenceInfoList.



---
