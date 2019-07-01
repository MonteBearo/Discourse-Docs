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


---

# IAudioHandler


```
public interface Montebearo.Discourse.IAudioHandler : IEventComponent
```

---

## Properties

| Property | Returns | Description |
|:--|:---|:---|
| IsPlaying | bool | Returns true for as long as this handler is playing Audio. |


## Methods

| Method | Returns | Description |
|:--|:---|:---|
| RunInstruction(IAudioInstruction instruction) | void | Run a given audio instruction using its contained parameters. |
| Play(IAudioClipProvider clipProvider) | void | Play an IAudioClip. (Generic such that you can extend your own implementation). |
| PlayOneShot(IAudioClipProvider clipProvider) | void | Play an IAudioClip in a "OneShot" mode; i.e. run it immediately in the same way as the Unity PlayOneShot() method would. |
| Resume() | void | Resume playing the current clip. |
| Pause() | void | Pause the clip currently playing. |
| Stop() | void | Stop the current clip. |
