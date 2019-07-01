---
layout: default
title: ICameraTransitionHandler
parent: Cameras
grand_parent: Components
nav_order: 1
---

# ICameraTransitionHandler



```
public interface Montebearo.Discourse.ICameraTransitionHandler
```

---

The ICameraTransitionHandler interface should be implemented by a behaviour responsible for transitioning between Cameras over the course of the dialogue.

## Properties

| Property | Returns | Description |
|:--------|:--------|:------------|
| ActiveCamera | UnityEngine.Camera | The Camera currently rendering. |

## Methods

| Method | Returns | Description |
|:-----|:-----|:----|
| SwitchCamera(ICameraSwitchInstruction cameraSwitcher) | void | Switch the ActiveCamera according to a given instruction. |
