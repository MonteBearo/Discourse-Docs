---
layout: default
title: AudioInstruction
parent: Audio
grand_parent: Components
nav_order: 1
---

# AudioInstruction



```
public enum Montebearo.Discourse.IAudioInstruction
```

---

An enumerable list of the various audio instructions.


| Value | Description |
|:--|:---|
| None | No action. |
| Play | Play an IAudioClip with control over Pause/Resume/Stop. |
| PlayOneShot | Play an IAudioClip immediately with less control, in a similar manner to the Unity Audio PlayOneShot() method. |
| Resume | Resume the current IAudioClip. |
| Pause | Pause the current IAudioClip. |
| Stop | Stop the current IAudioClip. |
