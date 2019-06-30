---
layout: default
title: Audio Handlers
parent: Audio
grand_parent: Components
nav_order: 1
---

# AudioHandler

AudioHandlers are used for playing Audio on various objects, including Actors and the EventBehaviour.

Actor's require their own AudioHandler for playing voiced dialogue lines. Audio played by the built-in AudioAction node will use the EventBehaviour's AudioHandler.

Any dialogue that is referenced as Narrator dialogue (i.e the ActorReference is set to 'Narrator') will use a prefab specified on the PreferencesDatabase.  
