---
layout: default
title: IOptionButton
parent: Display
grand_parent: Components
nav_order: 1
---

# IOptionButton

```
public interface Montebearo.Discourse.IOptionButton : IEventComponent
```

---

## EventHandlers

| EventHandler | Arguments | Description |
|:--|:--|:--|
| Selected | Option | Subscribe for notifications when this OptionButton has been selected by the player. Passes the Option being displayed as the argument. |

## Methods

| Method | Returns | Description |
|:--|:--|:--|
| InvokeSelected() | void | Force the button to invoke its "Selected" EventHandler. This is useful if you need custom input to mark an IOptionButton as selected (e.g. with controller support).  |
| DisplayOption(Option option, bool immediateTransition) | void | Display a given option to the screen. The argument 'immediateTransition' indicates whether the button should transition its visibility with the 'Immediate' flag set. |
| Hide(bool immediate) | void | Hide the button from the screen. The bool 'immediate' indicates whether the button should transition its visibility with the 'Immediate' flag set. |
