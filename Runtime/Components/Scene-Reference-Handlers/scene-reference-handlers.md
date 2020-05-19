---
layout: default
title: Scene Reference Handlers
parent: Components
has_children: true
nav_order: 1
---

# Scene Reference Handlers

Usually in Unity, assets in the project cannot reference objects in the scene. This is problematic when you need to author a graph requiring references to scene objects ahead of time; GameObjects, Cameras, custom components etc. 

SceneReferenceHandlers are Discourse's solution to this problem. SceneReferenceHandlers map each of these object references to an ID, which is then used as a handle throughout the graph at edit-time, and whose reference value can by retrieved at runtime via the EventBehaviour.


