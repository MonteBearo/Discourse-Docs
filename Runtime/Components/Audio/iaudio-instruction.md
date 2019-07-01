---
layout: default
title: IAudioInstruction
parent: Audio
grand_parent: Components
nav_order: 1
---

# IAudioInstruction



```
public interface Montebearo.Discourse.IAudioInstruction
```

---

The IAudioInstruction interface is a wrapper for various objects necessary to modify the current state of Audio.

## Properties

| Property | Returns | Description |
|:---|:----|:---|
| AudioInstruction | AudioInstruction | The Instruction to run. |
| ClipProvider | IAudioClipProvider | The object that should provide an IAudioClip should the instruction require it. |
| AudioModifier | IAudioModifier | The modifier object used to change the settings of the AudioInstruction. |
