---
layout: default
title: Actor (Component)
parent: Actors
nav_order: 1
---

# Actor (Component)

```
Montebearo.Discourse.Actor : MonteBehaviour
```
---

The Actor component automatically registers an ActorInfo with the ReferenceDatabase (during Awake) such that various behaviours can be retrieved from the scene at runtime. This component should live on the actual character in the scene, and only one per-actor should be instanced at any given time.

## Public Properties

| Property | Returns | Description |
|:---------|:--------|:------------|
| Info | ActorInfo | Returns the ActorInfo with the Id of the ActorReference set in the inspector via References. Not available before Awake(). |
| Animator | IActorAnimator | Returns the first instance of an IActorAnimator behaviour found on this GameObject. |
| AudioHandler | IAudioHandler | Returns the first instance of an IAudioHandler behaviour found on this GameObject. |
