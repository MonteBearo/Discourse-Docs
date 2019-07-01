---
layout: default
title: ICameraSwitchInfo
parent: Cameras
grand_parent: Components
nav_order: 1
---

# ICameraSwitchInfo



```
public interface Montebearo.Discourse.ICameraSwitchInfo
```

---

An interface that should be implemented by an object describing information necessary to switch Cameras at runtime.

## Properties

| Property | Returns | Description |
|:--|:--|:--|
| ShouldSwitch | bool | Should the instruction switch the ActiveCamera? (Some actions may make adaptive choices about whether to transition shots or not). |
| TargetCameraId | string | The unique Id of the Camera to transition to (gained through a reference, e.g. the list of Cameras on the Entry action). |
